---
title: NonEmptyCrossjoin (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d77262ce3f6cf4f9e9cb1720d42b1bcbd85f31f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580684"
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 *カウント*  
 返すセットの数を指定する有効な数値式です。  
  
## <a name="remarks"></a>コメント  
 **NonEmptyCrossjoin**関数は、データを基になるファクト テーブルによって提供されることがなく、空の組または組を除外して、セットとして 2 つ以上のセットのクロス積を返します。 によって**NonEmptyCrossjoin**関数の動作、すべての計算メンバーは自動的に除外します。  
  
 場合*カウント*が指定されていない、クロス関数は、指定したすべてのセットを結合し、結果セットから空のメンバーを除外します。 セットの数を指定した場合は、指定した最初のセットを先頭として、指定数のセットがクロス結合されます。 **NonEmptyCrossjoin**関数は、後続の指定したセットに指定されているがされていないクロスのどのメンバーは、結果として得られるクロス結合されたセットに空でないと見なされますの決定に参加している残りのセットを使用します。 **NonEmptyCrossjoin**関数は、 **NON_EMPTY_BEHAVIOR**計算されるメジャーの設定。  
  
> [!IMPORTANT]  
>  この関数は旧バージョンとの互換性を維持するために用意されており、非推奨とされます。 代わりに、使用する必要があります、 [Exists (MDX)](../mdx/exists-mdx.md)メジャー グループ名の引数を持つ関数または[NonEmpty (MDX)](../mdx/nonempty-mdx.md)関数。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
