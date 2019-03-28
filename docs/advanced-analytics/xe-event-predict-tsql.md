---
title: PREDICT ステートメント - SQL Server Machine Learning サービスを監視するための拡張イベント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fa0d9d4ed647a6616c525533e696960784d09290
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510539"
---
# <a name="extended-events-for-monitoring-predict-statements"></a>PREDICT ステートメントを監視するための拡張イベント

この記事では、SQL Server の監視し、分析に使用できるジョブで使用する指定された、拡張イベントをについて説明します[PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) SQL Server でのリアルタイム スコアリングを実行します。

リアルタイム スコアリングは、machine learning の SQL Server に格納されているモデルからスコアを生成します。 PREDICT 関数では、R や Python など、特定のバイナリ形式を使用して作成されたモデルのみなどに外部実行時は必要ありません。 詳細については、次を参照してください。[リアルタイム スコアリング](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring)します。

## <a name="prerequisites"></a>前提条件

拡張のイベント (XEvents とも呼ばれます) とのセッションでイベントを追跡する方法については、次の記事を参照してください。

+ [拡張イベントの概念とアーキテクチャ](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [SSMS でのイベント キャプチャを設定します。](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [オブジェクト エクスプ ローラーで、イベント セッションを管理します。](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>拡張イベントの表

次の拡張イベントがサポートする SQL Server のすべてのバージョンで使用可能な[T-SQL 予測](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)ステートメントでは、Linux、および Azure SQL Database での SQL Server を含むです。 

予測の T-SQL ステートメントは、SQL Server 2017 で導入されました。 

|NAME |object_type|description| 
|----|----|----|
|predict_function_completed |イベント  |組み込み実行時間の内訳|
|predict_model_cache_hit |イベント|モデルが PREDICT 関数モデル キャッシュから取得されるときに発生します。 その他の predict_model_cache _ * イベントと共に、このイベントを使用すると、PREDICT 関数モデル キャッシュが原因の問題をトラブルシューティングできます。|
|predict_model_cache_insert |イベント  |   モデルが PREDICT 関数モデル キャッシュに挿入するときに発生します。 その他の predict_model_cache _ * イベントと共に、このイベントを使用すると、PREDICT 関数モデル キャッシュが原因の問題をトラブルシューティングできます。    |
|predict_model_cache_miss   |イベント|モデルが PREDICT 関数モデル キャッシュで見つからなかった場合に発生します。 このイベントの発生を頻繁に SQL Server がより多くのメモリを必要がある可能性があります。 その他の predict_model_cache _ * イベントと共に、このイベントを使用すると、PREDICT 関数モデル キャッシュが原因の問題をトラブルシューティングできます。|
|predict_model_cache_remove |イベント| モデルが PREDICT 関数モデル キャッシュから削除されたときに発生します。 その他の predict_model_cache _ * イベントと共に、このイベントを使用すると、PREDICT 関数モデル キャッシュが原因の問題をトラブルシューティングできます。|

## <a name="query-for-related-events"></a>関連するイベントのクエリ

これらのイベントに対して返されるすべての列の一覧を表示するには、SQL Server Management Studio で、次のクエリを実行します。

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>使用例

PREDICT を使用して、スコア付けのセッションのパフォーマンスに関する情報をキャプチャするには。

1. 拡張イベント セッションを Management Studio またはサポートされている別の使用を新規作成[ツール](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)します。
2. イベント追加`predict_function_completed`と`predict_model_cache_hit`セッションにします。
3. 拡張イベント セッションを開始します。
4. PREDICT を使用するクエリを実行します。

結果で、これらの列を確認します。

+ 値は、`predict_function_completed`示していますが、モデルの読み込みとスコア付けに費やされたクエリをどの程度時間します。
+ ブール値`predict_model_cache_hit`かどうか、クエリがキャッシュされたモデルを使用するかどうかを示します。 

### <a name="native-scoring-model-cache"></a>ネイティブ スコアリング モデルのキャッシュ

予測するのに特定のイベントだけでなく、キャッシュされたモデルとキャッシュの使用状況の詳細を取得するのに次のクエリを使用できます。

ネイティブのスコア付けモデルのキャッシュを参照してください。

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

モデル キャッシュでオブジェクトを表示します。

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

