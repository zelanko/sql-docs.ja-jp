---
title: 先祖 (MDX) |Microsoft ドキュメント
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
f1_keywords:
- ASCENDANTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 7eb0bff443065cff7a279320d85d848ae303f5dd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバー自体も含めたメンバーの先祖のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
