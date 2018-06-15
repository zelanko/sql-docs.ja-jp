---
title: MDX (MDX) の計算されるメンバーを作成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9235b9e3531e2ca40cabe211d85c077e629dacee
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021789"
---
# <a name="mdx-calculated-members---building-calculated-members"></a>MDX の計算されるメンバーの計算されるメンバーの構築
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) では、値を返す MDX 式の計算によって解決されるメンバーのことを、計算されるメンバーといいます。 これは一見なにげない定義ですが、非常に広範囲に影響を及ぼします。 MDX クエリで計算されるメンバーを作成して使用する機能によって、多次元データの操作能力が大幅に向上するからです。  
  
 計算されるメンバーは、階層内のどこにでも作成できます。 また、キューブ内の既存のメンバーだけでなく、同じ MDX 式で定義された他の計算されるメンバーにも依存するように、計算されるメンバーを作成することもできます。  
  
 計算されるメンバーの定義では、以下のいずれかのコンテキストを設定できます。  
  
-   **クエリ スコープ** MDX クエリの一部として定義する、計算されるメンバーを作成する場合 (スコープをそのクエリに限定する場合) は、WITH キーワードを使用します。 その計算されるメンバーは、MDX の SELECT ステートメントの中で使用できます。 この方法では、WITH キーワードを使用して作成した計算されるメンバーを、SELECT ステートメントを修正せずに変更できます。  
  
     WITH キーワードを使用して計算されるメンバーを作成する方法の詳細については、「[クエリ スコープの計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members.md)」を参照してください。  
  
-   **セッション スコープ** クエリのコンテキストよりも広いスコープを設定して計算されるメンバーを作成する場合 (スコープを MDX セッションの有効期間全体とする場合) は、CREATE MEMBER ステートメントを使用します。 CREATE MEMBER ステートメントで定義した計算されるメンバーは、そのセッションのすべての MDX クエリで使用できます。 CREATE MEMBER ステートメントを使用する方法は、たとえば、さまざまなクエリで同じセットを使い回すクライアント アプリケーションで役立ちます。  
  
     CREATE MEMBER ステートメントを使用してセッションでの計算されるメンバーを作成する方法の詳細については、「[セッション スコープの計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MEMBER ステートメント & #40; を作成します。MDX と #41 です。](../../../mdx/mdx-data-definition-create-member.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-function-reference-mdx.md)   
 [SELECT ステートメント & #40 です。MDX と #41 です。](../../../mdx/mdx-data-manipulation-select.md)  
  
  
