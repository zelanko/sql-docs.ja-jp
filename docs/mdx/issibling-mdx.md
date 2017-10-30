---
title: "IsSibling (MDX) |Microsoft ドキュメント"
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
- ISSIBLING
dev_langs:
- kbMDX
helpviewer_keywords:
- IsSibling function
ms.assetid: 12f302f0-141e-4ec0-ad5f-329aade17a4d
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bc48def38a353f94531aad4f56c659f959caffb2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="issibling-mdx"></a>IsSibling (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたメンバーが指定された別のメンバーの兄弟かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsSibling(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression1*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Member_Expression2*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **IsSibling**関数が返される**true**メンバーは、2 番目の指定されたメンバーの兄弟、最初に指定した場合。 関数を返しますそれ以外の場合、 **false**です。  
  
## <a name="example"></a>例  
 次の例では、Date ディメンションの Fiscal 階層の現在のメンバーが July 2002 の兄弟である場合、TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISSIBLINGDEMO AS`  
  
 `IsSibling([Date].[Fiscal].CURRENTMEMBER, [Date].[Fiscal].[Month].&[2002]&[7])`  
  
 `SELECT {MEASURES.ISSIBLINGDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

