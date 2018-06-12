---
title: MemberValue (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 73a54986a951095b16465cd4934b4dfd447d38bb
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742171"
---
# <a name="membervalue-mdx"></a>MemberValue (MDX)


  メンバーの値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.MemberValue  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーに評価される有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 次の情報を含むメンバー値を返します。次の情報は、戻り値に情報が示される順序で表示されています。  
  
-   定義されている場合は、値のバインド。  
  
-   名前のバインドが存在しないか、キーとキャプションが同じ列にバインドされている場合は、元のデータ型のキー。  
  
-   メンバーのキャプション。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の Date ディメンションの最初の日付の値のバインド、メンバー キー、およびキャプションを返します。  
  
```  
WITH MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn}  ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
