---
title: ノード テストの場所のパス (SQLXML 4.0) の指定 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7450810f45d81dd1530699677a80a052840ed867
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806004"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>ロケーション パスでのノード テストの指定 (SQLXML 4.0)
  ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (`child`、`parent`、`attribute`、または `self`) には主ノード型があります。 `attribute`軸の主ノード型は**\<属性 >** します。 `parent`、 `child`、および`self`軸の場合、主ノード型は**\<要素 >** します。  
  
> [!NOTE]  
>  ワイルドカード (*) のノード テスト (たとえば `child::*`) は、サポートされていません。  
  
## <a name="node-test-example-1"></a>ノード テスト:例 1  
 ロケーション パス`child::Customer`選択**\<顧客 >** コンテキスト ノードの子要素。  
  
 この例では、`child` は軸で、`Customer` はノード テストです。 主ノード型、`child`軸は**\<要素 >** します。 そのため、ノード テストの場合は TRUE、 **\<顧客 >** ノードが、 **\<要素 >** ノード。 コンテキスト ノードにない場合**\<顧客 >** 、子ノードの空のセットが返されます。  
  
## <a name="node-test-example-2"></a>ノード テスト:例 2  
 ロケーション パス`attribute::CustomerID`選択、 **CustomerID**コンテキスト ノードの属性です。  
  
 例では、`attribute`は、軸と`CustomerID`はノード テストです。 主ノード型、`attribute`軸は**\<属性 >** します。 そのため、ノード テストの場合は TRUE **CustomerID**は、 **\<属性 >** ノード。 コンテキスト ノードにない場合**CustomerID**空のノードのセットが返されます。  
  
> [!NOTE]  
>  XPath のロケーション ステップを参照する場合のこの実装では、 **\<要素 >** または**\<属性 >** エラーが生成されたスキーマで宣言されていない型です。 これは、空のノード セットを返す MSXML の XPath の実装とは異なります。  
  
## <a name="abbreviated-syntax-for-the-axes"></a>軸の省略構文  
 ロケーション パスでは、次の省略構文がサポートされています。  
  
-   `attribute::` は `@` で省略できます。  
  
     ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。  
  
-   ロケーション ステップから `child::` を省略できます。  
  
     つまり、`child` は既定の軸です。 ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。  
  
-   `self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。  
  
  
