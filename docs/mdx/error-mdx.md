---
title: "エラー (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ERROR
dev_langs: kbMDX
helpviewer_keywords: Error function
ms.assetid: 2caac19b-b297-443e-9299-648ef88a5039
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5b17e524eaf357988b3fb7c4ee46a0ba25e6df18
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="error-mdx"></a>Error (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  エラーを発生させます。指定されたエラー メッセージを示すこともできます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>引数  
 *Error_Text*  
 返すエラー メッセージを格納した有効な文字列式です。  
  
## <a name="examples"></a>使用例  
 次のクエリを使用する方法を示しています、**エラー**計算されるメジャー内の関数。  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
