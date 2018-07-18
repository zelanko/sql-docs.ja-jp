---
title: Source 要素 (ComAssembly) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Source Element (ComAssembly)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Source
helpviewer_keywords:
- Source element
ms.assetid: 5c9209e8-ace6-4688-a64d-4987a7648ab9
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81076927595714ae4e0c98847d99f2d246660cf9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152973"
---
# <a name="source-element-comassembly-assl"></a>Source 要素 (ComAssembly) (ASSL)
  Component Object Model (COM) コンポーネント用のファイル名またはプログラム識別子 (ProgID) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ComAssembly>  
   ...  
   <Source>...</Source>  
   ...  
</ComAssembly>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ComAssembly](../data-type/assembly-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Source`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ComAssembly>します。  
  
## <a name="see-also"></a>参照  
 [Assembly 要素&#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../data-type/clrassembly-data-type-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Server 要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
