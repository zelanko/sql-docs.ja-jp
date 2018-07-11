---
title: ClrAssemblyFile データ型 (ASSL) |Microsoft Docs
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
- ClrAssemblyFile Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ClrAssemblyFile
helpviewer_keywords:
- ClrAssemblyFile data type
ms.assetid: 91074677-c149-483b-a56d-0e35d959d9eb
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ebfcf0080184294cbbda05e671776972be18f9a1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277869"
---
# <a name="clrassemblyfile-data-type-assl"></a>ClrAssemblyFile データ型 (ASSL)
  構成するファイルの 1 つを表すプリミティブ データ型を定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] `Assembly` ([ClrAssembly](assembly-data-type-assl.md)要素)。  
  
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
|子要素|[データ](../objects/data-element-assl.md)、[名前](../properties/name-element-assl.md)、[型](../properties/type-element-clrassemblyfile-assl.md)|  
|派生要素|[ファイル](../objects/file-element-assl.md)([ファイル](../collections/files-element-assl.md)のコレクション[ClrAssembly](assembly-data-type-assl.md))|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素&#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Database 要素&#40;ASSL&#41;](../objects/database-element-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [Assembly 要素&#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [DataBlock データ型&#40;ASSL&#41;](datablock-data-type-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../objects/block-element-assl.md)   
 [ComAssembly データ型&#40;ASSL&#41;](comassembly-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
