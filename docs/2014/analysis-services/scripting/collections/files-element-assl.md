---
title: ファイルの要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Files Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Files
helpviewer_keywords:
- Files element
ms.assetid: 8a1327cb-1f60-42a7-b8ef-213d45a63e55
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 91fd214a87ea266a1c5849211bd30237b4313b20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078622"
---
# <a name="files-element-assl"></a>Files 要素 (ASSL)
  コレクションを格納[ファイル](../objects/file-element-assl.md)を構成する要素を[ClrAssembly](../data-type/assembly-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Assembly xsi:type="ClrAssembly">  
   ...  
   <Files>  
      <File xsi:type="ClrAssemblyFile">...</File>  
   </Files>  
   ...  
</Assembly>  
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
|親要素|[アセンブリ](../objects/assembly-element-assl.md)型の[ClrAssembly](../data-type/assembly-data-type-assl.md)|  
|子要素|[ファイル](../objects/file-element-assl.md)型の[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssemblyFileCollection>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](assemblies-element-assl.md)   
 [データ要素&#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock データ型&#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [要素のブロック&#40;ASSL&#41;](blocks-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../objects/block-element-assl.md)   
 [ComAssembly データ型&#40;ASSL&#41;](../data-type/comassembly-data-type-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
