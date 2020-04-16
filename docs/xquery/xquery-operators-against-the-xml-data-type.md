---
title: xml データ型に対する XQuery 演算子 |マイクロソフトドキュメント
description: xml データ型に対して使用できる XQuery 演算子について説明します。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
author: rothja
ms.author: jroth
ms.openlocfilehash: d5692aa5b46d79c68165fa6f1320034fdb7e03b3
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388302"
---
# <a name="xquery-operators-against-the-xml-data-type"></a>xml データ型に対する XQuery の演算子
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery は、次の演算子をサポートします。  
  
-   数値演算子 (+、-、*、div、mod)  
  
-   値比較のための演算子 (eq,ne, lt, gt, le, ge)  
  
-   一般比較の演算子 ( =, \<!= \<, >, =, >= )  
  
 これらの演算子の詳細については[、「XQuery&#41;&#40;比較式](../xquery/comparison-expressions-xquery.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="a-using-general-operators"></a>A. 一般演算子の使用  
 次のクエリでは、シーケンスおよびシーケンスの比較に適用される一般的な演算子の用途について説明します。 クエリは、**連絡先**テーブルの**追加のContactInfo**列から、各顧客の電話番号のシーケンスを取得します。 このシーケンスは、2 つの電話番号のシーケンス (「111-111-1111」、"222-2222") と比較されます。  
  
 クエリは比較演算子**=** を使用します。 **=** 演算子の右側のシーケンスの各ノードは、左側のシーケンスの各ノードと比較されます。 ノードが一致する場合、ノード比較は**TRUE**になります。 次に int に変換され、1 と比較され、クエリは顧客 ID を返します。  
  
```sql
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 前のクエリの動作を確認する別の方法があります:**追加の連絡先の**列から取得した各電話番号の値は、2 つの電話番号のセットと比較されます。 値がセット内にある場合、その顧客が結果に返されます。  
  
### <a name="b-using-a-numeric-operator"></a>B. 数値演算子の使用  
 このクエリの + 演算子は、単一の項目に適用されるため、値演算子です。 たとえば、値 1 は、クエリによって返されるロット サイズに追加されます。  
  
```sql
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>C. 値演算子の使用  
 次のクエリは、画像サイズ`Picture`が 「小さい」製品モデルの<>要素を取得します。  
  
```sql
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 **eq**演算子のオペランドはどちらもアトミック値であるため、値演算子はクエリで使用されます。 一般比較演算子 ( )**=** を使用して同じクエリを記述できます。  
  
## <a name="see-also"></a>参照  
 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [XML データ &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 言語リファレンス &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
