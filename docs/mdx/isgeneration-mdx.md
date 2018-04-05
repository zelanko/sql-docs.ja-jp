---
title: IsGeneration (MDX) |Microsoft ドキュメント
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
- ISGENERATION
dev_langs:
- kbMDX
helpviewer_keywords:
- IsGeneration function
ms.assetid: fd11d2e0-d81d-45af-ac45-c98634d05550
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d1b73679fed735599104dd3588d298602e48d3e7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="isgeneration-mdx"></a>IsGeneration (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーが指定された世代内にあるかどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsGeneration(Member_Expression, Generation_Number)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Generation_Number*  
 指定されたメンバーの評価対象となる世代を指定する有効な数値式です。  
  
## <a name="remarks"></a>Remarks  
 **IsGeneration**関数が返される**true**指定されたメンバーが指定された世代番号内にある場合。 関数を返しますそれ以外の場合、 **false**です。 また、指定されたメンバーは、空のメンバーに評価された場合、 **IsGeneration**関数が返される**false**です。  
  
 世代インデックスの作成上の目的から、リーフ メンバーの世代インデックスは 0 になっています。 非リーフ メンバーの世代インデックスを判別するには、まず指定されたメンバーのすべての子メンバーの和集合から最高の世代インデックスを取得し、そのインデックスに 1 を加算します。 非リーフ メンバーの世代インデックスはこのような方法で決定されるので、1 つの非リーフ メンバーが複数の世代に属することもあり得ます。  
  
## <a name="example"></a>例  
 次の例では、[Date].[Fiscal].CurrentMember が 2 番目の世代の場合に TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISGENERATIONDEMO AS`  
  
 `IsGeneration([Date].[Fiscal].CURRENTMEMBER, 2)`  
  
 `SELECT {MEASURES.ISGENERATIONDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
