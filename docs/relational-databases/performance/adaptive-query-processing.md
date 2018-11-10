---
title: Microsoft SQL データベースでのアダプティブ クエリの処理 | Microsoft Docs | Microsoft Docs
description: SQL Server (2017 以降) および Azure SQL Database のクエリ パフォーマンスを向上させるためのアダプティブ クエリ処理の機能です。
ms.custom: ''
ms.date: 10/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 60f02a303e6e085dc14a165ec51e316a2bc88f8e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51031199"
---
# <a name="adaptive-query-processing-in-sql-databases"></a>Microsoft SQL データベースでのアダプティブ クエリの処理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

この記事では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] 以降) および [!INCLUDE[ssSDS](../../includes/sssds-md.md)] でクエリのパフォーマンスを向上するために使用できるアダプティブ クエリ処理の機能について説明します。
- バッチ モード メモリ許可フィードバック。
- バッチ モード アダプティブ結合。
- インターリーブ実行。 

一般的なレベルでは、SQL Server はクエリを次のように実行します。
1. クエリ最適化プロセスが、特定のクエリに対して可能な一連の実行プランを生成します。 この間に、プランのオプションのコストが推定されて、最低推定コストのプランが使われます。
1. クエリ実行プロセスが、クエリ オプティマイザーによって選ばれたプランを取得し、それを使って実行します。
    
さまざまな理由で、クエリ オプティマイザーによって選ばれたプランが最適ではない場合があります。 たとえば、クエリ プランを通過する推定行数が正しくない可能性があります。 推定コストは、実行で使われるプランの決定に利用されます。 カーディナリティの推定が正しくない場合、当初の想定が悪くても元のプランが使われます。

![アダプティブ クエリ処理の機能](./media/1_AQPFeatures.png)

### <a name="how-to-enable-adaptive-query-processing"></a>アダプティブ クエリ処理を有効にする方法
データベースに対して互換性レベル 140 を有効にすることにより、自動的にワークロードをアダプティブ クエリ処理の対象にすることができます。  これは Transact-SQL を使って設定できます。 例 :  

```sql
ALTER DATABASE [WideWorldImportersDW] SET COMPATIBILITY_LEVEL = 140;
```

## <a name="batch-mode-memory-grant-feedback"></a>バッチ モード メモリ許可フィードバック
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのクエリの実行後プランには、実行に最低限必要なメモリと、すべての行をメモリに収めるのに最適なメモリ許可サイズが含まれます。 メモリ許可サイズが正しくない場合、パフォーマンスが低下します。 メモリ許可が多すぎると、メモリが無駄になり、コンカレンシーが制限されます。 メモリ許可が少なすぎると、負荷の高いディスクへの書き込みが発生する原因になります。 繰り返されるワークロードを処理することにより、バッチ モード メモリ許可フィードバックはクエリに実際に必要なメモリ量を再計算し、キャッシュされたプランの許可値を更新します。  同じクエリ ステートメントを実行するとき、クエリは、修正されたメモリ許可サイズを使うことで、コンカレンシーに影響を与える過剰なメモリ許可を減らし、負荷の高いディスクへの書き込みが発生する過少なメモリ許可を修正します。
次のグラフでは、バッチ モード アダプティブ メモリ許可フィードバックを使用する 1 つの例を示します。 最初のクエリ実行の場合、ディスクへの書き込みが多いため所要時間は  **88 秒**  でした。   

```sql
DECLARE @EndTime datetime = '2016-09-22 00:00:00.000';
DECLARE @StartTime datetime = '2016-09-15 00:00:00.000';
SELECT TOP 10 hash_unique_bigint_id
FROM dbo.TelemetryDS
WHERE Timestamp BETWEEN @StartTime and @EndTime
GROUP BY hash_unique_bigint_id
ORDER BY MAX(max_elapsed_time_microsec) DESC;
```

![ディスクへの書き込みが多い](./media/2_AQPGraphHighSpills.png)

メモリ許可フィードバックを有効にした 2 番目の実行では、所要時間は  **1 秒**  で (88 秒から短縮)、ディスクへの書き込みはまったくなくなり、許可は高くなっています。 

![ディスクへの書き込みがない](./media/3_AQPGraphNoSpills.png)

### <a name="memory-grant-feedback-sizing"></a>メモリ許可フィードバックのサイズ決定
メモリ許可条件が過剰な場合、許可されるメモリが実際に使われるメモリ サイズの 2 倍より多いと、メモリ許可フィードバックはメモリ許可を再計算して、キャッシュされるプランを更新します。 メモリ許可が 1 MB 未満のプランについては、超過分の再計算は行われません。
メモリ許可条件が過少な場合、バッチ モード演算子でディスクへの書き込みが発生すると、メモリ許可フィードバックはメモリ許可の再計算をトリガーします。 ディスク書き込みイベントがメモリ許可フィードバックに報告され、*spilling_report_to_memory_grant_feedback* xEvent で表示できます。 このイベントは、プランのノード ID と、そのノードでディスクに書き込まれたデータのサイズを返します。

### <a name="memory-grant-feedback-and-parameter-sensitive-scenarios"></a>メモリ許可フィードバックとパラメーター依存シナリオ
最適化のためには、クエリ プランによってパラメーター値を変えることが必要な場合もあります。 この種のクエリは "パラメーター依存" と定義されます。 パラメーター依存プランでは、メモリ要件が不安定な場合、メモリ許可フィードバック自体がクエリで無効になります。 クエリが数回繰り返し実行された後でプランは無効になり、このことは *memory_grant_feedback_loop_disabled* xEvent で監視できます。 パラメーター スニッフィングとパラメーターの感度の詳細については、「[Query Processing Architecture Guide](../../relational-databases/query-processing-architecture-guide.md#ParamSniffing)」(クエリ処理アーキテクチャ ガイド) を参照してください。

### <a name="memory-grant-feedback-caching"></a>メモリ許可フィードバックのキャッシュ
フィードバックは、1 回の実行に対してキャッシュされるプランに格納できます。 ただし、メモリ許可フィードバックの調整によってメリットがあるのは、そのステートメントを連続して実行する場合です。 この機能は、ステートメントの反復実行に適用されます。 メモリ許可フィードバックが変更するのはキャッシュされたプランのみです。 現在、変更はクエリ ストアではキャプチャされません。
プランがキャッシュから削除された場合、フィードバックは保持されません。 フェールオーバーが発生した場合もフィードバックは失われます。 `OPTION (RECOMPILE)` を使うステートメントでは、新しいプランが作成されますが、プランはキャッシュされません。 キャッシュされないため、メモリ許可フィードバックは生成されず、そのコンパイルおよび実行に対して格納されません。  ただし、 **を "** 使わない`OPTION (RECOMPILE)`" 同等のステートメント (つまり、クエリ ハッシュが同じ) がキャッシュされて再実行された場合、連続するステートメントでメモリ許可フィードバックのメリットがある場合があります。

### <a name="tracking-memory-grant-feedback-activity"></a>メモリ許可フィードバック アクティビティの追跡
*memory_grant_updated_by_feedback* xEvent を使って、メモリ許可フィードバック イベントを追跡することができます。 このイベントは、現在の実行カウント履歴、メモリ許可フィードバックによってプランが更新された回数、変更前の最適な追加メモリ許可、およびメモリ許可フィードバックによってキャッシュされたプランが変更された後の最適な追加メモリ許可を追跡します。

### <a name="memory-grant-feedback-resource-governor-and-query-hints"></a>メモリ許可フィードバック、リソース ガバナー、クエリ ヒント
実際に許可されるメモリは、リソース ガバナーまたはクエリ ヒントによって決定されるクエリ メモリ制限に従います。

### <a name="disabling-batch-mode-memory-grant-feedback-without-changing-the-compatibility-level"></a>互換性レベルを変更せず、バッチ モード メモリ許可フィードバックを無効にする
メモリ許可フィードバックは、データベースの互換性レベル 140 以上を維持しながら、データベースまたはステートメント範囲で無効にできます。 データベースを発生源とするすべてのクエリ実行に対してバッチ モード メモリ許可フィードバックを無効にするには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK = ON;
```

有効になっているとき、この設定は sys.database_scoped_configurations で有効として表示されます。

データベースを発生源とするすべてのクエリ実行に対してバッチ モード メモリ許可フィードバックを再有効化するには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK = OFF;
```

DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK を USE HINT クエリ ヒントとして指定することで、特定のクエリのバッチ モード メモリ許可フィードバックを無効にすることもできます。  例 :

```sql
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (USE HINT ('DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK')); 
```

USE HINT クエリ ヒントは、データベース スコープ構成またはトレース フラグ設定に優先します。

## <a name="row-mode-memory-grant-feedback"></a>行モード メモリ許可フィードバック
**適用対象:** SQL Database (パブリック プレビューの機能)

> [!NOTE]
> 行モード メモリ許可フィードバックはパブリック プレビューの機能です。  

行モード メモリ許可フィードバックは、バッチ モードと行モード両方の演算子のメモリ許可サイズを調整することで、バッチ モード メモリ許可フィードバックの機能を拡張します。  

Azure SQL Database で行モード メモリ許可フィードバックのパブリック プレビューを有効にするには、クエリを実行する際に接続されるデータベースのデータベース互換レベル 150 を有効にします。

行モード メモリ許可フィードバックのアクティビティは、**memory_grant_updated_by_feedback** XEvent を通じて確認できます。 

行モード メモリ許可フィードバック以降では、実際の実行後プランのために 2 つの新しいクエリ プラン属性 (**IsMemoryGrantFeedbackAdjusted** および **LastRequestedMemory**) が表示されます。これらは MemoryGrantInfo クエリ プランの XML 要素に追加されます。 

LastRequestedMemory では、前のクエリの実行から許可されたメモリがキロバイト (KB) で表示されます。 IsMemoryGrantFeedbackAdjusted 属性を使用すると、実際のクエリ実行プラン内のステートメントに対するメモリ許可フィードバックの状態を確認できます。 この属性に表示される値は次のとおりです。

| IsMemoryGrantFeedbackAdjusted の値 | [説明] |
|--- |--- |
| No: First Execution | メモリ許可フィードバックは、最初のコンパイルとそれに関連付けられた実行ではメモリを調整しません。  |
| No: Accurate Grant | ディスクへの書き込みが存在せず、許可されたメモリの少なくとも 50% がステートメントによって使用されている場合、メモリ許可フィードバックはトリガーされません。 |
| No: Feedback disabled | メモリ許可フィードバックが継続的にトリガーされ、メモリを増加させる操作と減少させる操作の間で変動している場合、ステートメントのメモリ許可フィードバックは無効にされます。 |
| Yes: Adjusting | メモリ許可フィードバックが適用されています。また、次の実行に向けてさらに調整される可能性があります。 |
| Yes: Stable | メモリ許可フィードバックが適用されています。また、許可されたメモリが安定しています (つまり、前回の実行で許可されたメモリと今回の実行で許可されたメモリが同じです)。 |

> [!NOTE]
> パブリック プレビューの行モード メモリ許可フィードバック プランの属性は、バージョン 17.9 以降の SQL Server Management Studio のグラフィカルなクエリ実行プランで表示されます。 

### <a name="disabling-row-mode-memory-grant-feedback-without-changing-the-compatibility-level"></a>互換性レベルを変更せず、行モード メモリ許可フィードバックを無効にする
行モード メモリ許可フィードバックは、データベースの互換性レベル 150 以上を維持しながら、データベースまたはステートメント範囲で無効にできます。 データベースを発生源とするすべてのクエリ実行に対して行モード メモリ許可フィードバックを無効にするには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ROW_MODE_MEMORY_GRANT_FEEDBACK = OFF;
```

データベースを発生源とするすべてのクエリ実行に対して行モード メモリ許可フィードバックを再び有効にするには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET ROW_MODE_MEMORY_GRANT_FEEDBACK = ON;
```

DISABLE_ROW_MODE_MEMORY_GRANT_FEEDBACK を USE HINT クエリ ヒントとして指定することで、特定のクエリの行モード メモリ許可フィードバックを無効にすることもできます。  例 :

```sql
SELECT * FROM Person.Address  
WHERE City = 'SEATTLE' AND PostalCode = 98104
OPTION (USE HINT ('DISABLE_ROW_MODE_MEMORY_GRANT_FEEDBACK')); 
```

USE HINT クエリ ヒントは、データベース スコープ構成またはトレース フラグ設定に優先します。


## <a name="batch-mode-adaptive-joins"></a>バッチ モード アダプティブ結合
バッチ モード アダプティブ結合機能を使うと、最初の入力のスキャンが "**終わる**" まで、[ハッシュ結合方法または入れ子になったループ結合](../../relational-databases/performance/joins.md)方法のどちらを選ぶかを、遅延することができます。 アダプティブ結合演算子は、入れ子になったループ プランに切り替えるタイミングを決定するために使われるしきい値を定義します。 したがって、実行中により適切な結合方法に動的に切り替えることができます。
しくみは次のとおりです。
-  ビルド結合入力の行数が十分に小さくて、入れ子になったループ結合の方がハッシュ結合より適している場合、プランは入れ子になったループ アルゴリズムに切り替わります。
-  ビルド結合入力が特定の行数しきい値を超えている場合、切り替えは行われず、プランはハッシュ結合を使い続けます。

アダプティブ結合の例として次のようなクエリを考えます。

```sql
SELECT  [fo].[Order Key], [si].[Lead Time Days],
[fo].[Quantity]
FROM [Fact].[Order] AS [fo]
INNER JOIN [Dimension].[Stock Item] AS [si]
       ON [fo].[Stock Item Key] = [si].[Stock Item Key]
WHERE [fo].[Quantity] = 360;
```

このクエリは 336 行を返します。 [ライブ クエリ統計](../../relational-databases/performance/live-query-statistics.MD)を有効にすると次のようなプランが表示されます。

![クエリ結果 336 行](./media/4_AQPStats336Rows.png)

このプランでは次のことがわかります。
1. ハッシュ結合ビルド フェーズの行を提供するために、列ストア インデックス スキャンが使われています。
1. 新しいアダプティブ結合演算子があります。 この演算子は、入れ子になったループ プランに切り替えるタイミングを決定するために使われるしきい値を定義します。 この例では、しきい値は 78 行です。 &gt;= 78 行になると、ハッシュ結合が使われます。 しきい値より小さい場合は、入れ子になったループ結合が使われます。
1. この場合は 336 行を返すため、しきい値を超えており、2 番目の分岐は標準的なハッシュ結合操作のプローブ フェーズを表します。 ライブ クエリ統計は演算子を通過する行数を示すことに注意してください (この場合は "672 of 672")。
1. 最後の分岐は入れ子になったループ結合で使うためのクラスター化インデックス シークで、しきい値は超えていません。 "0 of 336" 行と表示されます (分岐は使われません)。
 次は、クエリは同じですがテーブルの *Quantity* 値が 1 行だけのプランと比較してみましょう。
 
```sql
SELECT  [fo].[Order Key], [si].[Lead Time Days],
[fo].[Quantity]
FROM [Fact].[Order] AS [fo]
INNER JOIN [Dimension].[Stock Item] AS [si]
       ON [fo].[Stock Item Key] = [si].[Stock Item Key]
WHERE [fo].[Quantity] = 361;
```
クエリでは 1 行が返されます。 ライブ クエリ統計を有効にすると次のようなプランが表示されます。

![クエリ結果 1 行](./media/5_AQPStatsOneRow.png)

このプランでは次のことがわかります。
- 返されるのが 1 行なので、クラスター化インデックス シークを行が通過します。
- また、ハッシュ結合ビルド フェーズは続行しなかったので、2 番目の分岐を通る行はありません。

### <a name="adaptive-join-benefits"></a>アダプティブ結合の利点
大小の結合入力スキャンが頻繁に切り替わるワークロードの場合、この機能から最もメリットがあります。

### <a name="adaptive-join-overhead"></a>アダプティブ結合のオーバーヘッド
アダプティブ結合では、同等のインデックスが入れ子になったループ結合プランより多くのメモリが必要です。 追加のメモリは、入れ子になったループがハッシュ結合であるかのように要求されます。 ストップ アンド ゴー操作と、同等の入れ子になったループ ストリーミング結合の違いのため、ビルド フェーズにもオーバーヘッドがあります。 その追加コストにより、ビルド入力で行数が変動するシナリオに対して柔軟性があります。

### <a name="adaptive-join-caching-and-re-use"></a>アダプティブ結合のキャッシュと再利用
バッチ モード アダプティブ結合は、ステートメントの最初の実行に対して作用し、コンパイル後は、コンパイルされたアダプティブ結合しきい値と、外部入力のビルド フェーズを通過するランタイム行に基づいて、連続する実行がアダプティブのままになります。

### <a name="tracking-adaptive-join-activity"></a>アダプティブ結合アクティビティの追跡
アダプティブ結合演算子には次のプラン演算子属性があります。

| プラン属性 | [説明] |
|--- |--- |
| AdaptiveThresholdRows | ハッシュ結合から入れ子になったループ結合への切り替えに使われるしきい値を示します。 |
| EstimatedJoinType | 予想される結合の種類を示します。 |
| ActualJoinType | 実際のプランで、しきい値に基づいて最終的に選ばれた結合アルゴリズムを示します。 |

予想されるプランは、アダプティブ結合プランの概要と、定義されているアダプティブ結合しきい値および予想される結合の種類を示します。

### <a name="adaptive-join-and-query-store-interoperability"></a>アダプティブ結合とクエリ ストアの相互運用性
クエリ ストアは、バッチ モード アダプティブ結合プランをキャプチャし、強制できます。

### <a name="adaptive-join-eligible-statements"></a>アダプティブ結合を使えるステートメント
論理結合をバッチ モード アダプティブ結合で使うにはいくつかの条件があります。
- データベースの互換性レベルが 140 である。
- クエリが SELECT ステートメントである (現在、データ変更ステートメントは使えません)。
- 結合が、インデックス付きの入れ子になったループ結合またはハッシュ結合の両方の物理アルゴリズムで実行できる。
- クエリ全体に列ストア インデックスが存在することにより、または列ストア インデックス テーブルを結合で直接参照することにより、ハッシュ結合がバッチ モードを使っている。
- 入れ子になったループ結合とハッシュ結合の生成された代替ソリューションが、同じ最初の子 (外部参照) を持っている。

### <a name="adaptive-joins-and-nested-loop-efficiency"></a>アダプティブ結合と入れ子になったループの効率
アダプティブ結合は、入れ子になったループ操作に切り替えた場合、ハッシュ結合ビルドによって既に読み取られた行を使います。 演算子が外部参照行をもう一度読み込むことは "**ありません**"。

### <a name="adaptive-threshold-rows"></a>アダプティブしきい値行
次のグラフは、ハッシュ結合のコストと入れ子になったループ結合のコストの交点の例を示します。  この交点で、しきい値が決定され、それによって結合操作に実際に使われるアルゴリズムが決まります。

![結合しきい値](./media/6_AQPJoinThreshold.png)

### <a name="disabling-adaptive-joins-without-changing-the-compatibility-level"></a>互換性レベルを変更せず、適応型結合を無効にする

適応型結合は、データベースの互換性レベル 140 以上を維持しながら、データベースまたはステートメント範囲で無効にできます。  
データベースを発生源とするすべてのクエリ実行に対して適応型結合を無効にするには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_ADAPTIVE_JOINS = ON;
```

有効になっているとき、この設定は sys.database_scoped_configurations で有効として表示されます。
データベースを発生源とするすべてのクエリ実行に対して適応型結合を再有効化するには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_BATCH_MODE_ADAPTIVE_JOINS = OFF;
```

USE HINT クエリ ヒントとして DISABLE_BATCH_MODE_ADAPTIVE_JOINS を指定することで、特定のクエリで適応型結合を無効にすることもできます。  例 :

```sql
SELECT s.CustomerID,
       s.CustomerName,
       sc.CustomerCategoryName
FROM Sales.Customers AS s
LEFT OUTER JOIN Sales.CustomerCategories AS sc
ON s.CustomerCategoryID = sc.CustomerCategoryID
OPTION (USE HINT('DISABLE_BATCH_MODE_ADAPTIVE_JOINS')); 
```

USE HINT クエリ ヒントは、データベース スコープ構成またはトレース フラグ設定に優先します。

## <a name="interleaved-execution-for-multi-statement-table-valued-functions"></a>複数ステートメントのテーブル値関数のインターリーブ実行
インターリーブ実行は、単一クエリ実行の最適化フェーズと実行フェーズの間の一方向境界を変更し、修正されたカーディナリティ推定に基づいてプランが適応できるようにします。 最適化中に、インターリーブ実行の候補を検出した場合 (現在は**複数ステートメント テーブル値関数 (MSTVF)**)、最適化を一時停止し、該当するサブツリーを実行し、正確なカーディナリティの推定をキャプチャし、ダウンストリームの演算に対する最適化を再開します。
MSTVF の固定のカーディナリティの推定は、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] および [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] では 100、それより前のバージョンでは 1 です。 インターリーブ実行は、複数ステートメント テーブル値関数に関するこれらの固定カーディナリティ推定によるワークロードのパフォーマンスの問題に役立ちます。

次の図では、MSTVF からの固定カーディナリティ推定の影響を示す全体実行プランのサブセットであるライブ クエリ統計出力を示します。 実際の行フローと推定行数を比較できます プランの 3 つの注目すべき領域があります (フローは右から左)。
1. MSTVF テーブル スキャンの推定行数は 100 の固定です。 ただし、この例では、この MSTVF テーブル スキャンを通過したのはライブ クエリ統計が示すように 527,597 であるのに対し、実際の推定は *527597 of 100* であり、固定の推定に大きな非対称があります。
1. Nested Loops 操作では、結合の外側によって返されるものと推定されたのは 100 行だけです。 MSTVF によって実際に返される行数が多いと、そっくり異なる結合アルゴリズムにした方がよくなると思われます。
1. Hash Match 操作では、小さい警告シンボルに注意してください。これはここではディスクへの書き込みを示します。

![行フローと推定行数](./media/7_AQPFlowThreeAreas.png)

前のプランと、インターリーブ実行を有効にして生成された実際のプランを比較します。

![インターリーブ プラン](./media/8_AQPInterleavedEnabledPlan.png)

1. MSTVF テーブル スキャンに正確なカーディナリティ推定が反映されるようになったことに注意してください。 また、このテーブル スキャンと他の操作の順序の変更に注意してください。
1. 結合アルゴリズムに関しては、Nested Loop 操作から Hash Match 操作に切り替えました。これは、多くの行が関係する場合に、より適しています。
1. また、MSTVF テーブル スキャンからフローする実際の行数に基づいて多くのメモリを許可しているので、ディスク書き込み警告は表示されなくなっています。

### <a name="interleaved-execution-eligible-statements"></a>インターリーブ実行に適したステートメント
インターリーブ実行内のステートメントを参照する MSTVF は、現在は読み取り専用でなければならず、データ変更操作の一部であってはなりません。 また、MSTVF は、ランタイム定数を使用していない場合は、インターリーブ実行には適しません。

### <a name="interleaved-execution-benefits"></a>インターリーブ実行の利点
一般に、推定行数と実際の行数の非対称が大きいほど、ダウンストリーム プラン操作の数との組み合わせで、パフォーマンスへの影響が大きくなります。
一般に、インターリーブ実行は次の場合にクエリに対して利点があります。
1. 中間結果セット (この例では MSTVF) で推定行数と実際の行数の非対称が大きい。
1. かつ、全体的なクエリが中間結果のサイズの変化による影響を受けやすい。 これは通常、クエリ プランのそのサブツリーの上に複雑なツリーが存在する場合に発生します。
MSTVF の単純な "SELECT *" では、インターリーブ実行によるメリットはありません。

### <a name="interleaved-execution-overhead"></a>インターリーブ実行のオーバーヘッド
オーバーヘッドは最小限か、ありません。 MSTVF はインターリーブ実行導入前に既に具体化されていましたが、違いは、今では最適化を延期でき、具体化された行セットのカーディナリティの推定を利用できることです。
変更に影響を与える他のプランと同様に、一部のプランでは、サブツリーのカーディナリティがよくなることで、クエリ全体が悪いプランになることがあります。 軽減策は、互換性レベルを元に戻すか、またはクエリ ストアを使ってプランの非機能低下バージョンを強制します。

### <a name="interleaved-execution-and-consecutive-executions"></a>インターリーブ実行と連続実行
インターリーブ実行プランがキャッシュされると、最初の実行の推定を修正されたプランが、インターリーブ実行を再インスタンス化することなく連続する実行に使われます。

### <a name="tracking-interleaved-execution-activity"></a>インターリーブ実行アクティビティの追跡
実際のクエリ実行プランで使用法属性を確認できます。

| 実行プラン属性 | [説明] |
| --- | --- |
| ContainsInterleavedExecutionCandidates | *QueryPlan* ノードに適用します。 *true* の場合、プランにインターリーブ実行候補が含まれることを意味します。 |
| IsInterleavedExecuted | TVF ノードの RelOp 以下にある *RuntimeInformation* 要素の属性。 *true* の場合、操作がインターリーブ実行操作の一部としてマテリアル化されたことを意味します。 |

次の xEvent を使って、インターリーブ実行の発生を追跡することもできます。

| xEvent | [説明] |
| ---- | --- |
| interleaved_exec_status | このイベントは、インターリーブ実行が発生すると発生します。 |
| interleaved_exec_stats_update | このイベントは、インターリーブ実行によって更新されたカーディナリティの推定を記述します。 |
| Interleaved_exec_disabled_reason | このイベントは、インターリーブ実行の候補を含むクエリが実際にはインターリーブ実行されなかったときに発生します。 |

インターリーブ実行が MSTVF カーディナリティ推定を修正できるようにするには、クエリを実行する必要があります。 ただし、`ContainsInterleavedExecutionCandidates` showplan 属性によるインターリーブ実行候補がある場合は、推定実行プランがまだ表示されます。    

### <a name="interleaved-execution-caching"></a>インターリーブ実行のキャッシュ
プランがキャッシュからクリアまたは消去された場合、クエリ実行時に、インターリーブ実行を使う新しいコンパイルが行われます。
`OPTION (RECOMPILE)` を使うステートメントは、インターリーブ実行を使う新しいプランを作成し、それをキャッシュしません。     

### <a name="interleaved-execution-and-query-store-interoperability"></a>インターリーブ実行とクエリ ストアの相互運用性
インターリーブ実行を使うプランは強制的に実行できます。 プランは、最初の実行に基づいてカーディナリティの推定を修正されたバージョンです。    

### <a name="disabling-interleaved-execution-without-changing-the-compatibility-level"></a>互換性レベルを変更せず、インターリーブ実行を無効にする

インターリーブ実行は、データベースの互換性レベル 140 以上を維持しながら、データベースまたはステートメント範囲で無効にできます。  データベースを発生源とするすべてのクエリ実行に対してインターリーブ実行を無効にするには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_INTERLEAVED_EXECUTION_TVF = ON;
```

有効になっているとき、この設定は sys.database_scoped_configurations で有効として表示されます。
データベースを発生源とするすべてのクエリ実行に対してインターリーブ実行を再有効化するには、該当するデータベースとの関連で次を実行します。

```sql
ALTER DATABASE SCOPED CONFIGURATION SET DISABLE_INTERLEAVED_EXECUTION_TVF = OFF;
```

USE HINT クエリ ヒントとして DISABLE_INTERLEAVED_EXECUTION_TVF を指定することで、特定のクエリでインターリーブ実行を無効にすることもできます。  例 :

```sql
SELECT  [fo].[Order Key], [fo].[Quantity], [foo].[OutlierEventQuantity]
FROM    [Fact].[Order] AS [fo]
INNER JOIN [Fact].[WhatIfOutlierEventQuantity]('Mild Recession',
                            '1-01-2013',
                            '10-15-2014') AS [foo] ON [fo].[Order Key] = [foo].[Order Key]
                            AND [fo].[City Key] = [foo].[City Key]
                            AND [fo].[Customer Key] = [foo].[Customer Key]
                            AND [fo].[Stock Item Key] = [foo].[Stock Item Key]
                            AND [fo].[Order Date Key] = [foo].[Order Date Key]
                            AND [fo].[Picked Date Key] = [foo].[Picked Date Key]
                            AND [fo].[Salesperson Key] = [foo].[Salesperson Key]
                            AND [fo].[Picker Key] = [foo].[Picker Key]
OPTION (USE HINT('DISABLE_INTERLEAVED_EXECUTION_TVF'));
```

USE HINT クエリ ヒントは、データベース スコープ構成またはトレース フラグ設定に優先します。

## <a name="see-also"></a>参照
[SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[クエリ処理アーキテクチャ ガイド](../../relational-databases/query-processing-architecture-guide.md)    
[プラン表示の論理操作と物理操作のリファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[結合](../../relational-databases/performance/joins.md)    
[アダプティブ クエリ処理のデモンストレーション](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)          

