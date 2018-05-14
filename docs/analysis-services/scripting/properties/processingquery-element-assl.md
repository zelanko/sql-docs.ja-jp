---
title: ProcessingQuery 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ff294d15e56f23721cd87f1934298e9fea756328
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="processingquery-element-assl"></a>ProcessingQuery 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[IncrementalProcessingNotification](../../../analysis-services/scripting/objects/incrementalprocessingnotification-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 内のテーブル、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)によって参照される、 **ProcessingQuery** 、兄弟要素によって識別される[TableID](../../../analysis-services/scripting/properties/tableid-element-assl.md)です。  
  
 親に対応する要素**ProcessingQuery**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
