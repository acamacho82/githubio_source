---
title: "McAfee_Epolicy_Orchestrator_Version36_Agent_Details"
description: "The McAfee_Epolicy_Orchestrator_Version36_Agent_Details data type represents a virus scan agent and contains details abo... "
layout: "datatype"
tags:
    - "datatype"
    - "sldn"
    - "Epolicy"
classes:
    - "McAfee_Epolicy_Orchestrator_Version36_Agent_Details"
---

# McAfee_Epolicy_Orchestrator_Version36_Agent_Details
<div id='service-datatype'>
    <ul id='sldn-reference-tabs'>
        <li id='datatype'> <a href='/reference/datatypes/McAfee_Epolicy_Orchestrator_Version36_Agent_Details' >Datatype</a></li>
    </ul>
</div>

## Description 
The McAfee_Epolicy_Orchestrator_Version36_Agent_Details data type represents a virus scan agent and contains details about its version.





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
                <a href="#agentVersion" name=agentVersion>agentVersion</a>
            </span>
            <div class='views-field-body'>Version number of the anti-virus scan agent. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#lastUpdate" name=lastUpdate>lastUpdate</a>
            </span>
            <div class='views-field-body'>The date of the last time the anti-virus agent checked in. </div>
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
                <a href="#currentPolicy" name=currentPolicy>currentPolicy</a>
            </span>
            <div class='views-field-body'>The current anti-virus policy of an agent. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>McAfee_Epolicy_Orchestrator_Version36_Agent_Parent_Details</p>
            </div>
        </div>
                <h2>Count</h2>
            </div>
</div>


