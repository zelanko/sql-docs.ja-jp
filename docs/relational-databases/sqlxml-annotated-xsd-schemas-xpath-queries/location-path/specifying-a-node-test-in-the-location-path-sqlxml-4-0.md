---
title: ノード テストの場所のパス (SQLXML 4.0) の指定 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8d0913a6066ddc0faec657a5e4857e206c227d5e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073305"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>ロケーション パスでのノード テストの指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  ノード テストによって、ロケーション ステップで選択されるノードの型が決まります。 すべての軸 (**子**、**親**、**属性**、または**セルフ**) 主ノード型があります。 **属性**軸の主ノード型は **\<属性 >** します。 **親**、**子**、および**セルフ**軸の場合、主ノード型は **\<要素 >** します。  
  
> [!NOTE]  
>  ワイルドカード (*) のノード テスト (たとえば `child::*`) は、サポートされていません。  
  
## <a name="node-test-example-1"></a>ノード テスト:例 1  
 ロケーション パス`child::Customer`選択 **\<顧客 >** コンテキスト ノードの子要素。  
  
 この例では、`child` は軸で、`Customer` はノード テストです。 主ノード型、**子**軸は **\<要素 >** します。 そのため、ノード テストの場合は TRUE、 **\<顧客 >** ノードが、 **\<要素 >** ノード。 コンテキスト ノードにない場合 **\<顧客 >** 、子ノードの空のセットが返されます。  
  
## <a name="node-test-example-2"></a>ノード テスト:例 2  
 ロケーション パス`attribute::CustomerID`選択、 **CustomerID**コンテキスト ノードの属性です。  
  
 例では、`attribute`は、軸と`CustomerID`はノード テストです。 主ノード型、**属性**軸は **\<属性 >** します。 そのため、ノード テストの場合は TRUE **CustomerID**は、 **\<属性 >** ノード。 コンテキスト ノードにない場合**CustomerID**空のノードのセットが返されます。  
  
> [!NOTE]  
>  XPath のロケーション ステップを参照する場合のこの実装では、 **\<要素 >** または **\<属性 >** エラーが生成されたスキーマで宣言されていない型です。 これは、空のノード セットを返す MSXML の XPath の実装とは異なります。  
  
## <a name="abbreviated-syntax-for-the-axes"></a>軸の省略構文  
 ロケーション パスでは、次の省略構文がサポートされています。  
  
-   `attribute::` は `@` で省略できます。  
  
     ロケーション パス `Customer[@CustomerID="ALFKI"]` は、`child::Customer[attribute::CustomerID="ALFKI"]` と同じです。  
  
-   ロケーション ステップから `child::` を省略できます。  
  
     したがって、**子**は既定の軸。 ロケーション パス `Customer/Order` は、`child::Customer/child::Order` と同じです。  
  
-   `self::node()` は 1 つのピリオド (.) で省略できます。また、`parent::node()` は 2 つのピリオド (..) で省略できます。  
  
  
