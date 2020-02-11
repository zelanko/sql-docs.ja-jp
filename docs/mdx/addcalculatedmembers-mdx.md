---
title: Add演算メンバー (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 982484b729b59a7106b6195e361110c1d4012653
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017183"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  計算されるメンバーを指定されたセットに追加することによって生成されるセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 既定では、MDX は、セット関数を解決するときに、計算されるメンバーを除外します。 **Add演算メンバー**関数は、 *Set_Expression*で指定されたセット式を調べ、そのセット式のスコープ内に含まれるメンバーの兄弟である計算されるメンバーを含みます。  
  
> [!NOTE]  
>  この関数で使用できるのは、1 次元のセット式だけです。  
  
## <a name="examples"></a>例  
 この関数の使用例を次に示します。  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 次の例では`Measures.[Unit Price]` 、 **Adventure works**キューブから、 **Measures**ディメンション内のすべての計算されるメンバーに加えて、メンバーが返されます。  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
