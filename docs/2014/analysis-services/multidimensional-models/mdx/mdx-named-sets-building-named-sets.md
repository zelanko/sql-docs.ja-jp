---
title: MDX での名前付きセットの作成 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98d363ab09e75905b13503687fe425a981c790e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074144"
---
# <a name="building-named-sets-in-mdx-mdx"></a>MDX での名前付きセットの作成 (MDX)
  セット式は、長く複雑な宣言になることがあり、そのような場合は読みにくく、理解するのが難しい式になります。 また、同じセット式を頻繁に使用する場合に、その同じセットを繰り返し定義しなければならないのは面倒です。 長く複雑な式や頻繁に使用する式の取り扱いを簡略化するために、多次元式 (MDX) では、そのような式を *名前付きセット*として定義できるようになっています。  
  
 基本的に、名前付きセットとは、別名を割り当てたセット式です。 名前付きセットには、通常 1 つのセットに組み込めるメンバーや関数を任意に組み込めます。 MDX では、名前付きセットの別名をセット式として取り扱うので、セット式を使用できる場所であればどこででもその別名を使用できます。  
  
 名前付きセットの定義では、以下のいずれかのコンテキストを設定できます。  
  
-   **クエリスコープ**MDX クエリの一部として定義されている名前付きセットを作成し、そのスコープをそのクエリに限定する場合は、WITH キーワードを使用します。 その名前付きセットは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した名前付きセットを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して名前付きセットを作成する方法の詳細については、「[クエリ スコープの名前付きセットの作成 (MDX)](mdx-named-sets-creating-query-scoped-named-sets.md)」を参照してください。  
  
-   **セッションスコープ**スコープが MDX セッションの有効期間である、クエリのコンテキストよりも広いスコープを持つ名前付きセットを作成するには、CREATE SET ステートメントを使用します。 CREATE SET ステートメントで定義した名前付きセットは、そのセッションのすべての MDX クエリで使用できます。 CREATE SET ステートメントを使用する方法は、たとえば、さまざまなクエリで 1 つのセットを使い回すクライアント アプリケーションで役立ちます。  
  
     CREATE SET ステートメントを使用してセッションでの名前付きセットを作成する方法の詳細については、「[セッション スコープの名前付きセットの作成 (MDX)](mdx-named-sets-creating-session-scoped-named-sets.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SELECT ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)   
 [CREATE SET ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-set)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
