---
title: ': (範囲) (MDX) |Microsoft ドキュメント'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 152158128a58cc2df12c0975b9c00976800fe64d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581194"
---
# <a name="-range-mdx"></a>: (範囲) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  自然な順序で並べたセットを返すセット演算を実行します。指定された 2 つのメンバーが終端になり、その 2 つのメンバーの間にあるすべてのメンバーがセットのメンバーに含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression : Member_Expression      
```  
  
#### <a name="parameters"></a>パラメーター  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 指定されているメンバーと、指定されているメンバーの間にあるすべてのメンバーを含むセットです。  
  
## <a name="remarks"></a>コメント  
 両方のパラメーターに、ディメンションの同じレベルと同じ階層にあるメンバーを指定する必要があります。 両方のパラメーターが、同じメンバーを指定した場合、 **: (範囲)** 演算子が指定されたメンバーのみを含むセットを返します。 最初のパラメーターが NULL の場合、2 番目のパラメーターで指定されたメンバーのレベルの、最初のメンバーからその指定されたメンバー (その指定されたメンバーを含む) までのすべてのメンバーがセットに含まれます。 2 番目のパラメーターが NULL の場合、最初のパラメーターで指定されたメンバーから同じレベルの最後のメンバー (最後のメンバーを含む) までのすべてのメンバーがセットに含まれます。  
  
 MDX にこのセット演算子と等価な関数はありません。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This query returns the freight cost per user  
-- for products, averaged by month, for the first quarter.  
With Member [Measures].[Freight Per Customer] as  
 (  
     [Measures].[Internet Freight Cost]  
     /   
     [Measures].[Customer Count]  
)  
  
SELECT   
    {[Ship Date].[Calendar].[Month].&[2004]&[1] : [Ship Date].[Calendar].[Month].&[2004]&[3]} ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Freight Per Customer])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
