---
description: DataMember (MDX)
title: DataMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7291a8d2c57d4a996893146e8e855df234ed0139
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413138"
---
# <a name="datamember-mdx"></a>DataMember (MDX)


  ディメンションの非リーフメンバーに関連付けられているシステムによって生成されたデータメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>引数  
 *Member_Expression*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 この関数は、任意の階層の非リーフメンバーに対して動作し、 [UPDATE CUBE ステートメント (MDX)](../mdx/mdx-data-manipulation-update-cube.md) コマンドで使用して、リーフメンバーの子孫ではなく、非リーフメンバーに直接データを書き戻すことができます。  
  
> [!NOTE]  
>  指定されたメンバーがリーフメンバーである場合、または非リーフメンバーに関連付けられたデータメンバーがない場合は、指定されたメンバーを返します。  
  
## <a name="example"></a>例  
 次の例では、各従業員の販売ノルマを示すために、計算されるメジャーで **DataMember** 関数を使用します。  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX の主な概念 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)  
  
  
