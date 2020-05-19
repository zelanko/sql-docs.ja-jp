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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e4ff55980c7ca4cae45d568f03fef32ba1ea5155
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703099"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>ロケーション パスでのノード テストの指定 (SQLXML 4.0)
  ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (`child`、`parent`、`attribute`、または `self`) には主ノード型があります。 軸の場合 `attribute` 、主ノード型は** \< 属性>** です。 `parent`、 `child` 、および軸の場合 `self` 、主ノード型は** \< 要素>** です。  
  
> [!NOTE]  
>  ワイルドカード (*) のノード テスト (たとえば `child::*`) は、サポートされていません。  
  
## <a name="node-test-example-1"></a>ノードテスト: 例1  
 ロケーションパスは、 `child::Customer` コンテキストノードの** \< Customer>** 要素の子を選択します。  
  
 この例では、`child` は軸で、`Customer` はノード テストです。 軸の主ノード型 `child` は** \< 要素>** です。 したがって、 ** \< Customer>** ノードが** \< 要素>** ノードの場合、ノードテストは TRUE になります。 コンテキストノードに** \< 顧客>** 子がない場合は、空のノードセットが返されます。  
  
## <a name="node-test-example-2"></a>ノード テスト : 例 2  
 ロケーションパスによって、 `attribute::CustomerID` コンテキストノードの**CustomerID**属性が選択されます。  
  
 この例で `attribute` は、は軸で、 `CustomerID` はノードテストです。 軸の主ノード型 `attribute` は** \< 属性>** です。 このため、 **CustomerID**が** \< 属性>** ノードの場合、ノードテストは TRUE になります。 コンテキストノードに**CustomerID**がない場合は、空のノードセットが返されます。  
  
> [!NOTE]  
>  この XPath の実装では、ロケーションステップが、スキーマで宣言されていない** \< 要素>** または** \< 属性>** 型を参照している場合、エラーが生成されます。 これは、空のノード セットを返す MSXML の XPath の実装とは異なります。  
  
## <a name="abbreviated-syntax-for-the-axes"></a>軸の省略構文  
 ロケーション パスでは、次の省略構文がサポートされています。  
  
-   `attribute::` は `@` で省略できます。  
  
     ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。  
  
-   ロケーション ステップから `child::` を省略できます。  
  
     つまり、`child` は既定の軸です。 ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。  
  
-   `self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。  
  
  
