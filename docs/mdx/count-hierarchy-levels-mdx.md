---
title: Count (階層レベル) (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cc09cf02cb0ee75788cbd2e6ff9e9d99ab34e784
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577574"
---
# <a name="count-hierarchy-levels-mdx"></a>Count (階層レベル) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  階層内のレベル数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 階層内のレベル数を返します。`[All]` レベルがある場合はこれも含みます。  
  
> [!IMPORTANT]  
>  表示可能な階層がディメンション内に 1 つしかない場合は、ディメンション名がその 1 つしかない階層に解決されるため、その階層はディメンション名でも階層名でも参照できます。 たとえば、`Measures.Levels.Count`有効な MDX 式は、Measures ディメンション内の唯一の階層に解決されるためです。  
  
## <a name="example"></a>例  
 次の例は、Adventure Works キューブ内のユーザー定義階層 Product Categories 内のレベル数を返します。  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント&#40;ディメンション&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [カウント&#40;組&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)   
 [カウント&#40;設定&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
