---
title: ELEMENT ディレクティブとエンティティのエンコードの指定 | Microsoft Docs
description: クエリ結果がエンティティとしてエンコードされるように、SQL クエリで ELEMENT ディレクティブを指定する方法について学習します。
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 176cbbd92b55ada81a845018826cbf0b899b3475
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85632654"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>例:ELEMENT ディレクティブとエンティティのエンコードの指定
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
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
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML での EXPLICIT モードの使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
