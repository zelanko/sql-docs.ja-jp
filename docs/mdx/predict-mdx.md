---
title: "予測 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PREDICT
dev_langs:
- kbMDX
helpviewer_keywords:
- Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7bec1c96bd70b9b75c3a8c212cf1f6c04c27c73e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="predict-mdx"></a>Predict (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

    
> [!CAUTION]  
>  この関数は、内部不整合により削除処理中です。  
>   
>  DMX 式を使用した回避策の例のセクションを参照してください。  
  
 データ マイニング モデルに対して評価される数値式の値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Mining_Model_Name*  
 マイニング モデルの名前を表す有効な文字列式です。  
  
 *String_Expression*  
 指定されたマイニング モデルの有効な DMX 式に評価される有効な文字列式です。  
  
## <a name="remarks"></a>解説  
 **Predict**関数は、指定されたマイニング モデルのコンテキスト内で指定された文字列式を評価します。  
  
 データ マイニングの構文と関数については、データ マイニング式 (DMX) のリファレンスを参照してください。  
  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

