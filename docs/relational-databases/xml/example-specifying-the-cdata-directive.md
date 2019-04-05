---
title: '例: CDATA ディレクティブの指定 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f2cba1b43d782ef9d9a75d159e245f0f5d4077a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511099"
---
# <a name="example-specifying-the-cdata-directive"></a>例:CDATA ディレクティブの指定
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **CDATA**ディレクティブが指定されている場合、含まれているデータはエンティティとしてエンコードされず、CDATA セクションに配置されます。 **CDATA** 属性は、無名でなければなりません。  
  
 次のクエリでは、製品モデルの概要説明を CDATA セクションに配置しています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 結果を次に示します。  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での EXPLICIT モードの使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
