---
title: (MDX) の予測 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca47db953df9889cb1d72d0add45f2b0ed681980
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277483"
---
# <a name="predict-mdx"></a>予測 (MDX)


    
> [!CAUTION]  
>  この関数は、内部不整合により削除処理中です。  
>   
>  DMX 式を使用して回避策の例のセクションを確認します。  
  
 データ マイニング モデルに対して評価される数値式の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Mining_Model_Name*  
 マイニング モデルの名前を表す有効な文字列式です。  
  
 *String_Expression*  
 指定されたマイニング モデルの有効な DMX 式に評価される有効な文字列式。  
  
## <a name="remarks"></a>コメント  
 **Predict**関数は、指定されたマイニング モデルのコンテキスト内で指定された文字列式を評価します。  
  
 データ マイニングの構文と関数は、データ マイニング式 (DMX) リファレンスに記載されています。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
