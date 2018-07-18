---
title: ファイルの要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- File
helpviewer_keywords:
- File element
ms.assetid: 21c70707-d2f8-4040-9acb-cbce23076bcc
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 03b78545b1df04192a69dffa1a49733509b99700
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155354"
---
# <a name="file-element-assl"></a>File 要素 (ASSL)
  構成するファイルのいずれかを定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [ClrAssembly](../data-type/assembly-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Files>  
   <File xsi:type="ClrAssemblyFile">...</File>  
</Files>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[ファイル]](../collections/files-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Files`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素&#40;ASSL&#41;](server-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](database-element-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Assembly 要素&#40;ASSL&#41;](assembly-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [データ要素&#40;ASSL&#41;](data-element-assl.md)   
 [DataBlock データ型&#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](block-element-assl.md)   
 [ComAssembly データ型&#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
