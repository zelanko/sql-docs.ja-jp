---
title: "ファイルの要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: File Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: File
helpviewer_keywords: File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1dfd2a68c0d5c6d8f67c034dd6b86b6fdeb640e1
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="file-element-assl"></a>File 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]構成するファイルのいずれかを定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[ファイル]](../../../analysis-services/scripting/collections/files-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ファイル**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Database 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Assemblies 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Assembly 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [ClrAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [データ要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
