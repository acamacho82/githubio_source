---
title: "getAllowedReplicationSubnets"
description: "Retrieve the SoftLayer_Network_Subnet objects which are allowed access to this storage volume's Replicant."
layout: "method"
tags:
    - "method"
    - "sldn"
    - "Network"
classes:
    - "SoftLayer_Network_Storage"
---
# SoftLayer_Network_Storage::getAllowedReplicationSubnets
## Overview 
Retrieve the SoftLayer_Network_Subnet objects which are allowed access to this storage volume's Replicant.

### Parameters 
|Name | Type | Description |
| --- | --- | --- |


### Required Headers
* SoftLayer_Network_StorageInitParameters
* authenticate

### Optional Headers
* SoftLayer_Network_StorageObjectMask
* SoftLayer_Network_StorageObjectFilter
* resultLimit
* SoftLayer_ObjectMask

### Return Values
<a href='/reference/datatypes/SoftLayer_Network_Subnet'>SoftLayer_Network_Subnet[] </a>
