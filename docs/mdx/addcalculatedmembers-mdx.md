---
title: "AddCalculatedMembers (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ADDCALCULATEDMEMBERS
dev_langs: kbMDX
helpviewer_keywords: AddCalculatedMembers function
ms.assetid: c676cf70-7c24-46ea-b88c-d4a389a71d48
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3976939335164567f32810e700bb31199df4af89
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  計算されるメンバーを指定されたセットに追加して生成したセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>解説  
 既定では、セット関数を解決する際、計算されるメンバーは除外されます。 **AddCalculatedMembers**関数がで指定されたセット式を調べ*Set_Expression、*スコープ内に含まれるメンバーの兄弟である計算されるメンバーが含まれていますとそのセット式のです。  
  
> [!NOTE]  
>  この関数で使用できるのは、1 次元のセット式だけです。  
  
## <a name="examples"></a>使用例  
 この関数の使用例を以下に示します。  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 次の例を返します、`Measures.[Unit Price]`内のすべての計算されるメンバーだけでなく、メンバー、**メジャー**ディメンションから、 **Adventure Works**キューブ。  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
