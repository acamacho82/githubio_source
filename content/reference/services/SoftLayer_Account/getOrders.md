---
title: "getOrders"
description: "Retrieve an account's associated billing orders excluding upgrades."
layout: "method"
tags:
    - "method"
    - "sldn"
    - "Account"
classes:
    - "SoftLayer_Account"
---
# SoftLayer_Account::getOrders
## Overview 
Retrieve an account's associated billing orders excluding upgrades.

### Parameters 
|Name | Type | Description |
| --- | --- | --- |


### Required Headers
* authenticate

### Optional Headers
* SoftLayer_AccountObjectMask
* SoftLayer_AccountObjectFilter
* resultLimit
* SoftLayer_ObjectMask

### Return Values
<a href='/reference/datatypes/SoftLayer_Billing_Order'>SoftLayer_Billing_Order[] </a>
