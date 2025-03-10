---
title: "Text.TrimEnd([Text]) Method"
description: "Removes all trailing occurrences of a set of characters specified in an array from the current Text object."
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
# Text.TrimEnd([Text]) Method
> **Version**: _Available or changed with runtime version 1.0._

Removes all trailing occurrences of a set of characters specified in an array from the current Text object.


## Syntax
```AL
Result :=   Text.TrimEnd([Chars: Text])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*Text*  
&emsp;Type: [Text](text-data-type.md)  
An instance of the [Text](text-data-type.md) data type.  

*[Optional] Chars*  
&emsp;Type: [Text](text-data-type.md)  
A string containing the characters to remove.  


## Return Value
*Result*  
&emsp;Type: [Text](text-data-type.md)  
A copy of this string without all trailing occurrences of the characters specified in the *Chars* parameter.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Text Data Type](text-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)