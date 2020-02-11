---
title: Predict (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 165d03b886ad8e9beeb09bf5a835c879cc23a2a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055585"
---
# <a name="predict-mdx"></a>Predict (MDX)


    
> [!CAUTION]  
>  この関数は、内部不整合により削除処理中です。  
>   
>  DMX 式を使用する回避策については、「例」のセクションを参照してください。  
  
 データマイニングモデルに対して評価される数値式の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Mining_Model_Name*  
 マイニング モデルの名前を表す有効な文字列式です。  
  
 *String_Expression*  
 指定されたマイニングモデルの有効な DMX 式に評価される有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **Predict**関数は、指定されたマイニングモデルのコンテキスト内で指定された文字列式を評価します。  
  
 データマイニングの構文と関数については、「データマイニング式 (DMX) リファレンス」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、Customer Clusters マイニング モデルを使用して特定の顧客のクラスターの名前とその距離を予測します。  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
