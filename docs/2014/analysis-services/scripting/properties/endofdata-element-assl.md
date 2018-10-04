---
title: EndOfData 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EndOfData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EndOfData
helpviewer_keywords:
- EndOfData element
ms.assetid: 4cee48bc-d486-4125-9d65-f323c6ec9d09
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3f8d5b7038d767c6d261840edb63f9c1ebee7328
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211572"
---
# <a name="endofdata-element-assl"></a>EndOfData 要素 (ASSL)
  受信したデータの末尾を示す、 [PushedDataSource](../data-type/datasource-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PushedDataSource>  
   ...  
   <EndOfData>...</EndOfData>  
   ...  
</PushedDataSource  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[PushedDataSource](../data-type/datasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `PushedDataSource` からの最後のデータ パケットによって、`EndOfData` 要素が `True` に設定される必要があります。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
