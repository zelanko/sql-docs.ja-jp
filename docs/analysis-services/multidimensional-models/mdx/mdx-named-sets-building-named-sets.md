---
title: 名前付き MDX (MDX) のセットの構成 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b893dcd86ffcfa68c55057796c431e694903c46a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62740062"
---
# <a name="mdx-named-sets---building-named-sets"></a>MDX 名前付きセット - 名前付きセットの構築
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  セット式は、長く複雑な宣言になることがあり、そのような場合は読みにくく、理解するのが難しい式になります。 また、同じセット式を頻繁に使用する場合に、その同じセットを繰り返し定義しなければならないのは面倒です。 長く複雑な式や頻繁に使用する式の取り扱いを簡略化するために、多次元式 (MDX) では、そのような式を *名前付きセット*として定義できるようになっています。  
  
 基本的に、名前付きセットとは、別名を割り当てたセット式です。 名前付きセットには、通常 1 つのセットに組み込めるメンバーや関数を任意に組み込めます。 MDX では、名前付きセットの別名をセット式として取り扱うので、セット式を使用できる場所であればどこででもその別名を使用できます。  
  
 名前付きセットの定義では、以下のいずれかのコンテキストを設定できます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義される名前付きセットを作成する場合 (つまり、スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その名前付きセットは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した名前付きセットを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して名前付きセットを作成する方法の詳細については、「[クエリ スコープの名前付きセットの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して名前付きセットを作成する場合 (つまり、スコープを MDX セッションの有効期間全体とする場合) は、CREATE SET ステートメントを使用します。 CREATE SET ステートメントで定義した名前付きセットは、そのセッションのすべての MDX クエリで使用できます。 CREATE SET ステートメントを使用する方法は、たとえば、さまざまなクエリで 1 つのセットを使い回すクライアント アプリケーションで役立ちます。  
  
     CREATE SET ステートメントを使用してセッションでの名前付きセットを作成する方法の詳細については、「[セッション スコープの名前付きセットの作成 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [SELECT ステートメント &#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md)   
 [CREATE SET ステートメント (MDX)](../../../mdx/mdx-data-definition-create-set.md)   
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
