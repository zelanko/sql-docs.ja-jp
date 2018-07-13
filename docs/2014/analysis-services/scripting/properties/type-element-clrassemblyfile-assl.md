---
title: Type 要素 (ClrAssemblyFile) (ASSL) |Microsoft Docs
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
- Type Element (ClrAssemblyFile)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ab9e1e2c-ab06-4cd1-b007-16d738dc5604
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02a32dffab7d0274b98a5dcae3099703446b184b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218022"
---
# <a name="type-element-clrassemblyfile-assl"></a>Type 要素 (ClrAssemblyFile) (ASSL)
  属しているファイルの 1 つのファイルの種類を指定します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリ。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ClrAssemblyFile>  
      ...  
      <Type>...</Type>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*Main*|アセンブリのメイン ファイルであるファイルを指定します。|  
|*依存します。*|アセンブリの依存ファイルであるファイルを指定します。|  
|*デバッグ*|デバック情報を含んでいるファイルを指定します。|  
  
 許容された値に対応する列挙体`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFileType>します。  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [要素が&#40;ASSL&#41;](../objects/file-element-assl.md)   
 [要素をファイル&#40;ASSL&#41;](../collections/files-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [Assembly 要素&#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [Assemblies 要素&#40;ASSL&#41;](../collections/assemblies-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
