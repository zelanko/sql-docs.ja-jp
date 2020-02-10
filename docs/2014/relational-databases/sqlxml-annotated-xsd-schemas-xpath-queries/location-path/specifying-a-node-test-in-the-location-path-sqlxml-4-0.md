---
title: ロケーションパスでのノードテストの指定 (SQLXML 4.0) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d0a3dd41259bcbf2567d34a86527865de011faf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66012671"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>ロケーション パスでのノード テストの指定 (SQLXML 4.0)
  ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (`child`、`parent`、`attribute`、または `self`) には主ノード型があります。 `attribute`軸の場合、主ノード型は** \<属性>** です。 `parent`、 `child`、および`self`軸の場合、主ノード型は** \<要素>** です。  
  
> [!NOTE]  
>  ワイルドカード (*) のノード テスト (たとえば `child::*`) は、サポートされていません。  
  
## <a name="node-test-example-1"></a>ノードテスト: 例1  
 ロケーションパス`child::Customer`は、コンテキストノードの** \<Customer>** 要素の子を選択します。  
  
 この例では、`child` は軸で、`Customer` はノード テストです。 `child`軸の主ノード型は** \<要素>** です。 したがって、 ** \<Customer>** ノードが** \<要素>** ノードの場合、ノードテストは TRUE になります。 コンテキストノードに** \<顧客>** 子がない場合は、空のノードセットが返されます。  
  
## <a name="node-test-example-2"></a>ノード テスト : 例 2  
 ロケーションパス`attribute::CustomerID`によって、コンテキストノードの**CustomerID**属性が選択されます。  
  
 この例では`attribute` 、は軸で`CustomerID` 、はノードテストです。 `attribute`軸の主ノード型は** \<属性>** です。 このため、 **CustomerID**が** \<属性>** ノードの場合、ノードテストは TRUE になります。 コンテキストノードに**CustomerID**がない場合は、空のノードセットが返されます。  
  
> [!NOTE]  
>  この XPath の実装では、ロケーションステップが、スキーマで宣言されていない** \<要素>** または** \<属性>** 型を参照している場合、エラーが生成されます。 これは、空のノード セットを返す MSXML の XPath の実装とは異なります。  
  
## <a name="abbreviated-syntax-for-the-axes"></a>軸の省略構文  
 ロケーション パスでは、次の省略構文がサポートされています。  
  
-   
  `attribute::` は `@` で省略できます。  
  
     ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。  
  
-   ロケーション ステップから `child::` を省略できます。  
  
     つまり、`child` は既定の軸です。 ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。  
  
-   
  `self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。  
  
  
