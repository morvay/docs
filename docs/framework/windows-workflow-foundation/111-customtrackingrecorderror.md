---
title: "111 - CustomTrackingRecordError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d469fb12-e094-4d6c-9b4d-abd7ce0d17da
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
---
# 111 - CustomTrackingRecordError
## Properties  
  
|||  
|-|-|  
|Id|111|  
|Keywords|UserEvents, EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking|  
|Level|Error|  
|Channel|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## Description  
 This event is emitted by the ETW tracking participant when an activity within a workflow instance emits CustomTrackingRecord with level error.  
  
## Message  
 TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11  
  
## Details  
  
|Data Item Name|Data Item Type|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|The instance id for the workflow|  
|RecordNumber|xs:long|The sequence number of the emitted record|  
|EventTime|xs:dateTime|The time in UTC when the event was emitted|  
|Name|xs:string|The name of the CustomTrackingRecord|  
|ActivityName|xs:string|The name of the activity that emitted the CustomTrackingRecord|  
|ActivityId|xs:string|The id of the activity that emitted the CustomTrackingRecord|  
|ActivityInstanceId|xs:string|The instance id of the activity that emitted the CustomTrackingRecord|  
|ActivityTypeName|xs:string|The name of the activity that emitted the CustomTrackingRecord|  
|Data|xs:string|The data that was tracked with this event.  The values are stored in an xml element in the format \<items>\< item  name = "dataName" type="System.String">dataValue\</item>\</items>.  If no data was tracked then the string contains \<items/>. The ETW event size is limited by the ETW buffer size or the max payload for an ETW event. If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the data value with \<items>...\</items>.  The following types are stored as their value as returned by ToString(); string,char,bool,int,short,long,uint,ushort,ulong,System.Single,float,double,System.Guid,System.DateTimeOffset,System.DateTime.  All other types are serialized using System.Runtime.Serialization.NetDataContractSerializer.|  
|Annotations|xs:string|The annotations that were added to this event.  The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.  If no annotations are specified then the string contains \<items/>. The ETW event size is limited by the ETW buffer size or the max payload for an ETW event. If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.|  
|ProfileName|xs:string|The name or the tracking profile that resulted in this event being emitted|  
|HostReference|xs:string|For web hosted services, this field uniquely identifies the service in the web hierarchy.  Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:string|The string returned by AppDomain.CurrentDomain.FriendlyName.|