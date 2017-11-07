---
title: "ブロック要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Blocks Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4ce7b7d5d062ec09eb0e098ec3c9a9624a9e518
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="blocks-element-assl"></a>Blocks 要素 (ASSL)
  ブロックのバイナリの内容を表すバイナリ データのコレクションを格納、 [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Data xsi:type="DataBlock">  
   ...  
   <Blocks>  
      <Block>...</Block>  
   </Blocks>  
   ...  
</File>  
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
|親要素|[データ](../../../analysis-services/scripting/objects/data-element-assl.md)型の[DataBlock](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)|  
|子要素|[ブロック](../../../analysis-services/scripting/objects/block-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ブロック**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Assembly 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [ClrAssembly データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Files 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [File 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [ClrAssemblyFile データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [データ要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

