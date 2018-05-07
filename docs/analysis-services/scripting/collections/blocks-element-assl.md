---
title: ブロック要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2372c7b95ac16a6151b335908c94d6d37c90e93c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="blocks-element-assl"></a>Blocks 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [Assembly 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/assembly-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [要素をファイル&#40;ASSL&#41;](../../../analysis-services/scripting/collections/files-element-assl.md)   
 [File 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/file-element-assl.md)   
 [ClrAssemblyFile データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md)   
 [データ要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/data-element-assl.md)   
 [DataBlock データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/datablock-data-type-assl.md)   
 [Blocks 要素](../../../analysis-services/scripting/collections/blocks-element-assl.md)   
 [Block 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/block-element-assl.md)   
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
