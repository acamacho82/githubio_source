---
title: "Take the Bite Out of Editing Firewall Rules – A Python Example"
description: "<p>Time is the only true bartering resource. We trade dollars for goods or services but the hard earned currency for the"
date: "2012-05-09"
author: "phil"
tags:
    - "blog"
---

<p>Time is the only true bartering resource. We trade dollars for goods or services but the hard earned currency for the transaction is one's time for another's. Due to the nonrenewable nature of this resource it is oft difficult for spare hours to be put into learning or researching that topic you always had a passing interest in or that everyone is gushing over. I try and keep an eye out during my daily experience for situations which may provide the excuse I need to allot time to one of the items on my "when-time-allows" list. On my list for some time: <a href="http://python.org/">Python</a>. This will not be a post about the merits and strengths of Python, but rather a look into a use case which provided me an opportunity to make use of it.</p>
<p>One of our customers needed to create a large number of firewall rules. While this can be accomplished through the <a href="https://manage.softlayer.com/">SoftLayer Portal</a>, the process quickly becomes time consuming when facing 100’s of rules. In this case time was indeed of the essence as a server missing firewall rules is a server exposed to the elements. The blanket in this case is woven of SoftLayer’s python client, argparse and ipaddr.</p>
<p>We will be looking at a command line script which can also be imported for use in your own implementations. A full concatenated version of the script can be found below.</p>
<p>Our script will update the rules for a firewall protecting an entire VLAN and takes short CIDR notatated IP addresses, port, protocol and action as parameters.</p>
<div class="geshifilter">
<pre class="python geshifilter-python" style="font-family:monospace;"><span style="color: #ff7700;font-weight:bold;">import</span> SoftLayer.<span style="color: black;">API</span>
<span style="color: #ff7700;font-weight:bold;">import</span> ipaddr
&nbsp;
&nbsp;
<span style="color: #808080; font-style: italic;"># Split a CIDR notated IP address into two strings: IP address, and netmask</span>
<span style="color: #ff7700;font-weight:bold;">def</span> splitIpCidrNotation<span style="color: black;">&#40;</span>arg<span style="color: black;">&#41;</span>:
    ipv4 <span style="color: #66cc66;">=</span> ipaddr.<span style="color: black;">IPv4Network</span><span style="color: black;">&#40;</span>arg<span style="color: black;">&#41;</span>
    <span style="color: #ff7700;font-weight:bold;">return</span> <span style="color: #008000;">str</span><span style="color: black;">&#40;</span>ipv4.<span style="color: black;">ip</span><span style="color: black;">&#41;</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">str</span><span style="color: black;">&#40;</span>ipv4.<span style="color: black;">netmask</span><span style="color: black;">&#41;</span>
&nbsp;
&nbsp;
<span style="color: #808080; font-style: italic;"># Create all API clients</span>
<span style="color: #ff7700;font-weight:bold;">def</span> getClients<span style="color: black;">&#40;</span><span style="color: #dc143c;">user</span><span style="color: #66cc66;">,</span> key<span style="color: black;">&#41;</span>:
    accountClient <span style="color: #66cc66;">=</span> SoftLayer.<span style="color: black;">API</span>.<span style="color: black;">Client</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'SoftLayer_Account'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">None</span><span style="color: #66cc66;">,</span> <span style="color: #dc143c;">user</span><span style="color: #66cc66;">,</span> key<span style="color: black;">&#41;</span>
    vlanClient <span style="color: #66cc66;">=</span> SoftLayer.<span style="color: black;">API</span>.<span style="color: black;">Client</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'SoftLayer_Network_Vlan'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">None</span><span style="color: #66cc66;">,</span> <span style="color: #dc143c;">user</span><span style="color: #66cc66;">,</span> key<span style="color: black;">&#41;</span>
    firewallUpdateRequestClient <span style="color: #66cc66;">=</span> SoftLayer.<span style="color: black;">API</span>.<span style="color: black;">Client</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'SoftLayer_Network_Firewall_Update_Request'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">None</span><span style="color: #66cc66;">,</span> <span style="color: #dc143c;">user</span><span style="color: #66cc66;">,</span> key<span style="color: black;">&#41;</span>
    <span style="color: #ff7700;font-weight:bold;">return</span> accountClient<span style="color: #66cc66;">,</span> vlanClient<span style="color: #66cc66;">,</span> firewallUpdateRequestClient</pre></div>
<p>Contrary to server specific firewalls, VLAN routed firewalls point of interaction is an Access Control List. SoftLayer_Network_Vlans have the firewallInterfaces property which contains all of the firewall ACLs on that VLAN and can be relationally expanded to the rules owned by those ACLs. Each VLAN will have two types of firewallInterface: 'inside' and 'outisde'. firewallContextAccessControlLists are organized by a direction of 'in' or 'out'. Currently the SoftLayer Platform supports the 'outside' firewallInterfaces and the 'in' ACLs.</p>
<div class="geshifilter">
<pre class="python geshifilter-python" style="font-family:monospace;"><span style="color: #808080; font-style: italic;"># This method, when given an IP address, will return the ID of the ACL which</span>
<span style="color: #808080; font-style: italic;"># provides protection for the given address as well as the full set of existing</span>
<span style="color: #808080; font-style: italic;"># firewall rules on the VLAN.</span>
<span style="color: #ff7700;font-weight:bold;">def</span> findAccessControlListByIp<span style="color: black;">&#40;</span>client<span style="color: #66cc66;">,</span> ip<span style="color: black;">&#41;</span>:
    mask <span style="color: #66cc66;">=</span> <span style="color: black;">&#123;</span>
        <span style="color: #483d8b;">'firewallInterfaces'</span>: <span style="color: black;">&#123;</span>
            <span style="color: #483d8b;">'firewallContextAccessControlLists'</span>: <span style="color: black;">&#123;</span>
                <span style="color: #483d8b;">'rules'</span>: <span style="color: black;">&#123;</span><span style="color: black;">&#125;</span>
            <span style="color: black;">&#125;</span>
        <span style="color: black;">&#125;</span>
    <span style="color: black;">&#125;</span>
&nbsp;
    client.<span style="color: black;">set_object_mask</span><span style="color: black;">&#40;</span>mask<span style="color: black;">&#41;</span>
    networkVlan <span style="color: #66cc66;">=</span> client.<span style="color: black;">getVlanForIpAddress</span><span style="color: black;">&#40;</span>ip<span style="color: black;">&#41;</span>
    <span style="color: #ff7700;font-weight:bold;">for</span> firewall <span style="color: #ff7700;font-weight:bold;">in</span> networkVlan<span style="color: black;">&#91;</span><span style="color: #483d8b;">'firewallInterfaces'</span><span style="color: black;">&#93;</span>:
        <span style="color: #ff7700;font-weight:bold;">if</span> firewall<span style="color: black;">&#91;</span><span style="color: #483d8b;">'name'</span><span style="color: black;">&#93;</span> <span style="color: #66cc66;">=</span> <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">'inside'</span>:
            <span style="color: #ff7700;font-weight:bold;">continue</span>
        <span style="color: #ff7700;font-weight:bold;">for</span> controlList <span style="color: #ff7700;font-weight:bold;">in</span> firewall<span style="color: black;">&#91;</span><span style="color: #483d8b;">'firewallContextAccessControlLists'</span><span style="color: black;">&#93;</span>:
            <span style="color: #ff7700;font-weight:bold;">if</span> controlList<span style="color: black;">&#91;</span><span style="color: #483d8b;">'direction'</span><span style="color: black;">&#93;</span> <span style="color: #66cc66;">=</span> <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">'out'</span>:
                <span style="color: #ff7700;font-weight:bold;">continue</span>
            firewallContextAccessControlListId <span style="color: #66cc66;">=</span> controlList<span style="color: black;">&#91;</span><span style="color: #483d8b;">'id'</span><span style="color: black;">&#93;</span>
            rules <span style="color: #66cc66;">=</span> controlList<span style="color: black;">&#91;</span><span style="color: #483d8b;">'rules'</span><span style="color: black;">&#93;</span>
&nbsp;
    <span style="color: #ff7700;font-weight:bold;">return</span> firewallContextAccessControlListId<span style="color: #66cc66;">,</span> rules</pre></div>
<p>Updating firewall rules is accomplished by passing a <a href="/reference/datatypes/SoftLayer_Network_Firewall_Update_Request/">SoftLayer_Network_Firewall_Update_Request</a> template object to <a href="/reference/services/SoftLayer_Network_Firewall_Update_Request/createObject">SoftLayer_Network_Firewall_Update_Request::createObject</a>. Upon creation the request will be added to the update queue and is typically completed in about 60 seconds. It is of note that this template object will overwrite any existing configuration. This creates the need for this template object to not only contain additional rules, but a complete set of all rules which should be set on the ACL. Modification of existing rules can be accomplished by manipulating the array of rules recieved by findAccessControlListByIp().</p>
<div class="geshifilter">
<pre class="python geshifilter-python" style="font-family:monospace;"><span style="color: #808080; font-style: italic;"># Build a SoftLayer_Network_Firewall_Update_Request template object. This method</span>
<span style="color: #808080; font-style: italic;"># will take CIDR notated destination and source addresses and append the required</span>
<span style="color: #808080; font-style: italic;"># individual rules to the existing ruleset.</span>
<span style="color: #ff7700;font-weight:bold;">def</span> createUpdateRequstTemplateObject<span style="color: black;">&#40;</span>client<span style="color: #66cc66;">,</span> sourceCidr<span style="color: #66cc66;">,</span> destCidr<span style="color: #66cc66;">,</span> action<span style="color: #66cc66;">,</span> protocol<span style="color: #66cc66;">,</span> port<span style="color: black;">&#41;</span>:
    destIp<span style="color: #66cc66;">,</span> destMask <span style="color: #66cc66;">=</span> splitIpCidrNotation<span style="color: black;">&#40;</span>destCidr<span style="color: black;">&#41;</span>
    destIps <span style="color: #66cc66;">=</span> ipaddr.<span style="color: black;">IPv4Network</span><span style="color: black;">&#40;</span>destCidr<span style="color: black;">&#41;</span>
    firewallContextAccessControlListId<span style="color: #66cc66;">,</span> rules <span style="color: #66cc66;">=</span> findAccessControlListByIp<span style="color: black;">&#40;</span>client<span style="color: #66cc66;">,</span> destIp<span style="color: black;">&#41;</span>
&nbsp;
    <span style="color: #ff7700;font-weight:bold;">if</span> sourceCidr <span style="color: #66cc66;">!=</span> <span style="color: #483d8b;">'any'</span>:
        sourceIp<span style="color: #66cc66;">,</span> sourceMask <span style="color: #66cc66;">=</span> splitIpCidrNotation<span style="color: black;">&#40;</span>sourceCidr<span style="color: black;">&#41;</span>
    <span style="color: #ff7700;font-weight:bold;">else</span>:
        sourceIp <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">'any'</span>
&nbsp;
    i <span style="color: #66cc66;">=</span> <span style="color: #008000;">len</span><span style="color: black;">&#40;</span>rules<span style="color: black;">&#41;</span> + <span style="color: #ff4500;">1</span>
    <span style="color: #ff7700;font-weight:bold;">for</span> destIp <span style="color: #ff7700;font-weight:bold;">in</span> destIps.<span style="color: black;">iterhosts</span><span style="color: black;">&#40;</span><span style="color: black;">&#41;</span>:
        newRule <span style="color: #66cc66;">=</span> <span style="color: black;">&#123;</span>
            <span style="color: #483d8b;">'action'</span>: action<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'destinationIpAddress'</span>: <span style="color: #008000;">str</span><span style="color: black;">&#40;</span>destIp<span style="color: black;">&#41;</span><span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'destinationIpSubnetMask'</span>: <span style="color: #483d8b;">'255.255.255.255'</span><span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'sourceIpAddress'</span>: sourceIp<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'sourceIpSubnetMask'</span>: sourceMask<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'protocol'</span>: protocol<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'destinationPortRangeStart'</span>: port<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'destinationPortRangeEnd'</span>: port<span style="color: #66cc66;">,</span>
            <span style="color: #483d8b;">'orderValue'</span>: i<span style="color: #66cc66;">,</span>
        <span style="color: black;">&#125;</span>
        i <span style="color: #66cc66;">=</span> i + <span style="color: #ff4500;">1</span>
        rules.<span style="color: black;">append</span><span style="color: black;">&#40;</span>newRule<span style="color: black;">&#41;</span>
&nbsp;
    templateObject <span style="color: #66cc66;">=</span> <span style="color: black;">&#123;</span>
        <span style="color: #483d8b;">'firewallContextAccessControlListId'</span>: firewallContextAccessControlListId<span style="color: #66cc66;">,</span>
        <span style="color: #483d8b;">'rules'</span>: rules
    <span style="color: black;">&#125;</span>
&nbsp;
    <span style="color: #ff7700;font-weight:bold;">return</span> templateObject
&nbsp;
&nbsp;
<span style="color: #808080; font-style: italic;"># Take in all necessary information for rule creation and create the Update Request</span>
<span style="color: #808080; font-style: italic;"># with the assitance of the above methods.</span>
<span style="color: #ff7700;font-weight:bold;">def</span> updateFirewall<span style="color: black;">&#40;</span>vlanClient<span style="color: #66cc66;">,</span> sourceCidr<span style="color: #66cc66;">,</span> destCidr<span style="color: #66cc66;">,</span> port<span style="color: #66cc66;">,</span> protocol<span style="color: #66cc66;">,</span> action<span style="color: #66cc66;">,</span> firewallUpdateRequestClient<span style="color: black;">&#41;</span>:
    <span style="color: #ff7700;font-weight:bold;">return</span> firewallUpdateRequestClient.<span style="color: black;">createObject</span><span style="color: black;">&#40;</span>createUpdateRequstTemplateObject<span style="color: black;">&#40;</span>vlanClient<span style="color: #66cc66;">,</span> sourceCidr<span style="color: #66cc66;">,</span> destCidr<span style="color: #66cc66;">,</span> action<span style="color: #66cc66;">,</span> protocol<span style="color: #66cc66;">,</span> port<span style="color: black;">&#41;</span><span style="color: black;">&#41;</span>
&nbsp;
&nbsp;
<span style="color: #808080; font-style: italic;"># Defines proces of events when being used as a command line tool. Wrapping this portion</span>
<span style="color: #808080; font-style: italic;"># of the script and calling as it is below allows the helper functions above to be</span>
<span style="color: #808080; font-style: italic;"># included in other projects without the need for rewriting.</span>
<span style="color: #ff7700;font-weight:bold;">def</span> main_cli<span style="color: black;">&#40;</span><span style="color: black;">&#41;</span>:
    <span style="color: #ff7700;font-weight:bold;">from</span> argparse <span style="color: #ff7700;font-weight:bold;">import</span> ArgumentParser
    <span style="color: #ff7700;font-weight:bold;">from</span> <span style="color: #dc143c;">pprint</span> <span style="color: #ff7700;font-weight:bold;">import</span> <span style="color: #dc143c;">pprint</span>
&nbsp;
    <span style="color: #dc143c;">parser</span> <span style="color: #66cc66;">=</span> ArgumentParser<span style="color: black;">&#40;</span>description<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Update a VLAN Firewall'</span><span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">parser</span>.<span style="color: black;">add_argument</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'-s'</span><span style="color: #66cc66;">,</span> nargs<span style="color: #66cc66;">=</span><span style="color: #ff4500;">1</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">type</span><span style="color: #66cc66;">=</span><span style="color: #008000;">str</span><span style="color: #66cc66;">,</span> required<span style="color: #66cc66;">=</span><span style="color: #008000;">True</span><span style="color: #66cc66;">,</span> metavar<span style="color: #66cc66;">=</span><span style="color: #483d8b;">"Source Address"</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">help</span><span style="color: #66cc66;">=</span><span style="color: #483d8b;">"Source IP in short CIDR Notation"</span><span style="color: #66cc66;">,</span>
        dest<span style="color: #66cc66;">=</span><span style="color: #483d8b;">"sourceCidr"</span><span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">parser</span>.<span style="color: black;">add_argument</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'-d'</span><span style="color: #66cc66;">,</span> nargs<span style="color: #66cc66;">=</span><span style="color: #ff4500;">1</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">type</span><span style="color: #66cc66;">=</span><span style="color: #008000;">str</span><span style="color: #66cc66;">,</span> required<span style="color: #66cc66;">=</span><span style="color: #008000;">True</span><span style="color: #66cc66;">,</span> metavar<span style="color: #66cc66;">=</span><span style="color: #483d8b;">"Destination Address"</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">help</span><span style="color: #66cc66;">=</span><span style="color: #483d8b;">"Destination IP in short CIDR Notation"</span><span style="color: #66cc66;">,</span>
        dest<span style="color: #66cc66;">=</span><span style="color: #483d8b;">"destCidr"</span><span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">parser</span>.<span style="color: black;">add_argument</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'-r'</span><span style="color: #66cc66;">,</span> nargs<span style="color: #66cc66;">=</span><span style="color: #ff4500;">1</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">type</span><span style="color: #66cc66;">=</span><span style="color: #008000;">int</span><span style="color: #66cc66;">,</span> required<span style="color: #66cc66;">=</span><span style="color: #008000;">True</span><span style="color: #66cc66;">,</span> metavar<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Port'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">help</span><span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Destination Port'</span><span style="color: #66cc66;">,</span> dest<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'port'</span><span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">parser</span>.<span style="color: black;">add_argument</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'-p'</span><span style="color: #66cc66;">,</span> nargs<span style="color: #66cc66;">=</span><span style="color: #ff4500;">1</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">type</span><span style="color: #66cc66;">=</span><span style="color: #008000;">str</span><span style="color: #66cc66;">,</span> required<span style="color: #66cc66;">=</span><span style="color: #008000;">True</span><span style="color: #66cc66;">,</span> metavar<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Protocol'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">help</span><span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Protocol tcp/udp'</span><span style="color: #66cc66;">,</span>
        dest<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'protocol'</span><span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">parser</span>.<span style="color: black;">add_argument</span><span style="color: black;">&#40;</span><span style="color: #483d8b;">'-a'</span><span style="color: #66cc66;">,</span> nargs<span style="color: #66cc66;">=</span><span style="color: #ff4500;">1</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">type</span><span style="color: #66cc66;">=</span><span style="color: #008000;">str</span><span style="color: #66cc66;">,</span> required<span style="color: #66cc66;">=</span><span style="color: #008000;">True</span><span style="color: #66cc66;">,</span> metavar<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Action'</span><span style="color: #66cc66;">,</span> <span style="color: #008000;">help</span><span style="color: #66cc66;">=</span><span style="color: #483d8b;">'Action the rule will impliment: permit/deny'</span><span style="color: #66cc66;">,</span>
        dest<span style="color: #66cc66;">=</span><span style="color: #483d8b;">'action'</span><span style="color: black;">&#41;</span>
&nbsp;
    args <span style="color: #66cc66;">=</span> <span style="color: #dc143c;">parser</span>.<span style="color: black;">parse_args</span><span style="color: black;">&#40;</span><span style="color: black;">&#41;</span>
&nbsp;
    apiUsername <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">""</span>
    apiKey <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">""</span>
    accountClient<span style="color: #66cc66;">,</span> vlanClient<span style="color: #66cc66;">,</span> firewallUpdateRequestClient <span style="color: #66cc66;">=</span> getClients<span style="color: black;">&#40;</span>apiUsername<span style="color: #66cc66;">,</span> apiKey<span style="color: black;">&#41;</span>
    <span style="color: #dc143c;">pprint</span><span style="color: black;">&#40;</span>updateFirewall<span style="color: black;">&#40;</span>vlanClient<span style="color: #66cc66;">,</span> args.<span style="color: black;">sourceCidr</span><span style="color: black;">&#91;</span><span style="color: #ff4500;">0</span><span style="color: black;">&#93;</span><span style="color: #66cc66;">,</span> args.<span style="color: black;">destCidr</span><span style="color: black;">&#91;</span><span style="color: #ff4500;">0</span><span style="color: black;">&#93;</span><span style="color: #66cc66;">,</span> args.<span style="color: black;">port</span><span style="color: black;">&#91;</span><span style="color: #ff4500;">0</span><span style="color: black;">&#93;</span><span style="color: #66cc66;">,</span> args.<span style="color: black;">protocol</span><span style="color: black;">&#91;</span><span style="color: #ff4500;">0</span><span style="color: black;">&#93;</span><span style="color: #66cc66;">,</span> args.<span style="color: black;">action</span><span style="color: black;">&#91;</span><span style="color: #ff4500;">0</span><span style="color: black;">&#93;</span><span style="color: #66cc66;">,</span> firewallUpdateRequestClient<span style="color: black;">&#41;</span><span style="color: black;">&#41;</span>
&nbsp;
&nbsp;
<span style="color: #ff7700;font-weight:bold;">if</span> __name__ <span style="color: #66cc66;">=</span> <span style="color: #66cc66;">=</span> <span style="color: #483d8b;">"__main__"</span>:
    main_cli<span style="color: black;">&#40;</span><span style="color: black;">&#41;</span></pre></div>
<p>Since taking that first step into the Python world I have now found it quickly becoming my go to SLAPI tinkering language. So now I charge you, Adventurer. I charge you with making time for that one thing you keep meaning to do. If it happens to be writing a SLAPI script, be sure to send it my way!</p>
<p>Grab the full script: <a href="https://gist.github.com/2158553">here</a></p>
<p>-Phil</p>

