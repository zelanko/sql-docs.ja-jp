---
title: TableID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7fd2304c4f442102ff8d654bec3be19e34bdd944
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201582"
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
  
  
