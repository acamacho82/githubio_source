---
title: "SoftLayer_Dns_Domain_ResourceRecord_MxType"
description: "SoftLayer_Dns_Domain_ResourceRecord_MxType is a SoftLayer_Dns_Domain_ResourceRecord object whose ''type'' property is se... "
layout: "datatype"
tags:
    - "datatype"
    - "sldn"
    - "Dns"
classes:
    - "SoftLayer_Dns_Domain_ResourceRecord_MxType"
---

# SoftLayer_Dns_Domain_ResourceRecord_MxType
<div id='service-datatype'>
    <ul id='sldn-reference-tabs'>
    <li id='service'> <a href='/reference/services/SoftLayer_Dns_Domain_ResourceRecord_MxType' >Service</a></li>    <li id='datatype'> <a href='/reference/datatypes/SoftLayer_Dns_Domain_ResourceRecord_MxType' >Datatype</a></li>
    </ul>
</div>

## Description 
SoftLayer_Dns_Domain_ResourceRecord_MxType is a SoftLayer_Dns_Domain_ResourceRecord object whose ''type'' property is set to "mx" and used to describe MX resource records. MX records control which hosts are responsible as mail exchangers for a domain. For instance, in the domain example.org, an MX record whose host is "@" and data is "mail" says that the host "mail.example.org" is responsible for handling mail for example.org. That means mail sent to users @example.org are delivered to mail.example.org. 

Domains can have more than one MX record if it uses more than one server to send mail through. Multiple MX records are denoted by their priority, defined by the mxPriority property. 

MX records must be defined for hosts with accompanying A or AAAA resource records. They may not point mail towards a host defined by a CNAME record. 

### External Links


* [MX Record at Wikipedia](http://en.wikipedia.org/wiki/MX_record)



### associatedMethods

*  [SoftLayer_Dns_Domain::createMxRecord](/reference/services/SoftLayer_Dns_Domain/createMxRecord )
*  [SoftLayer_Dns_Domain_ResourceRecord_MxType::createObject](/reference/services/SoftLayer_Dns_Domain_ResourceRecord_MxType/createObject )



### seeAlso

* [SoftLayer_Dns_Domain](/reference/services/SoftLayer_Dns_Domain )


* [SoftLayer_Dns_Domain_ResourceRecord](/reference/services/SoftLayer_Dns_Domain_ResourceRecord )




<!-- Service Filer BEGIN -->
<div class="view-filters">
        <div class="clearfix">
            <div class="search-input-box">
                <input placeholder="Method Filter" onkeyup="titleSearch(inputId='prop-input', divId='properties', elementClass='prop-row')" 
                    type="text" id="prop-input" value="" size="30" maxlength="128" class="form-text">
            </div>
        </div>
</div>
<!-- Service Filer END -->

<div id="properties" class="content">
    <div id="localProperties" class="prop-content" >
        <h2>Local</h2>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#data" name=data>data</a>
            </span>
            <div class='views-field-body'>The value of a domain's resource record. This can be an IP address or a hostname. Fully qualified host and domain name data must end with the "." character.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#domainId" name=domainId>domainId</a>
            </span>
            <div class='views-field-body'>An identifier belonging to the domain that a resource record is associated with. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#expire" name=expire>expire</a>
            </span>
            <div class='views-field-body'>The amount of time in seconds that a secondary name server (or servers) will hold a zone before it is no longer considered authoritative.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#host" name=host>host</a>
            </span>
            <div class='views-field-body'>The host defined by a resource record. A value of "@" denotes a wildcard. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#id" name=id>id</a>
            </span>
            <div class='views-field-body'>A domain resource record's internal identifier. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#minimum" name=minimum>minimum</a>
            </span>
            <div class='views-field-body'>The amount of time in seconds that a domain's resource records are valid. This is also known as a minimum TTL, and can be overridden by an individual resource record's TTL.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#mxPriority" name=mxPriority>mxPriority</a>
            </span>
            <div class='views-field-body'>Useful in cases where a domain has more than one mail exchanger, the priority property is the priority of the MTA that delivers mail for a domain. A lower number denotes a higher priority, and mail will attempt to deliver through that MTA before moving to lower priority mail servers. Priority is defaulted to 10 upon resource record creation.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#refresh" name=refresh>refresh</a>
            </span>
            <div class='views-field-body'>The amount of time in seconds that a secondary name server should wait to check for a new copy of a DNS zone from the domain's primary name server. If a zone file has changed then the secondary DNS server will update it's copy of the zone to match the primary DNS server's zone.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#responsiblePerson" name=responsiblePerson>responsiblePerson</a>
            </span>
            <div class='views-field-body'>The email address of the person responsible for a domain, with the "@" replaced with a ".". For instance, if root@example.org is responsible for example.org, then example.org's SOA responsibility is "root.example.org.".  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#retry" name=retry>retry</a>
            </span>
            <div class='views-field-body'>The amount of time in seconds that a domain's primary name server (or servers) should wait if an attempt to refresh by a secondary name server failed before attempting to refresh a domain's zone with that secondary name server again.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#ttl" name=ttl>ttl</a>
            </span>
            <div class='views-field-body'>The Time To Live value of a resource record, measured in seconds. TTL is used by a name server to determine how long to cache a resource record. An SOA record's TTL value defines the domain's overall TTL.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#type" name=type>type</a>
            </span>
            <div class='views-field-body'>The string "mx" which defines a resource record as an MX record. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
            </div>
        <div id="relationalProperties"  class="prop-content" >
        <h2>Relational</h2>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#domain" name=domain>domain</a>
            </span>
            <div class='views-field-body'>The domain that a resource record belongs to. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Dns_Domain'>SoftLayer_Dns_Domain </a></p>
            </div>
        </div>
                <h2>Count</h2>
            </div>
</div>


