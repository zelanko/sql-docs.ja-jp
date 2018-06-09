---
title: 先祖 (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ef9cccb488cebb08c1b9721c40cb8037ea8687a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739621"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  指定されたメンバー自体も含めたメンバーの先祖のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **先祖**関数では、すべてのメンバーの先祖を返しますメンバーの階層の最上位までメンバーから以外の場合は具体的には、指定されたメンバーの階層の逆順にたどってを実行しを返します。 すべての先祖メンバーに関連すると、メンバーをセット自体も含めたです。 これは、対照的に、[先祖](../mdx/ancestor-mdx.md)関数で、特定の先祖メンバー、または特定のレベルの先祖を返します。  
  
## <a name="examples"></a>使用例  
 次の例は、再販業者の注文の数を返します、`[Sales Territory].[Northwest]`メンバーとそのメンバーからのすべての先祖、 **Adventure Works**キューブ。 **先祖**関数を含むセットを構築、`[Sales Territory].[Northwest]`メンバーとその先祖 ROWS 軸のです。  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
