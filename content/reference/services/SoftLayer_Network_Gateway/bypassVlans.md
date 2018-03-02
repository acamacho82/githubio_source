---
title: "bypassVlans"
description: "Start the asynchronous process to bypass the provided VLANs. The VLANs must already be attached. Any VLANs that are alre... "
layout: "method"
tags:
    - "method"
    - "sldn"
    - "Network"
classes:
    - "SoftLayer_Network_Gateway"
---
# SoftLayer_Network_Gateway::bypassVlans
## Overview 
Start the asynchronous process to bypass the provided VLANs. The VLANs must already be attached. Any VLANs that are already bypassed will be ignored. The status field can be checked for progress. 

### Parameters 
|Name | Type | Description |
| --- | --- | --- |
|vlans| <a href='/reference/datatypes/SoftLayer_Network_Gateway_Vlan'>SoftLayer_Network_Gateway_Vlan[] </a>| |


### Required Headers
* authenticate
* SoftLayer_Network_GatewayInitParameters

### Optional Headers

### Return Values
void
