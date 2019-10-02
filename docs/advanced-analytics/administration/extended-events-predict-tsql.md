---
title: 拡張イベントを使用した T-sql の予測を監視する
description: 拡張イベントを使用して、SQL Server Machine Learning Services で T-sql ステートメントを予測する方法を監視およびトラブルシューティングする方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 958ac3e24a9deec231e7fd4d5da14477d693f4de
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714306"
---
# <a name="monitor-predict-t-sql-statements-with-extended-events-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services の拡張イベントを使用した T-sql ステートメントの予測を監視します

拡張イベントを使用して、SQL Server Machine Learning Services で T-sql ステートメントを[予測](../../t-sql/queries/predict-transact-sql.md)する方法を監視およびトラブルシューティングする方法について説明します。

## <a name="table-of-extended-events"></a>拡張イベントの表

次の拡張イベントは、 [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) t-sql ステートメントをサポートするすべてのバージョンの SQL Server で使用できます。 

|NAME |object_type|description| 
|----|----|----|
|predict_function_completed |イベント  |組み込みの実行時間の内訳|
|predict_model_cache_hit |イベント|モデルが PREDICT 関数モデルキャッシュから取得されたときに発生します。 このイベントを他の predict_model_cache_ * イベントと共に使用して、PREDICT 関数モデルキャッシュが原因で発生した問題のトラブルシューティングを行います。|
|predict_model_cache_insert |イベント  |   モデルが PREDICT 関数モデルキャッシュに挿入されるときに発生します。 このイベントを他の predict_model_cache_ * イベントと共に使用して、PREDICT 関数モデルキャッシュが原因で発生した問題のトラブルシューティングを行います。    |
|predict_model_cache_miss   |イベント|PREDICT 関数モデルキャッシュでモデルが見つからない場合に発生します。 このイベントが頻繁に発生するのは、SQL Server により多くのメモリが必要であることを示す可能性があります。 このイベントを他の predict_model_cache_ * イベントと共に使用して、PREDICT 関数モデルキャッシュが原因で発生した問題のトラブルシューティングを行います。|
|predict_model_cache_remove |イベント| 予測関数のモデルキャッシュからモデルが削除されたときに発生します。 このイベントを他の predict_model_cache_ * イベントと共に使用して、PREDICT 関数モデルキャッシュが原因で発生した問題のトラブルシューティングを行います。|

## <a name="query-for-related-events"></a>関連イベントのクエリ

これらのイベントに対して返されたすべての列の一覧を表示するには、SQL Server Management Studio で次のクエリを実行します。

```sql
SELECT * 
FROM sys.dm_xe_object_columns 
WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>使用例

PREDICT を使用してスコアリングセッションのパフォーマンスに関する情報を取得するには

1. Management Studio またはサポートされている別の[ツール](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools)を使用して、新しい拡張イベントセッションを作成します。
2. イベント`predict_function_completed` と`predict_model_cache_hit`をセッションに追加します。
3. 拡張イベントセッションを開始します。
4. PREDICT を使用するクエリを実行します。

結果で、次の列を確認します。

+ の`predict_function_completed`値は、クエリがモデルの読み込みとスコア付けに費やした時間を示します。
+ の`predict_model_cache_hit`ブール値は、クエリがキャッシュされたモデルを使用したかどうかを示します。 

### <a name="native-scoring-model-cache"></a>ネイティブスコアリングモデルキャッシュ

予測に固有のイベントに加えて、次のクエリを使用して、キャッシュされたモデルとキャッシュの使用に関する詳細情報を取得できます。

ネイティブスコアリングモデルキャッシュを表示します。

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

モデルキャッシュ内のオブジェクトを表示します。

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

## <a name="next-steps"></a>次の手順

拡張イベント (Xevent とも呼ばれます) の詳細と、セッションのイベントを追跡する方法の詳細については、次の記事を参照してください。

+ [SQL Server Machine Learning Services で拡張イベントを使用して Python および R スクリプトを監視する](extended-events.md)
+ [拡張イベントの概念とアーキテクチャ](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [SSMS でのイベントキャプチャの設定](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [オブジェクトエクスプローラーでのイベントセッションの管理](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)
