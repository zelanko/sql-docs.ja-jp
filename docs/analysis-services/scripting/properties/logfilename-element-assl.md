---
title: "LogFileName 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
apiname:
- LogFileName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- LogFileName
helpviewer_keywords:
- LogFileName element
ms.assetid: 80c7530d-ef73-44c3-88b5-c11c0f290946
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c6a63ce9d911bc029489ed5ddcd03be97f7e79d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="logfilename-element-assl"></a>LogFileName 要素 (ASSL)
  ログ ファイルのファイル名を含む、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <LogFileName>...</LogFileName>  
   ...  
</Trace>  
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
|親要素|[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 インスタンスのログ フォルダーにログ ファイルが保存された[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 親に対応する要素**LogFileName**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Traces 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

