---
title: TableID 要素 (ASSL) |Microsoft ドキュメント
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
- TableID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TableID
helpviewer_keywords:
- TableID element
ms.assetid: 45fe7e23-b274-4bc2-be63-1a5bb6680f51
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9b8f85ee3fecac1b098a16afe6cf2d0eca61226b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179196"
---
# <a name="tableid-element-assl"></a>TableID 要素 (ASSL)
  テーブルの識別子 (ID) が含まれています (から、 [DataSourceView](../objects/datasourceview-element-assl.md)要素)、親要素に関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ColumnBinding> <!-- or DSVTableBinding, RowBinding, IncrementalProcessingNotification -->  
   ...  
   <TableID>...</TableID>  
   ...  
</ColumnBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ColumnBinding](../data-type/binding-data-type-assl.md)、 [DSVTableBinding](../data-type/tablebinding-data-type-assl.md)、 [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)、 [RowBinding](../data-type/rowbinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `TableID` によって識別されるテーブルは、所有するオブジェクト (ディメンションまたはキューブ) のバインド先のデータ ソースに含まれている必要があります。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `TableID` の親に対応する要素は、<xref:Microsoft.AnalysisServices.ColumnBinding>、<xref:Microsoft.AnalysisServices.DSVTableBinding>、<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>、および <xref:Microsoft.AnalysisServices.RowBinding> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  