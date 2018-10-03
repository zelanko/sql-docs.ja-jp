---
title: AxesInfo 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AxesInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#AxesInfo
- microsoft.xml.analysis.axesinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#AxesInfo
helpviewer_keywords:
- AxesInfo element
ms.assetid: 15cfa67d-5acd-4737-8a81-2df34b334d3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7bde7feb88ad570665200c1c3357bbba4127a963
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178492"
---
# <a name="axesinfo-element-xmla"></a>AxesInfo 要素 (XMLA)
  コレクションを含む[AxisInfo](axisinfo-element-xmla.md)要素を親に含まれる軸のメタデータを表す[OlapInfo](olapinfo-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<OlapInfo>  
   ...  
   <AxesInfo>  
      <AxisInfo>...</AxisInfo>  
   </AxesInfo>  
   ...  
</OlapInfo>  
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
|親要素|[OlapInfo](olapinfo-element-xmla.md)|  
|子要素|[AxisInfo](axisinfo-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `AxesInfo` 要素は、`AxisInfo` 要素によって `root` データ型を使用して返される多次元データセット内のそれぞれの軸ごとに、1 つの `MDDataSet` 要素を含みます。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
