---
title: 先祖 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 16c6f812d1d7cae5a81a8e64fb425f4d33f4cb5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017061"
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)


  指定されたメンバー自体も含めたメンバーの先祖のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **先祖**関数は、メンバーの階層の最上位にあるメンバーの先祖をすべて返します。具体的には、指定されたメンバーの階層のポスト順序走査を実行し、そのメンバーに関連するすべての先祖メンバー (それ自体を含む) を set で返します。 これは、特定のレベルで特定の先祖メンバー (先祖) を返す[先祖](../mdx/ancestor-mdx.md)関数とは対照的です。  
  
## <a name="examples"></a>例  
 次の例では、 **Adventure works**キューブから、 `[Sales Territory].[Northwest]`メンバーの再販業者の注文数と、そのメンバーのすべての先祖を返します。 **先祖**関数は、ROWS 軸の`[Sales Territory].[Northwest]`メンバーとその先祖を含むセットを構築します。  
  
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
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
