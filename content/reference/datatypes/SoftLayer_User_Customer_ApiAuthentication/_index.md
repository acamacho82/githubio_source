---
title: "SoftLayer_User_Customer_ApiAuthentication"
description: "The SoftLayer_User_Customer_ApiAuthentication type contains user's authentication key(s)."
layout: "datatype"
tags:
    - "datatype"
    - "sldn"
    - "User"
classes:
    - "SoftLayer_User_Customer_ApiAuthentication"
---

# SoftLayer_User_Customer_ApiAuthentication
<div id='service-datatype'>
    <ul id='sldn-reference-tabs'>
    <li id='service'> <a href='/reference/services/SoftLayer_User_Customer_ApiAuthentication' >Service</a></li>    <li id='datatype'> <a href='/reference/datatypes/SoftLayer_User_Customer_ApiAuthentication' >Datatype</a></li>
    </ul>
</div>

## Description 
The SoftLayer_User_Customer_ApiAuthentication type contains user's authentication key(s).


### associatedMethods

*  [SoftLayer_User_Customer::getApiAuthenticationKeys](/reference/services/SoftLayer_User_Customer/getApiAuthenticationKeys )
*  [SoftLayer_User_Customer_ApiAuthentication::getObject](/reference/services/SoftLayer_User_Customer_ApiAuthentication/getObject )



### seeAlso

* [SoftLayer_User_Customer](/reference/services/SoftLayer_User_Customer )




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
                <a href="#authenticationKey" name=authenticationKey>authenticationKey</a>
            </span>
            <div class='views-field-body'>The user's authentication key for API access. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#id" name=id>id</a>
            </span>
            <div class='views-field-body'>The user's API authentication identifying number. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#ipAddressRestriction" name=ipAddressRestriction>ipAddressRestriction</a>
            </span>
            <div class='views-field-body'>The IP addresses or IP ranges from which this user may access the SoftLayer API. Specify subnets in CIDR format and separate multiple addresses and subnets by commas. You may combine IPv4 and IPv6 addresses and subnets, for example: 192.168.0.0/16,fe80:021b::0/64. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#timestampKey" name=timestampKey>timestampKey</a>
            </span>
            <div class='views-field-body'>The user's authentication key modification date. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#userId" name=userId>userId</a>
            </span>
            <div class='views-field-body'>The user's identifying number. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
            </div>
        <div id="relationalProperties"  class="prop-content" >
        <h2>Relational</h2>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#user" name=user>user</a>
            </span>
            <div class='views-field-body'>The user who owns the api authentication key. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_User_Customer'>SoftLayer_User_Customer </a></p>
            </div>
        </div>
                <h2>Count</h2>
            </div>
</div>


