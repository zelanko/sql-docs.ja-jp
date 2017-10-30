---
title: "組式の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- single-member tuples [MDX]
- expressions [MDX], tuples
- one-member tuples
- tuples
- implicit tuples
ms.assetid: 0b802b76-9123-405e-ae43-d438754724ba
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f0d24279e896bc71faef81c5901d6d52069b717c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="using-tuple-expressions"></a>組式の使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  組は、キューブに含まれる各ディメンションの 1 つずつのメンバーから成っています。 そのため、組はキューブ内の 1 つのセルを一意に識別します。  
  
> [!NOTE]  
>  有効でない 1 つ以上のメンバーを参照する組は、空の組と呼ばれます。  
  
 組識別子の完全な式は、かっこの中に 1 つ以上のメンバーを明示的に指定して表します。  
  
 (*メンバー式*[、*メンバー式*...])  
  
 組は完全に修飾することができます。また、暗黙的なメンバーを含めることも、1 つのメンバーだけを含めることもできます。  
  
## <a name="tuples-and-implicit-members"></a>組と暗黙的なメンバー  
 キューブ内に含まれる各ディメンションからのメンバーを 1 つずつ明示的に指定した組は、完全修飾された組と呼ばれます。 ただし、すべての組が完全に修飾されている必要はありません。  
  
 組の中で明示的に参照されていないディメンションは、暗黙的に参照されます。 暗黙的に参照されたディメンションのメンバーは、ディメンションの構造とその中で定義されている属性リレーションシップによって異なります。 暗黙的に参照されている階層と同じディメンションの階層への明示的な参照があり、明示的に参照されている階層と暗黙的に参照されている階層との間に直接的または間接的なリレーションシップが定義されている場合、組は、明示的に参照されている階層のメンバーと共存する、暗黙的に参照されている階層のメンバーを含むように動作します。 たとえば、City 属性および Country 属性を持つ Customer ディメンションがキューブに含まれており、これら 2 つの属性間でリレーションシップが定義され、City に 1 つの Country が含まれ、Country に複数の City を含めることができるようになっている場合、明示的に City 'London' を組に含めると、Country 'United Kingdom' が暗黙的に参照されます。 ただし、属性リレーションシップが定義されておらず、リレーションシップの方向が逆になっている場合 (たとえば、City に Country とのリレーションシップがあっても、ある人が住んでいる Country がわかるだけで、住んでいる City を特定できない場合) や 2 つの属性間で直接的なリレーションシップが定義されていない場合 (たとえば、Customer から City へのリレーションシップと Customer から Country へのリレーションシップが定義されていても、City と Country 間のリレーションシップが定義されていない場合) は、次の規則が適用されます。  
  
-   暗黙的に参照された階層に既定のメンバーがある場合は、既定のメンバーが組に追加されます。  
  
-   暗黙的に参照された階層に既定のメンバーが存在しない場合、 **(すべて)**既定の階層のメンバーが使用されます。  
  
-   暗黙的に参照された階層に既定のメンバーがない場合は、その階層の最上位レベルにある最初のメンバーが使用されます。  
  
## <a name="one-member-tuples"></a>1 つのメンバーの組  
 組式に 1 つのメンバーしか指定されていない場合、MDX は、式を評価するためにそのメンバーを 1 つのメンバーのみの組に変換します。 つまり、組式の代わりにメンバー式 `[Measures].[TestMeasure]` を使用することは、組式 `( [Measures].[TestMeasure] ).` と機能的に等価です。  
  
## <a name="see-also"></a>参照  
 [式 & #40 です。MDX と #41 です。](../mdx/expressions-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

