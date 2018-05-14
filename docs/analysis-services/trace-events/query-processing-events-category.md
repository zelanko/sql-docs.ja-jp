---
title: クエリ処理イベントのカテゴリ |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77ee9a6a5533145809fe1f8a1bbf32e72cbcad3e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="query-processing-events-category"></a>クエリ処理イベント カテゴリ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  クエリ処理イベント カテゴリには、次の表に示したイベント クラスがあります。  
  
|**Event Class**|**イベント ID**|**Description**|  
|---------------------|------------------|---------------------|  
|Query Subcube|11|使用法に基づく最適化用のサブキューブのクエリ。|  
|Query Subcube Verbose|12|詳細情報を指定してサブキューブをクエリします。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|Get Data From Aggregation|60|集計からデータを取得することによってクエリに応答します。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|Get Data From Cache|61|キャッシュの 1 つからデータを取得することによってクエリに応答します。 このイベントを有効にすると、パフォーマンスが低下する場合があります。|  
|Query Cube Begin|70|トレースが開始されてからのすべての Query Cube Begin イベントを収集します。|  
|Query Cube End|71|トレースが開始されてからのすべての Query Cube End イベントを収集します。|  
|Calculate Non Empty Begin|72|空以外の計算の開始。|  
|Calculate Non Empty Current|73|空以外の計算の現在の状態。|  
|Calculate Non Empty End|74|空以外の計算の終了。|  
|Serialize Results Begin|75|結果のシリアル化の開始。|  
|Serialize Results Current|76|結果のシリアル化の現在の状態。|  
|Serialize Results End|77|結果のシリアル化の終了。|  
|Execute MDX Script Begin|78|MDX スクリプトの実行の開始。|  
|Execute MDX Script Current|79|MDX スクリプトの実行の現在の状態。|  
|Execute MDX Script End|80|MDX スクリプトの実行の終了。|  
|Query Dimension|81|クエリ ディメンション。|  
|VertiPaq SE Query Begin|82|VertiPaq SE クエリ。|  
|VertiPaq SE Query End|83|VertiPaq SE クエリ。|  
  
 クエリ処理イベントの各イベント クラスに関連する列については、「 [Query Processing Events Data Columns](../../analysis-services/trace-events/query-processing-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services トレース イベント](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
