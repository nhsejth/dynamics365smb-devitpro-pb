---
title: "XmlDocument.ReadFrom(String, XmlReadOptions, var XmlDocument) Method"
description: "Reads and parses the XML document from the given data source."
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
# XmlDocument.ReadFrom(String, XmlReadOptions, var XmlDocument) Method
> **Version**: _Available or changed with runtime version 1.0._

Reads and parses the XML document from the given data source.


## Syntax
```AL
[Ok := ]  XmlDocument.ReadFrom(Text: String, ReadOptions: XmlReadOptions, var Result: XmlDocument)
```
## Parameters
*Text*  
&emsp;Type: [String](../string/string-data-type.md)  
A string containing an XML document.
        
*ReadOptions*  
&emsp;Type: [XmlReadOptions](../xmlreadoptions/xmlreadoptions-data-type.md)  
Specifies options for customizing how the document is parsed.
        
*Result*  
&emsp;Type: [XmlDocument](xmldocument-data-type.md)  
The XmlDocument parsed from the given data source.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocument Data Type](xmldocument-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)