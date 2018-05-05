---
title: 選択述語の指定 (SQLXML 4.0) の場所のパスに |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7e32ce8235adfe6774b339219ced7ecb6a38f505
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>ロケーション パスでの選択述語の指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  述語は、SELECT ステートメントの WHERE 句と同様に、軸についてノード セットをフィルター選択するものです。 述語はかっこで囲みます。 フィルター選択されたノード セットの各ノードに対し、ノードをコンテキスト ノード、ノード セット内のノード数をコンテキストのサイズとして、述語式が評価されます。 述語式が TRUE と評価された場合、そのノードは結果のノード セットに含められます。  
  
 XPath では、位置に基づくフィルター選択を行うこともできます。 数値として評価される述語式を使用すると、その序数に対応するノードが選択されます。 たとえば、ロケーション パス `Customer[3]` では、3 番目の顧客が返されますが、 このような数値述語はサポートされていません。 サポートされているのは、ブール値の結果を返す述語式のみです。  
  
> [!NOTE]  
>  この XPath の XPath の実装の制限事項に関する情報と、および W3C の仕様の違いは、次を参照してください。 [XPath クエリの使用の概要&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md)です。  
  
## <a name="selection-predicate-example-1"></a>選択述語: 例 1  
 すべての現在のコンテキスト ノードから次の XPath 式 (ロケーション パス) を選択、 **\<顧客 >** 子要素が、 **CustomerID** ALFKI の値を持つ属性。  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 この XPath クエリでは、`child` と `attribute` は軸名で、 `Customer` ノード テストです (場合は TRUE`Customer`は、 **\<要素ノード >** ので、 **\<要素 >** の主ノード型は、`child`軸) です。 `attribute::CustomerID="ALFKI"` は述語です。 述語で`attribute`軸と`CustomerID`ノード テストです (場合は TRUE **CustomerID**ためコンテキスト ノードの属性は、 **\<属性 >** プリンシパルは、ノード型**属性**軸) です。  
  
 省略構文を使用した場合、XPath クエリは次のように指定できます。  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>選択述語: 例 2  
 すべての現在のコンテキスト ノードから次の XPath 式 (ロケーション パス) を選択、 **\<順序 >** 孫要素が、 **SalesOrderID**値 1 を持つ属性。  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 この XPath 式では、`child` と `attribute` は軸名で、 `Customer`、`Order`、および `SalesOrderID` はノード テストです。 `attribute::OrderID="1"` は述語です。  
  
 省略構文を使用した場合、XPath クエリは次のように指定できます。  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>選択述語: 例 3  
 すべての現在のコンテキスト ノードから次の XPath 式 (ロケーション パス) を選択、 **\<顧客 >** を 1 つまたは複数を含む子 **\<ContactName >** 子:  
  
```  
child::Customer[child::ContactName]  
```  
  
 この例では、  **\<ContactName >** の子要素、 **\<顧客 >** と呼ばれる XML ドキュメント内の要素*要素中心のマッピング*注釈付き XSD スキーマです。  
  
 この XPath 式では、`child` が軸名で、 `Customer` ノード テストです (場合は TRUE`Customer`は、 **\<要素 >** ノード、ため**\<要素 >** の主ノード型は、`child`軸) です。 `child::ContactName` は述語です。 述語で`child`軸と`ContactName`ノード テストです (場合は TRUE`ContactName`は、 **\<要素 >** ノード)。  
  
 この式はだけを返す、 **\<顧客 >** を含むコンテキスト ノードの要素の子 **\<ContactName >** 子要素です。  
  
 省略構文を使用した場合、XPath クエリは次のように指定できます。  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>選択述語: 例 4  
 次の XPath 式を選択**\<顧客 >** がない、コンテキスト ノードの要素の子 **\<ContactName >** 子要素。  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 この例では、  **\<ContactName >** の子要素、 **\<顧客 >** XML ドキュメントであり、ContactName フィールド内の要素は必須でない、データベースです。  
  
 この例では、`child` は軸で、 `Customer` ノード テストです (場合は TRUE`Customer`は、\<要素 > ノード)。 `not(child::ContactName)` は述語です。 述語で`child`軸と`ContactName`ノード テストです (場合は TRUE`ContactName`は、\<要素 > ノード)。  
  
 省略構文を使用した場合、XPath クエリは次のように指定できます。  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>選択述語: 例 5  
 すべての現在のコンテキスト ノードから次の XPath 式を選択、 **\<顧客 >** 子を持つ、 **CustomerID**属性。  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 この例では`child`軸と`Customer`ノード テストです (場合は TRUE`Customer`は、\<要素 > ノード)。 `attribute::CustomerID` は述語です。 述語で`attribute`軸と`CustomerID`述語である (TRUE の場合`CustomerID`は、 **\<属性 >** ノード)。  
  
 省略構文を使用した場合、XPath クエリは次のように指定できます。  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>選択述語 : 例 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 では、次の例に示すように、述語にクロス積を含む XPath クエリがサポートされています。  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 このクエリでは、`Order` の `OrderDate` が任意の `ShipDate` の `Order` と等しいすべての顧客が選択されます。  
  
## <a name="see-also"></a>参照  
 [注釈付き XSD スキーマの概要&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [クライアント側の XML 書式設定 (&) #40 です。SQLXML 4.0 & #41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
