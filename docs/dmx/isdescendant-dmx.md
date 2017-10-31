---
title: "IsDescendant (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IsDescendant
dev_langs:
- DMX
helpviewer_keywords:
- IsDescendant function
ms.assetid: d9fe7446-edb5-487b-8ea6-c9efaccf6d90
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4a1e7959a303b768851784af0ab9c88abd257674
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="isdescendant-dmx"></a>IsDescendant (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のノードが、指定したノードからの降順であるかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsDescendant(<NodeID>)  
```  
  
## <a name="return-type"></a>戻り値の型  
 Boolean 型。  
  
## <a name="remarks"></a>解説  
 **IsDescendant**だけで使われる[SELECT FROM &#60; モデル &#62;。コンテンツ &#40;DMX"&"#41;](../dmx/select-from-model-content-dmx.md)と[SELECT FROM &#60; モデル &#62;。DIMENSION_CONTENT &#40;DMX"&"#41;](../dmx/select-from-model-dimension-content-dmx.md)クエリ。  
  
## <a name="examples"></a>使用例  
 次の例は、IsDescendant 関数に指定されたノードの子孫であるケースをすべて返します。  
  
```  
SELECT * FROM [TM Decision Tree].CONTENT  
WHERE IsDescendant('00000000100')  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 &#40;DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 &#40;DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  

