---
title: "System.Decrypt(String) Method"
description: "Takes a string as input and returns the decrypted value of the string."
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
# System.Decrypt(String) Method
> **Version**: _Available or changed with runtime version 1.0._

Takes a string as input and returns the decrypted value of the string.


## Syntax
```AL
PlainTextString :=   System.Decrypt(EncryptedString: String)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*EncryptedString*  
&emsp;Type: [String](../string/string-data-type.md)  
The input string that will be decrypted.  


## Return Value
*PlainTextString*  
&emsp;Type: [String](../string/string-data-type.md)  
The output string that is decrypted.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

If encryption is not enabled or the encryption key does not exist, the following error will be displayed: **An encryption key is required to complete the request**. If decryption failed because input data could not be decrypted, the following error will be displayed: **Unable to decrypt data. The data was encrypted using a different key**.  

## Example  

This code example checks whether the tenant is configured to allow encryption using the [EncryptionEnabled](../../methods-auto/system/system-encryptionenabled-method.md) method, and then it decrypts an encrypted text string.  

This example requires that you create the following text constants: EncryptedText and PlainText.  

```al
if not EncryptionEnabled then  
        Error('Encryption has not been enabled.');  
      PlainText := Decrypt(EncryptedText);  

```  

## See Also

[System Data Type](system-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)