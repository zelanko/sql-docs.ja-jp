---
title: "または (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: OR
dev_langs: kbMDX
helpviewer_keywords: OR operator
ms.assetid: 7634c08a-5b70-44cd-9422-6555fed6ae05
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7cddabea47afb791fd4ec9f111d81248edc4c2f8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="or-mdx"></a>OR (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  2 つの数値式の論理和を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>パラメーター  
 Expression1  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 Expression2  
 数値を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 ブール値を返す**true**いずれかまたは両方の引数に評価される場合**true**、それ以外の**false**です。  
  
## <a name="remarks"></a>解説  
 **または**演算子はブール値として両方の引数を処理 (つまり、0 として**false**、それ以外の**true**) 論理和演算を実行します。 次の表に示す方法、**または**演算子が論理和演算を実行します。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**オプション**|**true**|  
|**オプション**|**true**|**true**|  
|**オプション**|**オプション**|**オプション**|  
  
## <a name="example"></a>例  
 次のクエリで計算されるメジャーは、Customer ディメンションの Gender 階層にある現在のメンバーが Male の場合、または Customer ディメンションの Marital Status 階層にある現在のメンバーが Married の場合、“MARRIED OR MALE” 文字列を返し、それ以外の場合は、“UNMARRIED OR FEMALE” 文字列を返します。  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
