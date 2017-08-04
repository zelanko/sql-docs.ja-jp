---
title: "MemberValue (MDX) |Microsoft ドキュメント"
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
- MEMBERVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- MemberValue function
ms.assetid: f9b2af16-2b81-48e4-ae81-99f64e4bbc98
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ede5ef1aa5903095bc990ed6871682ce341e77b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="membervalue-mdx"></a>MemberValue (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

