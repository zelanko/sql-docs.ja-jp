---
title: 関数 (MDX 構文) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed7e1770323a9691c2fe63c0df88df77198153ab
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740731"
---
# <a name="functions-mdx-syntax"></a>関数 (MDX 構文)


  多次元式 (MDX) には、特定の操作を実行するための固有の関数の分類がいくつかあります。 MDX で使用できる関数の分類を以下の表に示します。  
  
> [!NOTE]  
>  個々 の関数の詳細については、次を参照してください。 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)です。  
  
|関数の分類|説明|  
|-----------------------|-----------------|  
|配列関数|ストアド プロシージャで使用する配列を提供します。<br /><br /> 詳細については、次を参照してください。[ストアド プロシージャの使用&#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)です。|  
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
 [MDX 構文の要素&#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
