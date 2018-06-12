---
title: DataMember (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 98b10c951043416280c05fd6a0e5eeb5df92c104
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739491"
---
# <a name="datamember-mdx"></a>DataMember (MDX)


  ディメンションの非リーフ メンバーに関連付けられたシステム生成データ メンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX での概念をキー &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
