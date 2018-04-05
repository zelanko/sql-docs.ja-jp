---
title: 関数 (MDX 構文) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MDX [Analysis Services], functions
- Multidimensional Expressions [Analysis Services], functions
- functions [MDX]
ms.assetid: 74ca5e79-1f33-4795-9d68-98eff9c190c1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 00259604fe891a21f6f52835b1844762a751f09a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="functions-mdx-syntax"></a>関数 (MDX 構文)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) には、特定の操作を実行するための固有の関数の分類がいくつかあります。 MDX で使用できる関数の分類を以下の表に示します。  
  
> [!NOTE]  
>  個々 の関数の詳細については、次を参照してください。 [MDX 関数リファレンス &#40;です。MDX と #41 です](../mdx/mdx-function-reference-mdx.md)。  
  
|関数の分類|Description|  
|-----------------------|-----------------|  
|配列関数|ストアド プロシージャで使用する配列を提供します。<br /><br /> 詳細については、次を参照してください。[ストアド プロシージャの使用 &#40;です。MDX と #41 です](../mdx/using-stored-procedures-mdx.md)。|  
|ディメンション関数|階層、レベル、またはメンバーから、ディメンションへの参照を返します。<br /><br /> 詳細については、次を参照してください。[を使用してディメンション、階層、およびレベル関数](../mdx/using-dimension-hierarchy-and-level-functions.md)です。|  
|階層関数|レベルまたはメンバーから、階層への参照を返します。<br /><br /> 詳細については、次を参照してください。[を使用してディメンション、階層、およびレベル関数](../mdx/using-dimension-hierarchy-and-level-functions.md)です。|  
|レベル関数|メンバー、ディメンション、階層、または文字列式から、レベルへの参照を返します。<br /><br /> 詳細については、次を参照してください。[を使用してディメンション、階層、およびレベル関数](../mdx/using-dimension-hierarchy-and-level-functions.md)です。|  
|論理関数|オブジェクトおよび式に対して論理演算および論理比較を実行します。<br /><br /> 詳細については、次を参照してください。[論理関数を使用して](../mdx/using-logical-functions.md)です。|  
|メンバー関数|他のオブジェクトまたは文字列式から、メンバーへの参照を返します。<br /><br /> 詳細については、次を参照してください。[メンバー関数を使用して](../mdx/using-member-functions.md)です。|  
|数値関数|オブジェクトおよび式に対して数学関数および統計関数を実行します。<br /><br /> 詳細については、次を参照してください。[数学関数を使用して](../mdx/using-mathematical-functions.md)です。|  
|集合関数|他のオブジェクトまたは文字列式から、集合への参照を返します。<br /><br /> 詳細については、次を参照してください。 [Set 関数を使用して](../mdx/using-set-functions.md)です。|  
|文字列関数|他のオブジェクトまたは他のサーバーから文字列値を返します。<br /><br /> 詳細については、次を参照してください。[文字列関数を使用して](../mdx/using-string-functions.md)です。|  
|組関数|集合または文字列式から、組への参照を返します。<br /><br /> 詳細については、「組関数の使用」を参照してください。|  
  
## <a name="uses-of-functions"></a>関数の使用  
 関数は、任意の MDX 式の中に含めて使用することができます。 関数は入れ子にすることもできます。入れ子とは、関数の内部にさらに関数を使用することです。  
  
## <a name="see-also"></a>参照  
 [MDX 構文の要素 &#40;です。MDX と #41 です](../mdx/mdx-syntax-elements-mdx.md)  
  
  
