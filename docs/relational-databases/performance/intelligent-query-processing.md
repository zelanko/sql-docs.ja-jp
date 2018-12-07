---
title: Microsoft SQL データベースでのインテリジェントなクエリ処理 | Microsoft Docs
description: SQL Server および Azure SQL Database のクエリ パフォーマンスを向上させるためのインテリジェントなクエリ処理の機能です。
ms.custom: ''
ms.date: 11/07/2018
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
ms.openlocfilehash: d48f9fd87ff375a518b038d9ed4ef4a8d42675cc
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52403927"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>SQL データベースでのインテリジェントなクエリ処理
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

**インテリジェントなクエリ処理**機能ファミリには、実装の労力は最小限で既存のワークロードのパフォーマンスを改善する、広範な影響がある機能が含まれています。

![インテリジェントなクエリ処理の機能](./media/3_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>アダプティブ クエリ処理
アダプティブ クエリ処理の機能ファミリには、最適化戦略をアプリケーション ワークロードの実行時条件に適用するクエリ処理の改善が含まれます。 これらの改善には、以下が含まれます。 
-  バッチ モード アダプティブ結合
-  メモリ許可フィードバック
-  複数ステートメントのテーブル値関数 (MSTVF) のインターリーブ実行

### <a name="batch-mode-adaptive-joins"></a>バッチ モード アダプティブ結合
この機能により、キャッシュされている単独プランの実行中に、プランをより優れた結合戦略に動的に切り替えることができます。

バッチ モード アダプティブ結合の詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

### <a name="row-and-batch-mode-memory-grant-feedback"></a>行モードとバッチ モードのメモリ許可フィードバック
> [!NOTE]
> 行モード メモリ許可フィードバックはパブリック プレビューの機能です。  

この機能はクエリに必要な実際のメモリを再計算して、キャッシュされているプランで許可されている値を更新するため、コンカレンシーに影響する過大なメモリ許可が少なくなり、過剰なディスク書き込みの原因となる過小評価されたメモリ許可が修正されます。

メモリ許可フィードバックの詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>複数ステートメントのテーブル値関数 (MSTVF) のインターリーブ実行
インターリーブ実行では、関数に基づく実際の行数を使用して、より正確なダウンストリーム クエリ プランを決定します。 複数ステートメントのテーブル値関数 (MSTVF) の詳細については、「[テーブル値関数](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#TVF)」を参照してください。

インターリーブ実行の詳細については、「[Microsoft SQL データベースでのアダプティブ クエリの処理](../../relational-databases/performance/adaptive-query-processing.md)」をご覧ください。

## <a name="table-variable-deferred-compilation"></a>テーブル変数の遅延コンパイル
> [!NOTE]
> テーブル変数の遅延コンパイルは、パブリック プレビュー機能です。  

テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するクエリのプランの品質および全体的なパフォーマンスが向上します。 最適化と最初のコンパイルの実行中に、この機能は実際テーブル変数の行数に基づくカーディナリティの推定を反映します。  この正確な行数の情報は、ダウンストリーム プラン操作を最適化するために使用されます。

テーブル変数の遅延コンパイルを使用すると、テーブル変数を参照するステートメントのコンパイルは、そのステートメントが最初に実際に実行されるまで遅延されます。 この遅延コンパイルの動作は、一時テーブルの動作と同じです。この変更によって、元の 1 行の推定値ではなく、実際のカーディナリティを使用できるようになります。 Azure SQL Database でテーブル変数の遅延コンパイルのパブリック プレビューを有効にするには、クエリを実行する際に接続されるデータベースのデータベース互換レベル 150 を有効にします。

詳細については、「[テーブル変数の遅延コンパイル](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation )」をご覧ください。

## <a name="scalar-udf-inlining"></a>スカラー UDF のインライン化
> [!NOTE]
> スカラー UDF のインライン化は、パブリック プレビュー機能です。  

スカラー UDF のインライン化では、[スカラー ユーザー定義関数 (UDF)](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md#Scalar) が関係式に変換され、それらが呼び出し元の SQL クエリに埋め込まれます。これにより、スカラー UDF を利用するワークロードのパフォーマンスが向上します。 スカラー UDF のインライン化によって、UDF 内の操作に対するコストに基づく最適化が促進され、その結果として、非効率な、反復的および直列的な実行プランではなく、セット指向で並列的である効率的なプランが提供されます。 この機能は、データベース互換性レベル 150 では既定で有効です。

詳細については、「[スカラー UDF のインライン化](https://docs.microsoft.com/sql/relational-databases/user-defined-functions/scalar-udf-inlining?view=sqlallproducts-allversions)」を参照してください。

## <a name="approximate-query-processing"></a>概数クエリ処理
> [!NOTE]
> APPROX_COUNT_DISTINCT はパブリック プレビューの機能です。  

概数クエリ処理とは、絶対的な精度よりも応答性が重要となる場合に、大規模なデータ セット全体の集計を提供するために設計された、新しい機能ファミリです。  たとえば、ダッシュボードに表示するために、100 億の行に対する COUNT(DISTINCT()) を計算する場合などです。  この場合、重要なのは絶対的な精度ではなく、応答性です。 新しい集計関数 APPROX_COUNT_DISTINCT は、グループ内の一意の非 null 値の概数を返します。

詳細については、「[APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md)」をご覧ください。

## <a name="batch-mode-on-rowstore"></a>行ストアでのバッチ モード 
> [!NOTE]
> 行ストアでのバッチ モードは、パブリック プレビュー機能です。  

### <a name="background"></a>背景情報
[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、分析ワークロードを促進する新機能である列ストア インデックスが導入されました。 後続の各リリースでユース ケースを拡張し、列ストア インデックスのパフォーマンスを向上させました。 これまでは、これらすべての機能を 1 つの機能として浮上させ、文書化しました。テーブルに対して列ストア インデックスを作成すると、分析ワークロードが "高速化" します。 ただし実際には、関連しているが異なる 2 つのテクノロジ セットがあります。
- **列ストア** インデックスでは、分析クエリは必要な列のデータにのみアクセスできます。 列ストア形式では、従来の "行ストア" インデックスのページ圧縮よりもはるかに効果的な圧縮も可能です。 
- **バッチ モード**処理では、一度に 1 行ではなく行のバッチを処理することで、クエリ演算子によるデータ処理が効率的になります。 他のいくつかのスケーラビリティの向上がバッチ モード処理に関連付けられています。 バッチ モードの詳細については、「[実行モード](../../relational-databases/query-processing-architecture-guide.md#execution-modes)」を参照してください。

2 セットの機能が連携して、I/O と CPU の使用率を向上させます。
- 列ストア インデックスを使用すると、より多くのデータがメモリに収まるので、I/O の必要性が低減されます。
- バッチ モード処理では、CPU がより効率的に使用されます。

2 つのテクノロジは可能な限り相互活用されます。 たとえば、バッチ モード集計は、列ストア インデックス スキャンの一部として評価できます。 また、バッチ モード結合とバッチ モード集計により、Run-length エンコードを使用して圧縮された列ストア データをはるかに効率的に処理できます。 
 
2 つの機能は既に独立して使用できます。列ストア インデックスを使用する行モード プランを取得でき、行ストア インデックスのみを使用するバッチ モード プランを取得できます。 しかし、ほとんどの場合に、2 つの機能が一緒に使用されると最高の結果が得られるので、SQL のクエリ オプティマイザーはこれまで、列ストア インデックスのあるテーブルが少なくとも 1 つ関係するクエリに対してのみバッチ モード処理を検討しました。

一部のアプリケーションでは、列ストア インデックスは実行可能なオプションではありません。列ストア インデックスでサポートされていない他のいくつかの機能がアプリケーションで使用されるからです (たとえばトリガーは、クラスター化列ストア インデックスのあるテーブルではサポートされていません)。 さらに重要なのは、インプレース変更は列ストア圧縮と互換性がないので、列ストア インデックスによって DELETE および UPDATE ステートメントにオーバーヘッドが追加されることです。 一部のハイブリッド トランザクション分析ワークロードでは、列ストア インデックスによって分析クエリにもたらされるメリットをワークロードのトランザクション面でのオーバーヘッドが上回ります。 このようなシナリオでは、バッチ モード処理だけでも CPU 使用率を向上させることができます。そのため、**行ストアでのバッチ モード**機能では、関連するインデックスに関係なく、すべてのクエリに対してバッチ モードが考慮されます。

### <a name="what-workloads-may-benefit-from-batch-mode-on-rowstore"></a>行ストアでのバッチ モードの恩恵を受ける可能性があるワークロード
次のワークロードは、行ストアでのバッチ モードの恩恵を受ける可能性があります。
1.  ワークロードの大部分が分析クエリで構成される (目安として、数十万行以上の結合または集計処理などの演算子を使用したクエリ)。**かつ**
2.  ワークロードが CPU バウンドである (ボトルネックが IO の場合は、可能であれば列ストア インデックスを検討することを引き続きお勧めします)。**かつ**
3.  列ストア インデックスを作成すると、ワークロードのトランザクション部分に対するオーバーヘッドが増えすぎる、**または**列ストア インデックスでまだサポートされていない機能にアプリケーションが依存しているため列ストアインデックスの作成が現実的でない。

> [!NOTE]
> 行ストアでのバッチ モードは、CPU 使用量を減らすことでのみ支援できます。 ボトルネックが IO に関連し、データがまだキャッシュされていない場合 ("コールド" キャッシュ)、行ストアでのバッチ モードでは経過時間が向上しません。 同様に、すべてのデータをキャッシュするための十分なメモリがマシンにない場合、パフォーマンスは向上しない可能性があります。

### <a name="what-changes-with-batch-mode-on-rowstore"></a>行ストアでのバッチ モードによる変化
互換性レベルを 150 に移行する以外に、候補のワークロードに対して行ストアでのバッチ モードを有効にするためにユーザー側で変更を加える必要はありません。

クエリが列ストア インデックスのあるテーブルに関係しない場合でも、クエリ プロセッサではヒューリスティックを使用して、バッチ モードを検討するかどうかが決定されます。 ヒューリスティックは以下から構成されます。
1.  テーブル サイズ、使用される演算子、入力クエリの推定カーディナリティの初期チェック。
2.  オプティマイザーによってクエリに対する新しい低コストのプランが検出されたときの追加のチェックポイント。 これらの代替プランがバッチ モードを大いに利用しない場合、オプティマイザーではバッチ モードの代替手段の探索が停止されます。

行ストアでのバッチ モードを使用する場合、クエリ実行プランでは、実際の実行モードが、ディスク上のヒープと B ツリー インデックスに対してスキャン演算子によって使用される "バッチ モード" として表示されます。  このバッチ モード スキャンでは、バッチ モードのビットマップ フィルターを評価できます。  プランでは、ハッシュ結合、ハッシュ ベースの集計、並べ替え、ウィンドウ集計、フィルター、連結、Compute Scalar 演算子などの他のバッチ モード演算子も表示されることがあります。

### <a name="remarks"></a>Remarks
1.  クエリ プランによってバッチ モードが使用されるという保証はありません。 クエリ オプティマイザーでは、クエリがバッチ モードの恩恵を受けないと判断される場合があります。 
2.  クエリ オプティマイザーの検索スペースは変化するので、行モード プランを取得した場合に、それがより低い互換性レベルで取得するプランと同じであるという保証はありません。 また、バッチ モード プランを取得する場合に、それが列ストア インデックスを使用して取得したプランと同じであるという保証はありません。 
3.  新しいバッチ モード行ストア スキャンが原因で、プランは、列ストア インデックスと行ストア インデックスが混在するクエリに対してわずかに変化する可能性もあります。
4.  新しい行ストア スキャンでのバッチ モードに対する現在の制限事項: インメモリ OLTP テーブル、またはディスク上のヒープと B ツリー以外のインデックスに対しては開始されません。 LOB 列がフェッチまたはフィルター処理された場合にも開始しません。 この制限には、スパース列セットと XML 列が含まれます。
5.  バッチ モードが列ストア インデックスと共に使用されないクエリ (たとえばカーソルに関連するクエリ) があり、この同じ除外が行ストアでのバッチ モードにも拡張されます。

### <a name="configuring-batch-mode-on-rowstore"></a>行ストアでのバッチ モードの構成
BATCH_MODE_ON_ROWSTORE データベース スコープ構成は、既定でオンになり、データベース互換性レベルを変更する必要なく、行ストアでのバッチ モードを無効にするために使用できます。

```sql
-- Disabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = OFF;

-- Enabling batch mode on rowstore
ALTER DATABASE SCOPED CONFIGURATION SET BATCH_MODE_ON_ROWSTORE = ON;
```

データベース スコープ構成を使用して行ストアでのバッチ モードを無効にできますが、その場合も ALLOW_BATCH_MODE クエリ ヒントを使用してクエリ レベルで設定をオーバーライドできます。 次の例では、データベース スコープ構成を使用して無効になっている行ストアでのバッチ モードを有効にします。

```sql
SELECT [Tax Rate], [Lineage Key], [Salesperson Key], SUM(Quantity) AS SUM_QTY, SUM([Unit Price]) AS SUM_BASE_PRICE, COUNT(*) AS COUNT_ORDER
FROM Fact.OrderHistoryExtended
WHERE [Order Date Key]<=DATEADD(dd, -73, '2015-11-13')
GROUP BY [Tax Rate], [Lineage Key], [Salesperson Key]
ORDER BY [Tax Rate], [Lineage Key], [Salesperson Key]
OPTION(RECOMPILE, USE HINT('ALLOW_BATCH_MODE'));
```

DISALLOW_BATCH_MODE のクエリ ヒントを使用して、特定のクエリに対して行ストアでのバッチ モードを無効にすることもできます。 例 :

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
