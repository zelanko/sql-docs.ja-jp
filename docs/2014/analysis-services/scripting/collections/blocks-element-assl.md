---
title: ブロック要素 (ASSL) |Microsoft ドキュメント
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
- Blocks Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Blocks
helpviewer_keywords:
- Blocks element
ms.assetid: d6fd4e6b-b5bd-43cd-9c28-48af57cf977c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bf944cc053e7a8c32efec50d10f6cc176942cce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076309"
---
# <a name="blocks-element-assl"></a>Blocks 要素 (ASSL)
  ブロックのバイナリの内容を表すバイナリ データのコレクションを格納、 [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md)要素。  
  
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
|親要素|[データ](../objects/data-element-assl.md)型の[DataBlock](../data-type/datablock-data-type-assl.md)|  
|子要素|[ブロック](../objects/block-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`Blocks`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ClrAssemblyFile>します。  
  
## <a name="see-also"></a>参照  
 [Assembly 要素&#40;ASSL&#41;](../objects/assembly-element-assl.md)   
 [ClrAssembly データ型&#40;ASSL&#41;](../data-type/assembly-data-type-assl.md)   
 [要素をファイル&#40;ASSL&#41;](files-element-assl.md)   
 [要素が&#40;ASSL&#41;](../objects/file-element-assl.md)   
 [ClrAssemblyFile データ型&#40;ASSL&#41;](../data-type/clrassemblyfile-data-type-assl.md)   
 [データ要素&#40;ASSL&#41;](../objects/data-element-assl.md)   
 [DataBlock データ型&#40;ASSL&#41;](../data-type/datablock-data-type-assl.md)   
 [Blocks 要素](blocks-element-assl.md)   
 [要素のブロック&#40;ASSL&#41;](../objects/block-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  