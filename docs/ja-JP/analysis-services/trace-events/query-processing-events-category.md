---
title: クエリ処理イベントのカテゴリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a94b3198-be85-4935-845d-1cd4e121fc94
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 433a7260b538622c118e67411807538c6b4391d3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
  
