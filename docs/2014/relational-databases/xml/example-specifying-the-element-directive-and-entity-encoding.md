---
title: '例 : ELEMENT ディレクティブとエンティティのエンコードを指定する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: cadbc9e06530706f0b1e1406af7b38b72246303f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067824"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>例 : ELEMENT ディレクティブとエンティティのエンコードを指定する
  この例では、 **ELEMENT** ディレクティブと **XML** ディレクティブの違いを説明します。 **ELEMENT** ディレクティブを指定した場合はデータがエンティティとしてエンコードされますが、 **XML** ディレクティブを指定した場合はその処理が行われません。 \<Summary>要素には、クエリで XML が割り当てられ `<Summary>This is summary description</Summary>` ます。  
  
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
 [FOR XML での EXPLICIT モードの使用](use-explicit-mode-with-for-xml.md)  
  
  
