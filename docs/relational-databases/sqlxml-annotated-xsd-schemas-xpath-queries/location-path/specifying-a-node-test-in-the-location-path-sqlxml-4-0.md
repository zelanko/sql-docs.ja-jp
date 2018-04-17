---
title: ノード テストの場所のパス (SQLXML 4.0) に指定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 52a2be7c03a3e5265a36f40952398279ab4ec589
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>ロケーション パスでのノード テストの指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (**子**、**親**、**属性**、または**self**) 主ノード型を持ちます。 **属性**軸、主ノード型は**\<属性 >**です。 **親**、**子**、および**self**軸の場合、主ノード型は**\<要素 >**です。  
  
> [!NOTE]  
>  ワイルドカード (*) のノード テスト (たとえば `child::*`) は、サポートされていません。  
  
## <a name="node-test-example-1"></a>ノード テスト: 例 1  
 ロケーション パス`child::Customer`選択**\<顧客 >**コンテキスト ノードの子要素です。  
  
 この例では、`child` は軸で、`Customer` はノード テストです。 主ノード型、**子**軸は**\<要素 >**です。 そのため、ノード テストの場合は TRUE、 **\<顧客 >**ノードが、 **\<要素 >**ノード。 コンテキスト ノードを持たない場合**\<顧客 >** 、子ノードの空のセットが返されます。  
  
## <a name="node-test-example-2"></a>ノード テスト : 例 2  
 ロケーション パス`attribute::CustomerID`選択、 **CustomerID**コンテキスト ノードの属性です。  
  
 例では、`attribute`軸と`CustomerID`ノード テストです。 主ノード型、**属性**軸は**\<属性 >**です。 そのため、ノード テストの場合は TRUE **CustomerID**は、 **\<属性 >**ノード。 コンテキスト ノードを持たない場合**CustomerID**空のノードのセットが返されます。  
  
> [!NOTE]  
>  XPath ロケーション ステップを参照する場合のこの実装では、 **\<要素 >**または**\<属性 >**エラーが生成されたスキーマで宣言されていない型です。 これは、空のノード セットを返す MSXML の XPath の実装とは異なります。  
  
## <a name="abbreviated-syntax-for-the-axes"></a>軸の省略構文  
 ロケーション パスでは、次の省略構文がサポートされています。  
  
-   `attribute::` は `@` で省略できます。  
  
     ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。  
  
-   ロケーション ステップから `child::` を省略できます。  
  
     したがって、**子**は、既定の軸です。 ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。  
  
-   `self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。  
  
  
