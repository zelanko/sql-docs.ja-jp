---
title: OlapInfo 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- OlapInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#OlapInfo
- microsoft.xml.analysis.olapinfo
- urn:schemas-microsoft-com:xml-analysis#OlapInfo
- OLAPInfo
helpviewer_keywords:
- OlapInfo element
ms.assetid: 8828fdd7-c0f7-48ce-a0d0-ab4bc1a995cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 39cabfd1ce5e0dcbc815d1cc659fd4a4594be47b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48050692"
---
# <a name="olapinfo-element-xmla"></a>OlapInfo 要素 (XMLA)
  含まれる軸およびセル メタデータを含む、[ルート](root-element-xmla.md)を使用する要素、 [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <OlapInfo>  
      <CubeInfo>...</CubeInfo>  
      <AxesInfo>...</AxesInfo>  
      <CellInfo>...</CellInfo>  
   </OlapInfo>  
   ...  
</root>  
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
|親要素|[root](root-element-xmla.md)|  
|子要素|[AxesInfo](axesinfo-element-xmla.md)、 [CellInfo](cellinfo-element-xmla.md)、 [CubeInfo](cubeinfo-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `OLAPInfo` データ型を使用する `root` 要素の `MDDataSet` セクションは、キューブ、多次元結果の軸、および結果に含まれるセルのプロパティに関するメタデータを提供します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
