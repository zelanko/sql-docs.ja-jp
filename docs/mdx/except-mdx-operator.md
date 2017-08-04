---
title: "- (を除く)(MDX) |Microsoft ドキュメント"
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
- '-'
dev_langs:
- kbMDX
helpviewer_keywords:
- Except operator [MDX]
- '- (except operator)'
ms.assetid: 8971a09d-b254-4c4c-a099-103664783589
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d06de38c64dda440d04d49c498653bcb52f8c6fa
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="except-mdx-operator"></a>(MDX) 演算子を除く
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  2 つのセットの重複メンバーを削除して差集合を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression - Set_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="return-value"></a>戻り値  
 指定した両方のパラメーターによって共有されていないメンバーを含むセットです。  
  
## <a name="remarks"></a>解説  
 **- (Except)**演算子は機能的に等価、[を除く](../mdx/except-mdx-function.md)関数。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を次に示します。  
  
```  
// This query shows the quantity of orders for all product categories  
// with the exception of Components.  
SELECT   
   [Measures].[Order Quantity] ON COLUMNS,  
   [Product].[Product Categories].[All].Children   
   - [Product].[Product Categories].[Components] ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  

