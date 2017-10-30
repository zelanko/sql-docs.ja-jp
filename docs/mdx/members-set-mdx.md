---
title: "Members (セット) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 0c4d5bb9-500b-47ce-b7fc-f5a10e2400e0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4430d24665eb791b8567fa83e7793c64727fd88f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="members-set-mdx"></a>Members (セット) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディメンション、レベル、階層のメンバーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 階層式が指定されている場合、 **Members (セット)**関数は、計算されるメンバーを除く、指定された階層内のすべてのメンバーのセットを返します。 すべてのメンバー、計算のセットを取得またはそれ以外の場合、階層を使用する、 [AllMembers (& a) #40 です。MDX と #41 です。](../mdx/allmembers-mdx.md)関数  
  
 レベル式が指定されている場合、 **Members (セット)**関数は、指定されたレベル内のすべてのメンバーのセットを返します。  
  
> [!IMPORTANT]  
>  階層がディメンション内に 1 つしかない場合は、ディメンション名がその唯一の階層に解決されるので、ディメンション名または階層名でその階層を参照できます。 たとえば Measures.Members は、Measures ディメンション内の唯一の階層に解決されるため、有効な MDX 式です。  
  
## <a name="examples"></a>使用例  
 次の例では、Adventure Works キューブの Calendar Year 階層のすべてのメンバーのセットを返しています。  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 次の例では、`[Product].[Products].[Product Line]` レベルの各メンバーについて 2003 年の注文数量を返します。 **メンバー**関数を表すすべてのレベルにメンバー セットを返します。  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

