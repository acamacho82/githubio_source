---
title: "getOriginPullMappingInformation"
description: "This method returns a list of origin pull configuration data."
layout: "method"
tags:
    - "method"
    - "sldn"
    - "Network"
classes:
    - "SoftLayer_Network_ContentDelivery_Account"
aliases:
    - "/reference/services/softlayer_network_contentdelivery_account/getOriginPullMappingInformation"
---
# [SoftLayer_Network_ContentDelivery_Account](/reference/services/SoftLayer_Network_ContentDelivery_Account)::getOriginPullMappingInformation

Gets Origin Pull domain information


## Overview 
This method returns a list of origin pull configuration data. 

-----

### Parameters 
|Name | Type | Description |
| --- | --- | --- |


### Required Headers
* authenticate
* SoftLayer_Network_ContentDelivery_AccountInitParameters


### Return Values
* <a href='/reference/datatypes/SoftLayer_Container_Network_ContentDelivery_OriginPull_Mapping'>SoftLayer_Container_Network_ContentDelivery_OriginPull_Mapping[] </a>


### Associated Methods

*  [SoftLayer_Network_ContentDelivery_Account::createOriginPullRule](/reference/services/SoftLayer_Network_ContentDelivery_Account/createOriginPullRule )



### Error Handling

* SoftLayer_Exception_Public 

> Throws an exception if a user does not have CDN_ACCOUNT_MANAGE privilege. 

* SoftLayer_Exception_Public 

> Throws an exception if an Origin Pull rule is not set up. 



