---
title: 定量化式 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- universal quantifiers
- effective Boolean value [XQuery]
- quantified expressions [XQuery]
- XQuery, quantified expressions
- every expression [XQuery]
- existential quantifiers [XQuery]
- some expression [XQuery]
- EBV
- expressions [XQuery], quantifiers
ms.assetid: a3a75a6c-8f67-4923-8406-1ada546c817f
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cdbff23d2158dec00b6b8d050d6a4a90341bd23
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946376"
---
# <a name="quantified-expressions-xquery"></a>量化式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  存在量化子と全称量化子により、2 つのシーケンスに適用されるブール演算子に異なるセマンティクスが指定されます。 次の表にこれを示します。  
  
 *存在量化子*  
 2つのシーケンスが指定されている場合、最初のシーケンス内のいずれかの項目が2番目のシーケンスで一致すると、使用される比較演算子に基づいて、戻り値は True になります。  
  
 *ユニバーサル量指定子*  
 2 つのシーケンスがあるときに、最初のシーケンスのすべてのアイテムが 2 番目のシーケンスと一致する場合、True が返されます。  
  
 XQuery では、次の形式の定量化式がサポートされています。  
  
```  
( some | every ) <variable> in <Expression> (,...) satisfies <Expression>  
```  
  
 クエリでこれらの式を使用して、1つまたは複数のシーケンスに対する式に明示的に存在する全称または universal を適用することができます。 で[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は、 `satisfies`句内の式は、ノードシーケンス、空のシーケンス、またはブール値のいずれかになる必要があります。 この式の結果の有効なブール値が、量化に使用されます。 一部を使用する存在する全称は、量指定子によってバインドされた値の少なくと**も**1 つが、対応する式の真の結果を持っている場合に true を返します。 を使用するユニバーサル全称**は、** 量指定子によってバインドされたすべての値に対して True を持つ必要があります。  
  
 たとえば、次のクエリでは、 \<すべての場所> 要素に対して、locationid 属性があるかどうかを確認します。  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        if (every $WC in //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID)  
        then  
             <Result>All work centers have workcenterLocation ID</Result>  
         else  
             <Result>Not all work centers have workcenterLocation ID</Result>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 LocationID は\<Location> 要素の必須属性であるため、予想される結果を受け取ります。  
  
```  
<Result>All work centers have Location ID</Result>   
```  
  
 [Query () メソッド](../t-sql/xml/query-method-xml-data-type.md)を使用する代わりに、次のクエリに示すように、 [value () メソッド](../t-sql/xml/value-method-xml-data-type.md)を使用して、結果をリレーショナル環境に返すことができます。 このクエリは、すべてのワークセンターの場所に LocationID 属性がある場合に True を返します。 それ以外の場合は False が返されます。  
  
```  
SELECT Instructions.value('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        every $WC in  //AWMI:root/AWMI:Location   
            satisfies $WC/@LocationID',   
  'nvarchar(10)') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 次のクエリでは、製品の写真の中に小さいサイズの写真があるかどうかを確認します。 製品カタログ XML には、さまざまな角度で撮影されたサイズの異なる製品の写真が格納されています。 各製品カタログ XML にサイズの小さい写真が少なくとも 1 枚含まれているようにすることができます。 これを行うには、次のクエリを実行します。  
  
```  
SELECT ProductModelID, CatalogDescription.value('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     some $F in /PD:ProductDescription/PD:Picture  
        satisfies $F/PD:Size="small"', 'nvarchar(20)') as SmallPicturesStored  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 結果の一部を次に示します。  
  
```  
ProductModelID SmallPicturesStored   
-------------- --------------------  
19             true        
```  
  
## <a name="implementation-limitations"></a>実装の制限事項  
 制限事項は次のとおりです。  
  
-   量化式の変数をバインドする操作の一部として、型のアサーションはサポートされません。  
  
## <a name="see-also"></a>参照  
 [XQuery 式](../xquery/xquery-expressions.md)  
  
  
