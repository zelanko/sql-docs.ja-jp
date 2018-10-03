---
title: キューブ要素 (OlapInfo) (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cube Element (OlapInfo)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords:
- Cube element
ms.assetid: c2b6fe41-6ad4-4181-98a9-3a2517f0b7cc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a85f4c0eaf73ac3e971894fbfc4e42eb6c6a5045
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48111222"
---
# <a name="cube-element-olapinfo-xmla"></a>Cube 要素 (OlapInfo) (XMLA)
  親キューブに関する情報を格納[CubeInfo](cubeinfo-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeInfo>  
   <Cube>  
      <CubeName>...</CubeName>  
      <LastDataUpdate>...</LastDataUpdate>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
   </Cube>  
   ...  
</CubeInfo>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeInfo](cubeinfo-element-xmla.md)|  
|子要素|[CubeName](name-element-xmla.md)、 [LastDataUpdate](../xml-elements-commands/update-element-xmla.md)、 [LastSchemaUpdate](lastschemaupdate-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
