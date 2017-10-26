---
title: "CubeInfo 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- CubeInfo Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CubeInfo
- microsoft.xml.analysis.cubeinfo
- urn:schemas-microsoft-com:xml-analysis#CubeInfo
helpviewer_keywords:
- CubeInfo element
ms.assetid: a504bac5-4bf2-4f78-a288-e74a34eaa97e
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3d79cf9b3fd8ada51fabfacce8da107c02f7ad69
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="cubeinfo-element-xmla"></a>CubeInfo 要素 (XMLA)
  親に含まれるキューブのメタデータを含む[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<OlapInfo>  
   ...  
   <CubeInfo>  
      <Cube>...</Cube>  
   </CubeInfo>  
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
|親要素|[OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|子要素|[Cube](../../../analysis-services/xmla/xml-elements-properties/cube-element-olapinfo-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **CubeInfo**要素が 1 つを含む**キューブ**多次元データセットで参照される各キューブの要素。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ただ 1 つを返します**キューブ**このコレクション内の要素のため[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]多次元式 (の FROM 句で複数のキューブを参照するステートメントをサポートしていませんMDX) 言語。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

