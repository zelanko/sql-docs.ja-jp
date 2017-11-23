---
title: "ClrAssemblyFile データ型 (ASSL) |Microsoft ドキュメント"
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
apiname: ClrAssemblyFile Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ClrAssemblyFile
helpviewer_keywords: ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4af3de4002b9520654b344c3e393cdab1848fa20
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="clrassemblyfile-data-type-assl"></a>ClrAssemblyFile データ型 (ASSL)
  構成するファイルのいずれかを表すプリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] **アセンブリ**([ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)要素)。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClrAssemblyFile>  
   <Name>...</Name>  
      <Type>...</Type>  
      <Data>...</Data>  
</ClrAssemblyFile>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[データ](../../../analysis-services/scripting/objects/data-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[型](../../../analysis-services/scripting/properties/type-element-clrassemblyfile-assl.md)|  
|派生要素|[ファイル](../../../analysis-services/scripting/objects/file-element-assl.md)([ファイル](../../../analysis-services/scripting/collections/files-element-assl.md)のコレクション[ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Database 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Assemblies 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/assemblies-element-assl.md)   
 [Assembly 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [DataBlock データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [ComAssembly データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/comassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
