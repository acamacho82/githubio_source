---
title: "SoftLayer_Ticket_Attachment_Virtual_Guest"
description: "SoftLayer tickets have the ability to be associated with specific virtual guests in a customer's inventory. Attaching vi... "
layout: "datatype"
tags:
    - "datatype"
    - "sldn"
    - "Ticket"
classes:
    - "SoftLayer_Ticket_Attachment_Virtual_Guest"
---

# SoftLayer_Ticket_Attachment_Virtual_Guest
<div id='service-datatype'>
    <ul id='sldn-reference-tabs'>
        <li id='datatype'> <a href='/reference/datatypes/SoftLayer_Ticket_Attachment_Virtual_Guest' >Datatype</a></li>
    </ul>
</div>

## Description 
SoftLayer tickets have the ability to be associated with specific virtual guests in a customer's inventory. Attaching virtual guests to a ticket can greatly increase response time from SoftLayer for issues that are related to one or more specific servers on a customer's account. The SoftLayer_Ticket_Attachment_Virtual_Guest data type models the relationship between a virtual guest and a ticket. Only one attachment record may exist per virtual guest per ticket. 


### associatedMethods

*  [SoftLayer_Ticket::getAttachedVirtualGuests](/reference/services/SoftLayer_Ticket/getAttachedVirtualGuests )
*  [SoftLayer_Ticket::addAttachedVirtualGuest](/reference/services/SoftLayer_Ticket/addAttachedVirtualGuest )
*  [SoftLayer_Ticket::removeAttachedVirtualGuest](/reference/services/SoftLayer_Ticket/removeAttachedVirtualGuest )



### seeAlso

* [SoftLayer_Ticket](/reference/services/SoftLayer_Ticket )


* [SoftLayer_Ticket_Attachment_File](/reference/services/SoftLayer_Ticket_Attachment_File )


* [SoftLayer_Ticket_Attachment_Hardware](/reference/datatypes/SoftLayer_Ticket_Attachment_Hardware )




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
                <a href="#attachmentId" name=attachmentId>attachmentId</a>
            </span>
            <div class='views-field-body'>The internal identifier of an item that is attached to a ticket. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#createDate" name=createDate>createDate</a>
            </span>
            <div class='views-field-body'>The date that an item was attached to a ticket. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>dateTime</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#id" name=id>id</a>
            </span>
            <div class='views-field-body'>A ticket attachment's internal identifier. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#ticketId" name=ticketId>ticketId</a>
            </span>
            <div class='views-field-body'>The internal identifier of the ticket that an item is attached to. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#virtualGuestId" name=virtualGuestId>virtualGuestId</a>
            </span>
            <div class='views-field-body'>The internal identifier of the virtualized guest or CloudLayer Computing Instance that is attached to a ticket. </div>
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
                <a href="#resource" name=resource>resource</a>
            </span>
            <div class='views-field-body'>The virtualized guest or CloudLayer Computing Instance that is attached to a ticket. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Virtual_Guest'>SoftLayer_Virtual_Guest </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#ticket" name=ticket>ticket</a>
            </span>
            <div class='views-field-body'>The ticket that an item is attached to. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Ticket'>SoftLayer_Ticket </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#virtualGuest" name=virtualGuest>virtualGuest</a>
            </span>
            <div class='views-field-body'>The virtualized guest or CloudLayer Computing Instance that is attached to a ticket. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Virtual_Guest'>SoftLayer_Virtual_Guest </a></p>
            </div>
        </div>
                <h2>Count</h2>
            </div>
</div>


