---
title: サブセット (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e063d295480cff8e5db44f5ea30668a7a06ff74b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581394"
---
# <a name="subset-mdx"></a>Subset (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットから、組のサブセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Subset(Set_Expression, Start [ ,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *開始*  
 返す最初の組の位置を指定する有効な数値式です。  
  
 *カウント*  
 返す組の数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 指定したセットから、**サブセット**関数が指定された数の組を指定した開始位置を格納しているサブセットを返します。 開始位置は 0 を基点とするインデックスです。つまり、0 は指定したセットの最初の組に対応し、1 は次の組に対応します。  
  
 場合*カウント*が指定されていない、関数からのすべての組を返します*開始*セットの末尾にします。  
  
## <a name="example"></a>例  
 次の例では、階層とは無関係に、Reseller Gross Profit に基づいて、売上が上位 5 番目までの製品のサブカテゴリに対応する Reseller Sales メジャーを返しています。 **サブセット**関数を使用してを使用して結果を並べ替えてから、結果の最初の 5 つのセットのみを返す、**順序**関数。  
  
```  
SELECT Subset  
   (Order   
      ([Product].[Product Categories].[SubCategory].members  
         ,[Measures].[Reseller Gross Profit]  
         ,BDESC  
      )  
   ,0  
   ,5  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
