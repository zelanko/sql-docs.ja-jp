---
title: データの操作 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], data manipulation
- data manipulation [MDX]
- Multidimensional Expressions [Analysis Services], data manipulation
ms.assetid: 4865192e-f46b-4ce5-b51c-9e08dbad5b85
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1a1de8b9a3431d79573cd916fa7273b6d8fa7f0b
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546378"
---
# <a name="manipulating-data-mdx"></a>データの操作 (MDX)

多次元式 (MDX) を使用すると、さまざまな方法でデータを操作できます。 この記事に記載されている記事では、MDX 言語でのデータ操作の高度な概念をいくつか取り上げています。

## <a name="in-this-section"></a>このセクションの内容

|トピック|説明|  
|-----------|-----------------|  
|[DRILLTHROUGH を使用したソース データの取得 (MDX)](mdx-data-manipulation-retrieve-source-data-using-drillthrough.md)|MDX の [DRILLTHROUGH](/sql/mdx/mdx-data-manipulation-drillthrough) ステートメントを使用して、多次元データ ソースのセルに適用できる変換元データの行セットを取得する方法を説明します。|  
|[RollupChildren 関数の操作 (MDX)](mdx-data-manipulation-rollupchildren-function.md)|MDX [Rollupchildren](/sql/mdx/rollupchildren-mdx)の影響について説明します。
|[パス順序と解決順序の概要 (MDX)](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)|解決順序の概念を詳しく説明し、その機能がどのように MDX 式、ステートメント、およびスクリプトに影響するかについても説明します。|  

<!-- ??

|[Script for Search and Replace] function on the analysis of multidimensional data.|

GeneMi is removing this commented row because it is unclear what article its link meant to link to.
Also, I had to add its leading '|' character, for consistency to aid bulk automated updated to our markdown source code.

GeneMi , 2019/01/19
-->

## <a name="see-also"></a>参照

[MDX クエリの基礎 (Analysis Services)](mdx-query-fundamentals-analysis-services.md)
