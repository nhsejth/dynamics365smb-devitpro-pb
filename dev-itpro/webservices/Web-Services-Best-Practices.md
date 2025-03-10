---
title: Web Services Best Practices
description: Get the list of recommendations for how to use web services in your Business Central solution.
author: edupont04
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.service: dynamics365-business-central
ms.author: edupont
---
# Web Services Best Practices

This article provides recommendations that you can implement to make your web services applications faster and easier to understand and maintain.  
  
|Recommendation|Example|  
|--------------------|-------------|  
| Performance of web services is both the responsibility of the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] server endpoint and the consumer (the client). | Visit the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] performance tuning guide to learn how to make web services fast and stable. Read more at [Writing efficient Web Services](../performance/performance-developer.md)   |
|Use the HTTPS protocol to send data between [!INCLUDE[prod_short](../developer/includes/prod_short.md)] and the web service consumer. The examples in this section use the HTTP protocol to illustrate the setup, but we recommend that your solution uses transport-level security.|In the application that consumes the [!INCLUDE[prod_short](../developer/includes/prod_short.md)] web service, require that URIs are accessed by using HTTPS. For example, a more secure URI for the OData web services on your local computer is `https://localhost:7048/BC130/OData/`.|  
|Use singular forms of names. This provides meaningful singular entity names in the generated proxy classes.|When publishing page 21, Customer Card, use **Customer** as the service name instead of **Customers** or **CustomerCard**.|  
|Avoid using spaces and other characters because they are transformed to underscores or other characters that may not be displayed as you want and could lead to ambiguity.|When publishing page 42, Sales Order, remove the space and use **SalesOrder** as the service name.|  
|Use Pascal casing when you combine words. Pascal casing capitalizes the first character of each word, including acronyms and initialisms that are more than two letters long.|Use **SalesOrder** or **ContactPerson** as the service name.|

## See Also
[Web Services Overview](web-services.md)  
[Writing fast Web Services](../performance/performance-developer.md)
