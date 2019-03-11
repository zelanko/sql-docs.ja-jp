---
title: Microsoft SQL データベースでのインテリジェントなクエリ処理 | Microsoft Docs
description: SQL Server および Azure SQL Database のクエリ パフォーマンスを向上させるためのインテリジェントなクエリ処理の機能です。
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1b92bc15079fcc85212ea3d1b51be64a3348a4b1
ms.sourcegitcommit: 2663063e29f2868ee6b6d596df4b2af2d22ade6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305370"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>SQL データベースでのインテリジェントなクエリ処理

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

インテリジェントなクエリ処理 (QP) 機能ファミリには、幅広い影響がある機能が含まれています。 最小限の実装作業で既存のワークロードのパフォーマンスが向上します。 この機能ファミリから自動的に恩恵を受ける方法については、該当するデータベース互換性レベルに移動してください。

| **IQP の機能** | **Azure SQL Database でのサポート** | **SQL Server でのサポート** |
| --- | --- | --- |
| [適応型結合 (バッチ モード)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-adaptive-joins) | あり (互換性レベル 140 未満)| あり (SQL Server 2017 以降、互換性レベル 140 未満)|
| [個別の概算数](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#approximate-query-processing) | あり (パブリック プレビュー)| あり (SQL Server 2019 CTP 2.0 以降、パブリック プレビュー)|
| [行ストアでのバッチ モード](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#batch-mode-on-rowstore) | あり (互換性レベル 150 未満、パブリック プレビュー)| あり (SQL Server 2019 CTP 2.0 以降、互換性レベル 150 未満、パブリック プレビュー)|
| [インターリーブ実行](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#interleaved-execution-for-multi-statement-table-valued-functions) | あり (互換性レベル 140 未満)| あり (SQL Server 2017 以降、互換性レベル 140 未満)|
| [メモリ許可フィードバック (バッチ モード)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#batch-mode-memory-grant-feedback) | あり (互換性レベル 140 未満)| あり (SQL Server 2017 以降、互換性レベル 140 未満)|
| [メモリ許可フィードバック (行モード)](https://docs.microsoft.com/en-us/sql/relational-databases/performance/adaptive-query-processing?view=sql-server-2017#row-mode-memory-grant-feedback) | あり (互換性レベル 150 未満、パブリック プレビュー)| あり (SQL Server 2019 CTP 2.0 以降、互換性レベル 150 未満、パブリック プレビュー)|
| [スカラー UDF のインライン化](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#scalar-udf-inlining) | なし (ただし今後の更新プログラムで予定されている) | あり (SQL Server 2019 CTP 2.1 以降、互換性レベル 150 未満、パブリック プレビュー)|
| [テーブル変数の遅延コンパイル](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing?view=sql-server-2017#table-variable-deferred-compilation) | あり (互換性レベル 150 未満、パブリック プレビュー)| あり (SQL Server 2019 CTP 2.0 以降、互換性レベル 150 未満、パブリック プレビュー)|



## <a name="adaptive-query-processing"></a>アダプティブ クエリ処理

アダプティブ クエリ処理機能ファミリには、次のクエリ処理の機能強化が含まれています。 これらの機能強化で、最適化戦略がアプリケーション ワークロードの実行時条件に適用されます。 
- バッチ モード アダプティブ結合
- メモリ許可フィードバック
- 複数ステートメントのテーブル値関数 (MSTVF) のインターリーブ実行

### <a name="batch-mode-adaptive-joins"></a>バッチ モード アダプティブ結合

この機能により、キャッシュされている単独プランの実行中に、プランをより優れた結合戦略に動的に切り替えることができます。

バッチ モード アダプティブ結合の詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

### <a name="row-and-batch-mode-memory-grant-feedback"></a>行モードとバッチ モードのメモリ許可フィードバック

> [!NOTE]
> 行モード メモリ許可フィードバックはパブリック プレビューの機能です。  

この機能では、クエリに必要な実際のメモリを再計算します。 次に、キャッシュされたプランの付与値を更新します。 同時実行に影響を与える過剰なメモリ付与を減らします。 また、この機能では、ディスクへのコストが高い書き込みが発生する、過少評価されているメモリ付与も修正します。

メモリ許可フィードバックの詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

### <a name="interleaved-execution-for-mstvfs"></a>MSTVF のインターリーブ実行

インターリーブ実行では、関数に基づく実際の行数を使用して、より正確なダウンストリーム クエリ プランを決定します。 複数ステートメントのテーブル値関数 (MSTVF) の詳細については、「[テーブル値関数](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF)」を参照してください。

インターリーブ実行の詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

## <a name="table-variable-deferred-compilation"></a>テーブル変数の遅延コンパイル

> [!NOTE]
> テーブル変数の遅延コンパイルは、パブリック プレビュー機能です。  

テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するクエリのプランの品質および全体的なパフォーマンスが向上します。 最適化と最初のコンパイルの実行中に、この機能は実際テーブル変数の行数に基づくカーディナリティの推定を反映します。 この正確な行数の情報によって、ダウンストリーム プラン操作が最適化されます。

テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するステートメントのコンパイルは、そのステートメントが最初に実際に実行されるまで遅延されます。 この遅延コンパイルの動作は、一時テーブルの動作と同じです。 この変更によって、元の 1 行の推定値ではなく、実際のカーディナリティを使用できるようになります。 

テーブル変数の遅延コンパイルのパブリック プレビューは、Azure SQL Database で有効にすることができます。 そのためには、クエリの実行時に接続しているデータベースに対して互換性レベル 150 を有効にします。

詳細については、「[テーブル変数の遅延コンパイル](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation)」をご覧ください。

## <a name="scalar-udf-inlining"></a>スカラー UDF のインライン化

> [!NOTE]
> スカラー ユーザー定義関数 (UDF) のインライン化は、パブリック プレビュー機能です。  

スカラー UDF のインライン化によって、[スカラー UDF](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) は関係式に自動的に変換されます。 これらは呼び出し元の SQL クエリに埋め込まれます。 この変換により、スカラー UDF を利用するワークロードのパフォーマンスが向上します。 スカラー UDF のインライン化によって、UDF 内の操作をコストベースで簡単に最適化できるようになります。 その結果、非効率的で反復的な直列の実行プランではなく、効率的でセット指向の並列処理になります。 この機能は、データベース互換性レベル 150 では既定で有効です。

詳細については、「[スカラー UDF のインライン化](../user-defined-functions/scalar-udf-inlining.md)」を参照してください。

## <a name="approximate-query-processing"></a>概数クエリ処理

> [!NOTE]
> **APPROX_COUNT_DISTINCT** はパブリック プレビュー機能です。  

概数クエリ処理は新しい機能ファミリです。 絶対的な精度よりも応答性が重要となる場合に、大規模なデータ セット全体が集計されます。 たとえば、ダッシュボードに表示するために、100 億の行に対する **COUNT(DISTINCT())** を計算する場合などです。 この場合、重要なのは絶対的な精度ではなく、応答性です。 新しい集計関数 **APPROX_COUNT_DISTINCT** は、グループ内の一意の非 null 値の概数を返します。

詳細については、「[APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md)」をご覧ください。

## <a name="batch-mode-on-rowstore"></a>行ストアでのバッチ モード 

> [!NOTE]
> 行ストアでのバッチ モードは、パブリック プレビュー機能です。  

行ストアのバッチ モードでは、列ストア インデックスを要求せず、分析ワークロードをバッチ モードで実行できます。  この機能は、ディスク上のヒープと B ツリー インデックスに対するバッチ モード実行とビットマップ フィルターをサポートしています。 行ストアのバッチ モードでは、既存のすべてのバッチ モード対応演算子のサポートが有効になります。

### <a name="background"></a>背景情報

[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、分析ワークロードを促進する新機能である列ストア インデックスが導入されました。 後続の各リリースでユース ケースを拡張し、列ストア インデックスのパフォーマンスを向上させました。 これまでは、これらすべての機能を 1 つの機能として浮上させ、文書化しました。 テーブルに列ストア インデックスを作成します。 すると、分析ワークロードが高速になります。 ただし、関連しているが異なる 2 つのテクノロジ セットがあります。
- **列ストア** インデックスでは、分析クエリは必要な列のデータにのみアクセスできます。 列ストア形式のページ圧縮は、従来の**行ストア** インデックスの圧縮よりもはるかに効果的でもあります。 
- **バッチ モード**処理では、クエリ演算子によってデータがより効率的に処理されます。 一度に 1 行ずつではなく、複数行がバッチ処理されます。 他のいくつかのスケーラビリティの向上がバッチ モード処理に関連付けられています。 バッチ モードの詳細については、「[実行モード](../../relational-databases/query-processing-architecture-guide.md#execution-modes)」を参照してください。

2 セットの機能が連携して、入力/出力 (I/O) と CPU の使用率が向上します。
- 列ストア インデックスを使用すると、より多くのデータがメモリに格納されます。 その結果、I/O のニーズが減ります。
- バッチ モード処理では、CPU がより効率的に使用されます。

2 つのテクノロジは可能な限り相互活用されます。 たとえば、バッチ モード集計は、列ストア インデックス スキャンの一部として評価できます。 また、バッチ モード結合とバッチ モード集計により、Run-length エンコードを使用して圧縮された列ストア データをはるかに効率的に処理できます。 
 
2 つの機能は独立し使用できます。
* 列ストア インデックスを使用する行モード プランがあります。
* 行ストア インデックスのみを使用するバッチ モード プランがあります。 

通常、2 つの機能を一緒に使用すると、最適な結果が得られます。 そのため、これまで SQL Server のクエリ オプティマイザーは、列ストア インデックスのあるテーブルが少なくとも 1 つ関係するクエリに対してのみバッチ モード処理を検討しました。

列ストア インデックスは、一部のアプリケーションには適していません。 列ストア インデックスではサポートされていない他の機能を使用するアプリケーションもあります。 たとえば、インプレースの変更は列ストアの圧縮と互換性がありません。 そのため、クラスター化列ストアがあるテーブルでは、トリガーはサポートされません。 さらに重要なことに、列ストア インデックスによって **DELETE** および **UPDATE** ステートメントにオーバーヘッドが増えます。 

一部のトランザクションと分析のハイブリッド ワークロードでは、ワークロードのトランザクション面のオーバーヘッドが列ストア インデックスのメリットを上回ります。 このようなシナリオでは、バッチ モード処理単独での CPU 使用率を改善することができます。 そのため、行ストア機能のバッチ モードでは、すべてのクエリに対してバッチ モードが考慮されます。 どのインデックスが関係しているかは問題ではありません。

### <a name="workloads-that-might-benefit-from-batch-mode-on-rowstore"></a>行ストアでバッチ モードの恩恵を受ける可能性があるワークロード

次のワークロードは、行ストアでのバッチ モードの恩恵を受ける可能性があります。
* ワークロードの大部分が分析クエリで構成されています。 通常、このようなクエリには、数十万行以上を処理する結合や集計などの演算子があります。
* ワークロードが CPU バウンドです。 ボトルネックが IO の場合は、可能であれば列ストア インデックスを検討することを引き続きお勧めします。
* 列ストア インデックスを作成すると、ワークロードのトランザクション部分に過剰なオーバーヘッドがかかります。 または、列ストア インデックスの作成が現実的ではありません。アプリケーションは列ストア インデックスでまだサポートされていない機能に依存しているためです。

> [!NOTE]
> 行ストアでのバッチ モードは、CPU 使用量を減らすことでのみ支援できます。 ボトルネックが IO に関連し、データがまだキャッシュされていない場合 ("コールド" キャッシュ)、行ストアでのバッチ モードでは経過時間が向上しません。 同様に、すべてのデータをキャッシュするための十分なメモリがマシンにない場合、パフォーマンスは向上しない可能性があります。

### <a name="what-changes-with-batch-mode-on-rowstore"></a>行ストアでのバッチ モードによる変化

互換性レベルを 150 に移行する以外に、候補のワークロードに対して行ストアでのバッチ モードを有効にするためにユーザー側で変更を加える必要はありません。

クエリが列ストア インデックスのあるテーブルに関係しない場合でも、クエリ プロセッサではヒューリスティックを使用して、バッチ モードを検討するかどうかが決定されます。 ヒューリスティックは以下のチェックから構成されます。
1. テーブル サイズ、使用される演算子、入力クエリの推定カーディナリティの初期チェック。
2. オプティマイザーによってクエリに対する新しい低コストのプランが検出されたときの追加のチェックポイント。 これらの代替プランがバッチ モードを大いに利用しない場合、オプティマイザーではバッチ モードの代替手段の探索が停止されます。

行ストアでバッチ モードが使用されている場合、実際の実行モードはクエリ プランで **[バッチ モード]** と表示されます。 scan 演算子では、ディスク上のヒープと B ツリー インデックスにバッチ モードを使用します。 このバッチ モード スキャンでは、バッチ モードのビットマップ フィルターを評価できます。 また、プラン内の他のバッチ モード演算子も表示されることがあります。 たとえば、ハッシュ結合、ハッシュ ベースの集計、並べ替え、ウィンドウ集計、フィルター、連結、Compute Scalar 演算子などです。

### <a name="remarks"></a>Remarks

* クエリ プランは常にバッチ モードを使用するわけではありません。 クエリ オプティマイザーでは、クエリがバッチ モードの恩恵を受けないと判断される場合があります。 
* クエリ オプティマイザーの検索スペースは変化しています。 そのため、行モード プランを取得する場合、それがより低い互換性レベルで取得するプランと同じではない可能性があります。 また、バッチ モード プランを取得する場合、それが列ストア インデックスを使用して取得したプランと同じではない可能性があります。 
* 新しいバッチ モード行ストア スキャンが原因で、プランは、列ストア インデックスと行ストア インデックスが混在するクエリに対して変化する可能性もあります。
* 現在、行ストア スキャンには、新しいバッチ モードに対して制限事項があります。 
    * インメモリ OLTP テーブル、またはディスク上のヒープと B ツリー以外のインデックスに対しては開始されません。 
    * 大規模なオブジェクト (LOB) 列がフェッチまたはフィルター処理された場合にも開始されません。 この制限には、スパース列セットと XML 列が含まれます。
* 列ストア インデックスでもバッチ モードが使用されないクエリがあります。 たとえば、カーソルを含むクエリです。 これと同様の例外は、行ストアのバッチ モードにも適用されます。

### <a name="configure-batch-mode-on-rowstore"></a>行ストアにバッチ モードを構成する

**BATCH_MODE_ON_ROWSTORE** データベース スコープ構成は、既定で有効です。 データベースの互換性レベルを変更せずに、行ストアのバッチ モードを無効にすることができます。

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

データベース スコープ構成を使用して行ストアのバッチ モードを無効にすることができます。 ただし、その場合でも **ALLOW_BATCH_MODE** クエリ ヒントを使用してクエリ レベルで設定をオーバーライドできます。 次の例では、データベース スコープ構成を使用して無効になっている行ストアでのバッチ モードを有効にします。

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

**DISALLOW_BATCH_MODE** クエリ ヒントを使用して、特定のクエリに対して行ストアでのバッチ モードを無効にすることもできます。 次の例を参照してください。

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('DISALLOW_BATCH_MODE'));
```

## <a name="see-also"></a>参照

[SQL Server データベース エンジンと Azure SQL Database のパフォーマンス センター](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[クエリ処理アーキテクチャ ガイド](../../relational-databases/query-processing-architecture-guide.md)    
[プラン表示の論理操作と物理操作のリファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[結合](../../relational-databases/performance/joins.md)    
[アダプティブ クエリ処理のデモンストレーション](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)       
[インテリジェントな QP のデモ](https://github.com/joesackmsft/Conferences/blob/master/IQPDemos/IQP_Demo_ReadMe.md)   
