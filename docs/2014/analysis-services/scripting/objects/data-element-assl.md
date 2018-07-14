---
title: データ要素 (ASSL) |Microsoft Docs
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
- Data Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Data
helpviewer_keywords:
- Data element
ms.assetid: e52b1961-7e11-4029-8ab1-84d275845067
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b31922593446e7d8aafd88cdb5667bef8b109ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218282"
---
# <a name="data-element-assl"></a>Data 要素 (ASSL)
  含まれています (子のコレクションで[ブロック要素&#40;ASSL&#41; ](block-element-assl.md)要素) のバイナリ コンテンツを[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<File xsi:type="ClrAssemblyFile">  
   ...  
   <Data xsi:type="DataBlock">...</Data>  
   ...  
</ClrAssemblyFile>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataBlock](../data-type/datablock-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ファイル](file-element-assl.md)型の[ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Data`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Assembly 要素&#40;ASSL&#41;](assembly-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [要素をファイル&#40;ASSL&#41;](../collections/files-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../collections/blocks-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
