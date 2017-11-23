---
title: "EndOfData 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EndOfData Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EndOfData
helpviewer_keywords: EndOfData element
ms.assetid: 4cee48bc-d486-4125-9d65-f323c6ec9d09
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e6fa054baa12bbfb93fac8714991cb20f48a4bb3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="endofdata-element-assl"></a>EndOfData 要素 (ASSL)
  受け取ったデータの末尾を示す、 [PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)要素。  
  
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
|親要素|[PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 最後のデータ パケット、 **PushedDataSource**設定する必要があります、 **EndOfData**要素**True**です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
