---
title: "MDX 構文の要素 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], syntax
- MDX [Analysis Services], syntax
ms.assetid: f4c16e1a-cf1a-4be0-839a-db018430ff14
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: bf017bbd828a07418b6e05dd8a55a404952f5dd7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-syntax-elements-mdx"></a>MDX 構文の要素 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) には、以下に示すような、ほとんどのステートメントで使用される要素、およびほとんどのステートメントに影響を与える要素があります。  
  
|項目|定義|  
|----------|----------------|  
|[識別子](../mdx/identifiers-mdx.md)|識別子とは、キューブ、ディメンション、メンバー、メジャーなどのオブジェクトの名前です。|  
|**データ型**|セル、メンバー プロパティ、セル プロパティに格納されるデータの型を定義します。 MDX は OLE VARIANT データ型だけをサポートします。 VARIANT データ型の強制型変換、変換、および操作の詳細については、プラットフォーム SDK ドキュメントの「VARIANT と VARIANTARG」を参照してください。|  
|[式 &#40;です。MDX と #41 です。](../mdx/expressions-mdx.md)|式は、構文の単位を[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]単一 (スカラー) 値またはオブジェクトを解決することができます。 式には、単一値、セット式などを返す関数も含まれます。|  
|[演算子](../mdx/operators-mdx-syntax.md)|演算子とは、より複雑な MDX 式を作成するために 1 つ以上の単純 MDX 式と共に使用される構文要素です。|  
|[関数](../mdx/functions-mdx-syntax.md)|関数とは、0 個以上の入力値を受け入れてスカラー値またはオブジェクトを返す構文要素です。 例としては、[合計](../mdx/sum-mdx.md)いくつかの値を追加するための関数、[メンバー](../mdx/members-set-mdx.md)し、ディメンションまたはレベルからメンバーのセットを返すために機能します。|  
|[コメント](../mdx/comments-mdx-syntax.md)|コメントとは、ステートメントの用途を説明するために MDX ステートメントまたはスクリプトに挿入されるテキストです。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]コメントは実行されません。|  
|[予約済みキーワード](../mdx/reserved-keywords-mdx-syntax.md)|予約されたキーワードとは、MDX で使用するために予約されている単語です。MDX ステートメント内では予約されたキーワードをオブジェクト名として使用できません。|  
|[メンバー、組、およびセット](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|メンバー、組、セットは、多次元データの中心的な概念です。MDX クエリを作成する前に、これらを理解しておく必要があります。|  
  
## <a name="see-also"></a>参照  
 [多次元式 &#40;です。MDX と #41 です。参照](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
