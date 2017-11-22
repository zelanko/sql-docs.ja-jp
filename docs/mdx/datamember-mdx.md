---
title: "DataMember (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DATAMEMBER
dev_langs: kbMDX
helpviewer_keywords: DataMember function
ms.assetid: 65bf21e8-1cb2-4ae8-bfbe-bb4d72589557
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3f002e188055f7643d75e63506a95387198e99b4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="datamember-mdx"></a>DataMember (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディメンションの非リーフ メンバーに関連付けられたシステム生成データ メンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 この関数は、任意の階層の非リーフ メンバーに対して演算を行いで使用できる、 [UPDATE CUBE ステートメント (MDX)](../mdx/mdx-data-manipulation-update-cube.md)リーフ メンバーの子孫ではなく、直接、非リーフ メンバーに、書き戻しデータをコマンド。  
  
> [!NOTE]  
>  指定したメンバーがリーフ メンバーである場合、または非リーフ メンバーに関連付けられたデータ メンバーが存在しない場合は、指定したメンバーが返されます。  
  
## <a name="example"></a>例  
 次の例では、 **DataMember**各従業員の販売ノルマを表示する、計算されるメジャー内の関数。  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [MDX &#40; の主な概念Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
