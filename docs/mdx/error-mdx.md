---
title: エラー (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6644318053321ae5189a70a2bd2c1f0e67d092fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691332"
---
# <a name="error-mdx"></a>Error (MDX)


  必要に応じて指定したエラー メッセージを提供するエラーが発生します。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
