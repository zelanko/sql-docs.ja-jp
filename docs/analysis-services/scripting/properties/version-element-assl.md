---
title: "Version 要素 (ASSL) |Microsoft ドキュメント"
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
- Version Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Version
helpviewer_keywords:
- Version element
ms.assetid: fb26fe5d-de40-443b-a8bc-031c950552e6
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: da0d8a1b101dd16fe9e7b94a0538a8b73c732e64
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="version-element-assl"></a>Version 要素 (ASSL)
  インスタンスの読み取り専用のバージョン番号を含む[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]によって表される、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Server>  
      ...  
      <Version>...</Version>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[サーバー]](../../../analysis-services/scripting/objects/server-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **バージョン**要素のバージョンを記述する[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]がインストールされています。  
  
 親に対応する要素**バージョン**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Server>します。  
  
## <a name="see-also"></a>参照  
 [Edition 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/edition-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

