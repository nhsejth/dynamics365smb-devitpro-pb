---
title: "RecordRef.Copy(var Record [, Boolean]) Method"
description: "Copies a specified record's filters, views, automatically calculated FlowFields, marks, fields, and keys that are associated with the record from a table or creates a reference to a record."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.service: "dynamics365-business-central"
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# RecordRef.Copy(var Record [, Boolean]) Method
> **Version**: _Available or changed with runtime version 5.3._

Copies a specified record's filters, views, automatically calculated FlowFields, marks, fields, and keys that are associated with the record from a table or creates a reference to a record.


## Syntax
```AL
 RecordRef.Copy(var FromRecord: Record [, ShareTable: Boolean])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*FromRecord*  
&emsp;Type: [Record](../record/record-data-type.md)  
The record to copy.
        
*[Optional] ShareTable*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
Specifies whether the method copies filters, views, automatically calculated FlowFields, marks, fields, and keys of the record or creates a reference to a temporary record. If FromRecord and Record are both temporary and ShareTable is true, then the COPY method causes Record to reference the same table as FromRecord. If ShareTable is true, then both Record and FromRecord must be temporary; otherwise an error will occur. The default value is false. If you specify false, only filters, marks, and keys are copied.
        



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)