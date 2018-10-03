---
title: クエリ処理イベント カテゴリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a94b3198-be85-4935-845d-1cd4e121fc94
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c35f747d93bb36a767d2d9534cc285950114e25c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48174402"
---
# <a name="query-processing-events-category"></a>クエリ処理イベント カテゴリ
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
  
 クエリ処理イベントの各イベント クラスに関連する列については、「 [Query Processing Events Data Columns](query-processing-events-data-columns.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services トレース イベント](analysis-services-trace-events.md)  
  
  
