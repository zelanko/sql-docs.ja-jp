---
title: "例 : ELEMENT ディレクティブとエンティティのエンコードを指定する | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d2ddb67aee711a217bd9f75b62ef14067e4aac55
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>例 : ELEMENT ディレクティブとエンティティのエンコードを指定する
  この例では、 **ELEMENT** ディレクティブと **XML** ディレクティブの違いを説明します。 **ELEMENT** ディレクティブを指定した場合はデータがエンティティとしてエンコードされますが、 **XML** ディレクティブを指定した場合はその処理が行われません。 このクエリでは、\<Summary> 要素に、`<Summary>This is summary description</Summary>` のように XML が割り当てられています。  
  
 次のクエリについて考えてみます。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 結果は次のとおりです。 概要説明がエンティティとしてエンコードされています。  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 ここで、 **のように、列名に** ELEMENT `Summary!2!SummaryDescription!XML`ディレクティブではなく **XML** ディレクティブを指定すると、概要情報のエンコード処理が行われません。  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 次のクエリでは、静的な XML 値を割り当てる代わりに、 **xml** 型の **query()** メソッドを使用して、 **xml** 型の CatalogDescription 列から製品モデルの概要情報を取得します。 この場合、結果は **xml** 型であることがわかっているので、エンコード処理が適用されません。  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での EXPLICIT モードの使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
