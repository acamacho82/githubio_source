---
title: "SoftLayer_Software_Description"
description: "This class holds a description for a specific installation of a Software Component. 

SoftLayer_Software_Licenses tie a... "
layout: "datatype"
tags:
    - "datatype"
    - "sldn"
    - "Software"
classes:
    - "SoftLayer_Software_Description"
---

# SoftLayer_Software_Description
<div id='service-datatype'>
    <ul id='sldn-reference-tabs'>
    <li id='service'> <a href='/reference/services/SoftLayer_Software_Description' >Service</a></li>    <li id='datatype'> <a href='/reference/datatypes/SoftLayer_Software_Description' >Datatype</a></li>
    </ul>
</div>

## Description 
This class holds a description for a specific installation of a Software Component. 

SoftLayer_Software_Licenses tie a Software Component (A specific installation on a piece of hardware) to it's description. 

The "Manufacturer" and "Name" properties of a SoftLayer_Software_Description are used by the framework to factory specific objects, objects that may have special methods for that specific piece of software, or objects that contain application specific data, such as default ports.  For example, if you create a SoftLayer_Software_Component who's SoftLayer_Software_License points to the SoftLayer_Software_Description for "Swsoft" "Plesk", you'll actually get a SoftLayer_Software_Component_Swsoft_Plesk object. 



### seeAlso

* [SoftLayer_Software_Component](/reference/services/SoftLayer_Software_Component )


* [SoftLayer_Software_License](/reference/datatypes/SoftLayer_Software_License )




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
                <a href="#controlPanel" name=controlPanel>controlPanel</a>
            </span>
            <div class='views-field-body'>This is set to '1' if this Software Description describes a Control Panel. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#id" name=id>id</a>
            </span>
            <div class='views-field-body'>An ID number to identify this Software Description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#licenseTermUnit" name=licenseTermUnit>licenseTermUnit</a>
            </span>
            <div class='views-field-body'>The unit of measurement (day, month, or year) for license registration. Used in conjunction with licenseTermValue to determine overall license registration length of a new license.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#licenseTermValue" name=licenseTermValue>licenseTermValue</a>
            </span>
            <div class='views-field-body'>The number of units (licenseTermUnit) a new license is valid for at the time of registration. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#longDescription" name=longDescription>longDescription</a>
            </span>
            <div class='views-field-body'>The manufacturer, name and version of a piece of software. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#manufacturer" name=manufacturer>manufacturer</a>
            </span>
            <div class='views-field-body'>The name of the manufacturer for this specific piece of software.  This name is used by SoftLayer_Software_Component to tailor make (factory) specific types of Software Components that know details like default ports.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#name" name=name>name</a>
            </span>
            <div class='views-field-body'>The name of this specific piece of software.  This name is used by SoftLayer_Software_Component to tailor make (factory) specific types of Software Components that know details like default ports.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#operatingSystem" name=operatingSystem>operatingSystem</a>
            </span>
            <div class='views-field-body'>This is set to '1' if this Software Description describes an Operating System. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#referenceCode" name=referenceCode>referenceCode</a>
            </span>
            <div class='views-field-body'>A reference code is structured as three tokens separated by underscores. The first token represents the product, the second is the version of the product, and the third is whether the software is 32 or 64bit.  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#upgradeSoftwareDescriptionId" name=upgradeSoftwareDescriptionId>upgradeSoftwareDescriptionId</a>
            </span>
            <div class='views-field-body'>Contains the ID of the suggested upgrade from this Software_Description to a more powerful software installation. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#upgradeSwDescId" name=upgradeSwDescId>upgradeSwDescId</a>
            </span>
            <div class='views-field-body'>Contains the ID of the suggested upgrade from this Software_Description to a more powerful software installation. (Deprecated - Use upgradeSoftwareDescriptionId) </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#version" name=version>version</a>
            </span>
            <div class='views-field-body'>The version of this specific piece of software. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#virtualLicense" name=virtualLicense>virtualLicense</a>
            </span>
            <div class='views-field-body'>This is set to '1' if this Software Description can be licensed to a Virtual Machine (an IP address). </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#virtualizationPlatform" name=virtualizationPlatform>virtualizationPlatform</a>
            </span>
            <div class='views-field-body'>This is set to '1' if this Software Description a platform for hosting virtual servers. </div>
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
                <a href="#attributes" name=attributes>attributes</a>
            </span>
            <div class='views-field-body'> </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description_Attribute'>SoftLayer_Software_Description_Attribute[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#averageInstallationDuration" name=averageInstallationDuration>averageInstallationDuration</a>
            </span>
            <div class='views-field-body'>The average amount of time that a software description takes to install. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>integer</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#compatibleSoftwareDescriptions" name=compatibleSoftwareDescriptions>compatibleSoftwareDescriptions</a>
            </span>
            <div class='views-field-body'>A list of the software descriptions that are compatible with this software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description'>SoftLayer_Software_Description[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#features" name=features>features</a>
            </span>
            <div class='views-field-body'>The feature attributes of a software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description_Feature'>SoftLayer_Software_Description_Feature[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#latestVersion" name=latestVersion>latestVersion</a>
            </span>
            <div class='views-field-body'>The latest version of a software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description'>SoftLayer_Software_Description[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#productItems" name=productItems>productItems</a>
            </span>
            <div class='views-field-body'>The various product items to which this software description is linked. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Product_Item'>SoftLayer_Product_Item[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#provisionTransactionGroup" name=provisionTransactionGroup>provisionTransactionGroup</a>
            </span>
            <div class='views-field-body'>This details the provisioning transaction group for this software. This is only valid for Operating System software. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Provisioning_Version1_Transaction_Group'>SoftLayer_Provisioning_Version1_Transaction_Group </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#reloadTransactionGroup" name=reloadTransactionGroup>reloadTransactionGroup</a>
            </span>
            <div class='views-field-body'>The transaction group that a software description belongs to. A transaction group is a sequence of transactions that must be performed in a specific order for the installation of software. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Provisioning_Version1_Transaction_Group'>SoftLayer_Provisioning_Version1_Transaction_Group </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#requiredUser" name=requiredUser>requiredUser</a>
            </span>
            <div class='views-field-body'>The default user created for a given a software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>string</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#softwareLicenses" name=softwareLicenses>softwareLicenses</a>
            </span>
            <div class='views-field-body'>Software Licenses that govern this Software Description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_License'>SoftLayer_Software_License[] </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#upgradeSoftwareDescription" name=upgradeSoftwareDescription>upgradeSoftwareDescription</a>
            </span>
            <div class='views-field-body'>A suggestion for an upgrade path from this Software Description </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description'>SoftLayer_Software_Description </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#upgradeSwDesc" name=upgradeSwDesc>upgradeSwDesc</a>
            </span>
            <div class='views-field-body'>A suggestion for an upgrade path from this Software Description (Deprecated - Use upgradeSoftwareDescription) </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Software_Description'>SoftLayer_Software_Description </a></p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#validFilesystemTypes" name=validFilesystemTypes>validFilesystemTypes</a>
            </span>
            <div class='views-field-body'> </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p><a href='/reference/datatypes/SoftLayer_Configuration_Storage_Filesystem_Type'>SoftLayer_Configuration_Storage_Filesystem_Type[] </a></p>
            </div>
        </div>
                <h2>Count</h2>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#attributeCount" name=attributeCount>attributeCount</a>
            </span>
            <div class='views-field-body'>A count of  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#compatibleSoftwareDescriptionCount" name=compatibleSoftwareDescriptionCount>compatibleSoftwareDescriptionCount</a>
            </span>
            <div class='views-field-body'>A count of a list of the software descriptions that are compatible with this software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#featureCount" name=featureCount>featureCount</a>
            </span>
            <div class='views-field-body'>A count of the feature attributes of a software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#latestVersionCount" name=latestVersionCount>latestVersionCount</a>
            </span>
            <div class='views-field-body'>A count of the latest version of a software description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#productItemCount" name=productItemCount>productItemCount</a>
            </span>
            <div class='views-field-body'>A count of the various product items to which this software description is linked. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#softwareLicenseCount" name=softwareLicenseCount>softwareLicenseCount</a>
            </span>
            <div class='views-field-body'>A count of software Licenses that govern this Software Description. </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
                <div class='prop-row views-row'>
            <span class='views-field-title'>
                <a href="#validFilesystemTypeCount" name=validFilesystemTypeCount>validFilesystemTypeCount</a>
            </span>
            <div class='views-field-body'>A count of  </div>
            <span class="type-label">Type:</span> 
            <div class='type-content'>
                <p>unsignedLong</p>
            </div>
        </div>
            </div>
</div>


