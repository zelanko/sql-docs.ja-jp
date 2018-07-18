---
title: 入れ子になった FOR XML クエリを使用した XML の構造化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1c970d2472b304e3dbc2591019f7d70a9405cfd4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37234792"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a>入れ子になった FOR XML クエリを使用した XML の構造化
  次の例では、`Production.Product` テーブルにクエリを実行し、特定の製品の `ListPrice` 値と `StandardCost` 値を取得します。 ここでは、例示を目的として、両方の価格を <`Price`> 要素に返します。各 <`Price`> 要素には、`PriceType` 属性があります。  
  
## <a name="example"></a>例  
 次に、想定する XML の構造を示します。  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="http://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="http://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 次に、入れ子になった FOR XML クエリを示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 上のクエリに関して、次の点に注意してください。  
  
-   外側の SELECT ステートメントで <`Product`> 要素が構築されます。この要素には **ProductID** 属性と 2 つの <`Price`> 子要素があります。  
  
-   2 つの内側の SELECT ステートメントで <`Price`> 要素が 2 つ構築されます。各要素には **PriceType** 属性と製品価格を返す XML があります。  
  
-   外側の SELECT ステートメントの XMLSCHEMA ディレクティブで、結果の XML の構造を記述するインライン XSD スキーマが生成されます。  
  
 サンプルとして効果の高いクエリにするには、次のクエリに示すように、FOR XML クエリを記述し、その結果に対して XQuery を記述して、XML の構造を変更します。  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 前の例では、`query()`のメソッド、`xml`データが内側の FOR XML クエリによって返される XML に対してクエリを入力し、予想される結果を構築します。  
  
 結果を次に示します。  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a>参照  
 [入れ子になった FOR XML クエリの使用](use-nested-for-xml-queries.md)  
  
  
