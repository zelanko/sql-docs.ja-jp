---
title: CubeInfo 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CubeInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#CubeInfo
- microsoft.xml.analysis.cubeinfo
- urn:schemas-microsoft-com:xml-analysis#CubeInfo
helpviewer_keywords:
- CubeInfo element
ms.assetid: a504bac5-4bf2-4f78-a288-e74a34eaa97e
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcac19d70af83ec8e83ebf8bac06507ba9e28b82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229592"
---
# <a name="cubeinfo-element-xmla"></a>CubeInfo 要素 (XMLA)
  親に含まれるキューブのメタデータを含む[OlapInfo](olapinfo-element-xmla.md)要素。  
  
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
|親要素|[OlapInfo](olapinfo-element-xmla.md)|  
|子要素|[Cube](cube-element-olapinfo-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `CubeInfo` 要素は、多次元データセット内で参照される各キューブごとに 1 つの `Cube` 要素を含みます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] は多次元式 (MDX) 言語の FROM 句内で複数のキューブを参照するステートメントをサポートしないため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はこのコレクション内に 1 つの `Cube` 要素だけを返します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
