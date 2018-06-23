---
title: ProcessingQuery 要素 (ASSL) |Microsoft ドキュメント
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
- ProcessingQuery Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProcessingQuery element
ms.assetid: d18e6f4b-c24c-4f73-8b85-4b6e8a82a695
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4ade6950de95029d3eea4105bd34f636fd3632a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076916"
---
# <a name="processingquery-element-assl"></a>ProcessingQuery 要素 (ASSL)
  増分処理ステータスの通知のために実行するクエリのパラメーター化されたテキストを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<IncrementalProcessingNotification>  
   ...  
   <ProcessingQuery>...</ProcessingQuery>  
   ...  
</IncrementalProcessingNotification>  
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
|親要素|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 内のテーブル、 [DataSourceView](../objects/datasourceview-element-assl.md)によって参照される、 `ProcessingQuery` 、兄弟要素によって識別される[TableID](id-element-assl.md)です。  
  
 親に対応する要素`ProcessingQuery`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  