---
title: "ルート要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Root Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Root
helpviewer_keywords:
- Root element
ms.assetid: ad3319d5-c3f0-49e3-b9c0-2fb77945c512
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c43bf6b3a6c9d4a14a738db38f7e7be09f5c8a68
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="root-element-assl"></a>Root 要素 (ASSL)
  データ ソースのデータ (行セット) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<PushedDataSource>  
   ...  
   <Root>...</Root>  
   ...  
</PushedDataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[行セット]|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[PushedDataSource](../../../analysis-services/scripting/data-type/pusheddatasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

