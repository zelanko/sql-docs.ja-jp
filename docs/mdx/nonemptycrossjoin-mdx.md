---
title: NonEmptyCrossjoin (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7da56ac658f57d6eb664762f9dd94351df39fe0f
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63456567"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)


  1 つ以上のセットのクロス積を含むセットを返します。ただし、空の組と、ファクト テーブル データに関連付けられていない組は含まれません。  
  
## <a name="syntax"></a>構文  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Count*  
 返されるセットの数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **NonEmptyCrossjoin**関数は、データを基になるファクト テーブルによって提供されることがなく、空の組または組を除外し、セットとして 2 つ以上のセットのクロス積を返します。 によって**NonEmptyCrossjoin**関数の動作では、すべての計算メンバーは自動的に除外します。  
  
 場合*カウント*が指定されていない、クロス関数は、指定したすべてのセットを結合し、結果セットから空のメンバーを除外します。 セットの数が指定されている場合、関数はクロス結合の番号を指定した場合、最初のセットを指定して起動設定になります。 **NonEmptyCrossjoin**関数は、後続の指定されたセットで指定されているがされていないクロスのどのメンバーは、最終的なクロス結合されたセットは空でないと見なされますの決定に参加している残りのセットを使用します。 **NonEmptyCrossjoin**関数は、 **NON_EMPTY_BEHAVIOR**計算されるメジャーの設定。  
  
> [!IMPORTANT]  
>  この関数は旧バージョンとの互換性を維持するために用意されており、非推奨とされます。 代わりに、使用する必要があります、 [Exists (MDX)](../mdx/exists-mdx.md)メジャー グループ名の引数を持つ関数または[NonEmpty (MDX)](../mdx/nonempty-mdx.md)関数。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
