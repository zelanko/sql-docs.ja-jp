---
title: "クイック スタート 1: Transact-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ | Microsoft Docs"
ms.custom: 
ms.date: 12/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c25a164-547d-43c4-8484-6b5ee3cbaf3a
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82286b0d52ff37697ad9197b88c45935137a8dae
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="survey-of-initial-areas-in-in-memory-oltp"></a>インメモリ OLTP での初期領域の調査
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
この記事は、Microsoft SQL Server と Azure SQL データベースのインメモリ OLTP パフォーマンス機能の基本を短時間で学習する開発者を対象にしています。  
  
この記事では、インメモリ OLTP の以下のことについて説明します。  
  
- 機能の概要。  
- 機能を実装する主なコード サンプル。  
  
  
SQL Server および SQL データベースにおけるインメモリ テクノロジのサポートにはわずかな違いしかありません。  
  
  
インメモリ OLTP は、一部のブログでは *Hekaton*と呼ばれています。  
  
  
<a name="benefits-of-in-memory-features-21a"></a>  
  
## <a name="benefits-of-in-memory-features"></a>インメモリ機能の利点  
  
SQL Server では、多くのアプリケーション システムのパフォーマンスを大幅に改善できるインメモリ機能が提供されます。 この記事では考慮事項を簡単に説明します。  
  
  
### <a name="features-for-oltp-online-transactional-processing"></a>OLTP (オンライン トランザクション処理) の機能  
  
  
多数の SQL INSERT を同時に処理する必要があるシステムには OLTP 機能が最適です。  
  
- ベンチマークでは、インメモリ機能を導入することで速度が 5 倍から 20 倍に向上することが示されています。  
  
  
Transact-SQL で大量の計算を処理するシステムには最適です。  
  
- 大量計算専用のストアド プロシージャでは、実行速度が最大 99 倍になります。  
  
  
後で、インメモリ OLTP によるパフォーマンスの向上を実証する以下の記事を参照してください。  
  
- 「[実証: インメモリ OLTP によるパフォーマンスの向上](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) 」には、大幅なパフォーマンス向上が望める小規模なデモが用意されています。  
- 「[Sample Database for In-Memory OLTP](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) 」 (インメモリ OLTP のサンプル データベース) には、より大規模なデモが用意されています。  
  
  
  
### <a name="features-for-operational-analytics"></a>運用分析の機能  
  
インメモリ分析では、通常、GROUP BY 句を含めることによってトランザクション データを集計する SQL SELECT を参照します。 運用分析では主に *列ストア* というインデックスの種類が使用されます。  
  
2 つの主なシナリオを以下に示します。  
  
- *バッチ運用分析* では、営業時間後に実行されるか、トランザクション データのコピーを持つセカンダリ ハードウェアに対して実行される集計処理を参照します。  
  - [Azure SQL データ ウェアハウス](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-overview-what-is/) もバッチ運用分析に関連します。  
- *リアルタイム運用分析* では、営業時間内およびトランザクション ワークロードに使用されるプライマリ ハードウェアで実行される集計処理を参照します。  
  
  
この記事では分析ではなく OLTP に焦点を当てています。 列ストア インデックスを使用した SQL での分析の詳細については、次の項目を参照してください。  
  
- [列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
- [列ストア インデックス ガイド](../../relational-databases/indexes/columnstore-indexes-overview.md)  
  
  
> [!NOTE]
> 「 [Azure SQL Database - In-Memory Technologies](http://channel9.msdn.com/Blogs/Windows-Azure/Azure-SQL-Database-In-Memory-Technologies)」 (Azure SQL Database - インメモリ テクノロジ) では、インメモリ機能に関する 2 分間のビデオをご覧いただけます。 ビデオの制作日は 2015 年 12 月です。  


### <a name="columnstore"></a>列ストア

お勧めのブログの投稿を参照しながら、さまざまな観点から列ストア インデックスについて説明します。 多くの投稿では、列ストアがサポートしているリアルタイム運用分析の概念について詳しく説明します。  これらの投稿は、2016 年 3 月に Microsoft のプログラム マネージャーである Sunil Agarwal が書いたものです。

#### <a name="real-time-operational-analytics"></a>リアルタイム運用分析

1. [インメモリ テクノロジを使用したリアルタイム運用分析](https://blogs.technet.microsoft.com/dataplatforminsider/2015/12/09/real-time-operational-analytics-using-in-memory-technology/)
2. [リアルタイム運用分析 - 非クラスター化列ストア インデックス (NCCI) の概要](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-using-nonclustered-columnstore-index/)
3. [リアルタイム運用分析: SQL Server 2016 で非クラスター化列ストア インデックス (NCCI) を使用する単純な例](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/29/real-time-operational-analytics-simple-example-using-nonclustered-clustered-columnstore-index-ncci/)
4. [リアルタイム運用分析: SQL Server 2016 の DML 運用と非クラスター化列ストア インデックス (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/04/real-time-operational-analytics-dml-operations-and-nonclustered-columnstore-index-ncci-in-sql-server-2016/)
5. [リアルタイム運用分析: フィルターした非クラスター化列ストア インデックス (NCCI)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-filtered-nonclustered-columnstore-index-ncci/)
6. [リアルタイム運用分析: 非クラスター化列ストア インデックス (NCCI) の圧縮遅延オプション](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-for-nonclustered-columnstore-index-ncci/)
7. [リアルタイム運用分析: NCCI とパフォーマンスを使用した圧縮遅延オプション](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/06/real-time-operational-analytics-compression-delay-option-with-ncci-and-the-performance/)
8. [リアルタイム運用分析: メモリ最適化テーブルと列ストア インデックス](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/real-time-operational-analytics-memory-optimized-table-and-columnstore-index/)

#### <a name="defragment-a-columnstore-index"></a>列ストア インデックスを最適化する

1. [REORGANIZE コマンドを使用した列ストア インデックスの最適化](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)
2. [REORGANIZE の列ストア インデックス マージ ポリシー](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)

#### <a name="bulk-importation-of-data"></a>データの一括インポート

1. [クラスター化列ストア: 一括読み込み](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2014/07/27/clustered-column-store-index-bulk-loading-the-data/)
2. [クラスター化列ストア: データ読み込みの最適化 - 最小ログ記録](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/10/clustered-columnstore-index-data-load-optimizations-minimal-logging/)
3. [クラスター化列ストア インデックス: データ読み込みの最適化 - 並行一括インポート](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/02/28/clustered-columnstore-index-parallel-bulk-import/)





<a name="features-on-in-memory-oltp-13b"></a>  
  
## <a name="features-of-in-memory-oltp"></a>インメモリ OLTP の機能  
  
インメモリ OLTP での主な機能を見てみましょう。  
  
  
#### <a name="memory-optimized-tables"></a>メモリ最適化テーブル  
  
CREATE TABLE ステートメントの T-SQL キーワード MEMORY_OPTIMIZED は、ディスクではなく、アクティブ メモリに存在するテーブルの作成方法を示します。  
  
  
[メモリ最適化テーブル](../../relational-databases/in-memory-oltp/memory-optimized-tables.md) はアクティブ メモリ内に存在し、ディスク上にセカンダリ コピーを保持します。  
  
- ディスク上のコピーは、サーバーまたはデータベースがシャットダウンして再起動した後の日常的な復旧に使用されます。 このメモリとディスクの二重性はユーザーとユーザー コードに対して完全に非表示になります。  
  
  
#### <a name="natively-compiled-modules"></a>ネイティブ コンパイル モジュール  
  
CREATE PROCEDURE ステートメントの T-SQL キーワード NATIVE_COMPILATION は、ネイティブ プロシージャの作成方法を示します。 T-SQL ステートメントは、データベースがオンラインで循環されるたびにネイティブ プロシージャの初回使用時にコンピューター語コードにコンパイルされます。 T-SQL 命令がそれぞれ解釈されるまで長時間待つ必要はなくなりました。  
  
- ネイティブ コンパイル ストアド プロシージャの結果は、解釈されたストアド プロシージャの 1/100 の時間で得られます。  
  
  
ネイティブ モジュールが参照できるのはメモリ最適化テーブルのみで、ディスク ベース テーブルを参照することはできません。  
  
ネイティブ コンパイル モジュールには次の 3 種類があります。  
  
- [ネイティブ コンパイル ストアド プロシージャ](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)。  
- スカラーのネイティブ コンパイル ユーザー定義関数 (UDF)。  
- ネイティブ コンパイル トリガー。  
  
  
#### <a name="availability-in-azure-sql-database"></a>Azure SQL Database での提供状況  
  
インメモリ OLTP および列ストアは、Azure SQL Database で使用できます。 詳細については、「[Optimize Performance using In-Memory Technologies in SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-in-memory)」 (SQL データベースでのインメモリ テクノロジを使用したパフォーマンスの最適化) を参照してください。
  
  
<a name="ensure-compatibility-level-gteq-130-99c"></a>  
  
## <a name="1-ensure-compatibility-level--130"></a>1.互換性レベルを 130 以上に設定する  
  
  
このセクションと以降のセクションでは、インメモリ OLTP 機能の実装に使用できる Transact-SQL 構文をまとめて示します。  
  
  
まず、データベースの互換性レベルを少なくとも 130 に設定することが重要です。 ここでは、現在のデータベースに設定されている現在の互換性レベルを表示する T-SQL コードを示します。  
  
  
  
  
  
    SELECT d.compatibility_level  
        FROM sys.databases as d  
        WHERE d.name = Db_Name();  
  
  
  
  
次は、必要に応じて互換性レベルを更新するための T-SQL コードを示します。  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET COMPATIBILITY_LEVEL = 130;  
  
  
  
  
<a name="elevate-to-snapshot-26n"></a>  
  
## <a name="2-elevate-to-snapshot"></a>2.スナップショットに昇格させる  
  
  
トランザクションがディスク ベース テーブルとメモリ最適化テーブルの両方に関与することを、*複数のコンテナーにまたがるトランザクション*といいます。 このようなトランザクションの場合、トランザクションのメモリ最適化部分が、SNAPSHOT と呼ばれるトランザクション分離レベルで動作する必要があります。  
  
複数のコンテナーにまたがるトランザクションでメモリ最適化テーブルを確実にこのレベルで動作させるには、次の T-SQL を実行して[データベース設定を変更](../../t-sql/statements/alter-database-transact-sql-set-options.md)します。  
  
  
  
  
    ALTER DATABASE CURRENT  
        SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
  
  
  
  
<a name="create-an-optimized-filegroup-24r"></a>  
  
## <a name="3-create-an-optimized-filegroup"></a>3.最適化ファイル グループを作成する  
  
  
Microsoft SQL Server では、メモリ最適化テーブルを作成する前に、CONTAINS MEMORY_OPTIMIZED_DATA を宣言するファイルグループを作成する必要があります。 作成したファイルグループはデータベースに割り当てられます。 詳細については、次の項目を参照してください。  
  
- [メモリ最適化ファイルグループ](../../relational-databases/in-memory-oltp/the-memory-optimized-filegroup.md)  
  
  
Azure SQL Database では、このようなファイルグループを作成する必要はありません (作成できません)。  

次のサンプルの T-SQL スクリプトでは、インメモリ OLTP のデータベースを有効にし、すべての推奨設定を構成します。 SQL Server と Azure SQL Database の両方で機能します: [enable-in-memory-oltp.sql](https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/in-memory/t-sql-scripts/enable-in-memory-oltp.sql)。
  
  
<a name="create-a-memory-optimized-table-26y"></a>  
  
## <a name="4-create-a-memory-optimized-table"></a>4.メモリ最適化テーブルを作成する  
  
  
  
  
重要な Transact-SQL キーワードは MEMORY_OPTIMIZED です。  
  
  
  
  
    CREATE TABLE dbo.SalesOrder  
    (  
        SalesOrderId   integer        not null  IDENTITY  
            PRIMARY KEY NONCLUSTERED,  
        CustomerId     integer        not null,  
        OrderDate      datetime       not null  
    )  
        WITH  
            (MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
  
メモリ最適化テーブルに対する Transact SQL の INSERT ステートメントと SELECT ステートメントは、通常のテーブルの場合と同じです。  
  
#### <a name="alter-table-for-memory-optimized-tables"></a>メモリ最適化テーブルの ALTER TABLE  
  
ALTER TABLE...ADD/DROP では、メモリ最適化テーブルの列またはインデックスを追加または削除できます。  
  
- メモリ最適化テーブルに対して CREATE INDEX や DROP INDEX を実行することはできません。代わりに、ALTER TABLE ...ADD/DROP INDEX を使用してください。  
- 詳細については、「[メモリ最適化テーブルの変更](../../relational-databases/in-memory-oltp/altering-memory-optimized-tables.md)」を参照してください。  
  
  
#### <a name="plan-your-memory-optimized-tables-and-indexes"></a>メモリ最適化テーブルとインデックスの計画  
  
  
- [メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md)  
- [インメモリ OLTP でサポートされていない Transact-SQL の構造](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
  
<a name="create-a-natively-compiled-stored-procedure-native-proc-29u"></a>  
  
## <a name="5-create-a-natively-compiled-stored-procedure-native-proc"></a>5.ネイティブ コンパイル ストアド プロシージャ (ネイティブ プロシージャ) を作成する  
  
  
重要なキーワードは NATIVE_COMPILATION です。  
  
  
  
  
    CREATE PROCEDURE ncspRetrieveLatestSalesOrderIdForCustomerId  
        @_CustomerId   INT  
        WITH  
            NATIVE_COMPILATION,  
            SCHEMABINDING  
    AS  
    BEGIN ATOMIC  
        WITH  
            (TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
            LANGUAGE = N'us_english')  
      
        DECLARE @SalesOrderId int, @OrderDate datetime;  
      
        SELECT TOP 1  
                @SalesOrderId = s.SalesOrderId,  
                @OrderDate    = s.OrderDate  
            FROM dbo.SalesOrder AS s  
            WHERE s.CustomerId = @_CustomerId  
            ORDER BY s.OrderDate DESC;  
      
        RETURN @SalesOrderId;  
    END;  
  
  
  
  
SCHEMABINDING キーワードは、ネイティブ プロシージャで参照されているテーブルを削除するには、先にネイティブ プロシージャを削除しておく必要があることを意味します。 詳細については、「[ネイティブ コンパイル ストアド プロシージャの作成](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)」を参照してください。  
  
  
<a name="execute-the-native-proc-31e"></a>  
  
## <a name="6-execute-the-native-proc"></a>6.ネイティブ プロシージャを実行する  
  
  
テーブルにデータを 2 行挿入します。  
  
  
  
  
    INSERT into dbo.SalesOrder  
            ( CustomerId, OrderDate )  
        VALUES  
            ( 42, '2013-01-13 03:35:59' ),  
            ( 42, '2015-01-15 15:35:59' );  
  
  
  
  
EXECUTE によるネイティブ コンパイル ストアド プロシージャの呼び出しが後に続きます。  
  
  
  
  
    DECLARE @LatestSalesOrderId int, @mesg nvarchar(128);  
      
    EXECUTE @LatestSalesOrderId =  
        ncspRetrieveLatestSalesOrderIdForCustomerId 42;  
      
    SET @mesg = CONCAT(@LatestSalesOrderId,  
        ' = Latest SalesOrderId, for CustomerId = ', 42);  
    PRINT @mesg;  
      
    -- Here is the actual PRINT output:  
    -- 2 = Latest SalesOrderId, for CustomerId = 42  
  
  
  
  
<a name="guide-to-the-documentation-and-next-steps-32w"></a>  
  
### <a name="guide-to-the-documentation-and-next-steps"></a>ドキュメント ガイドと次のステップ  
  
  
上記の簡単な例では、インメモリ OLTP の高度な機能を学習するための基礎を示しました。 以降のセクションでは、特に考慮する必要がある事項と、その詳細について説明した参照先を示します。  
  
  
  
<a name="how-do-in-memory-oltp-features-work-so-much-faster-33v"></a>  
  
## <a name="how-in-memory-oltp-features-work-so-much-faster"></a>インメモリ OLTP 機能が高速で動作するしくみ  
  
  
以降のサブセクションでは、インメモリ OLTP 機能が内部でどのように動作してパフォーマンスを向上させているかについて、簡単に説明します。  
  
  
<a name="how-do-memory-optimized-tables-perform-faster-34q"></a>  
  
### <a name="how-memory-optimized-tables-perform-faster"></a>メモリ最適化テーブルが高速で動作するしくみ  
  
  
**デュアル構成:** メモリ最適化テーブルはデュアル構成になっており、アクティブ メモリ内とハード ディスク上に 1 つずつ存在します。 各トランザクションは両方のテーブルに対してコミットされます。 トランザクションは、より高速なアクティブ メモリ内のテーブルに対して操作を行います。 そのためメモリ最適化テーブルは、ディスクよりも高速なアクティブ メモリの恩恵を受けることになります。 さらに、アクティブ メモリは非常に敏捷なので、速度に関して最適化されたより高度なテーブル構造も使用できます。 高度なテーブル構造はページレスでもあるため、ラッチやスピンロックのオーバーヘッドや競合を回避できます。  
  
  
**ロックなし:** メモリ最適化テーブルは *オプティミスティック* なアプローチにより、データの整合性と、同時実行性および高スループットとのバランスを取っています。 トランザクションの間、更新されたデータ行のどのバージョンもロックすることはありません。 これにより、特に大規模システムでは大幅に競合を減らすことができます。  
  
  
**行のバージョン:** メモリ最適化テーブルは、更新された行をロックする代わりに、更新された行の新しいバージョンを (tempdb ではなく) テーブルに追加します。 元の行は、トランザクションがコミットされるまで保持されます。 トランザクションの間も、他のプロセスが行の元のバージョンを読み取ることができます。  
  
- ディスク ベース テーブルの行に複数のバージョンが作成されると、行のバージョンは一時的に tempdb に格納されます。  
  
  
**ログ記録の削減:** 行の更新前と更新後のバージョンは、メモリ最適化テーブルに保持されます。 この行のペアによって、従来はログ ファイルに書き込まれていた情報の多くが提供されるので、 システムが書き込むログの量も頻度も少なくて済むようになります。 ログの量と頻度が減っても、トランザクションの整合性は保証されます。  
  
  
<a name="how-do-native-procs-perform-faster-35x"></a>  
  
### <a name="how-native-procs-perform-faster"></a>ネイティブ プロシージャが高速で動作するしくみ  
  
通常の解釈されたストアド プロシージャをネイティブ コンパイル ストアド プロシージャに変換すると、実行時の命令の数が大幅に減少します。  
  
  
<a name="trade-offs-of-in-memory-features-36j"></a>  
  
## <a name="trade-offs-of-in-memory-features"></a>インメモリ機能のトレードオフ  
  
  
コンピューター サイエンスの世界では一般的なことですが、インメモリ機能によるパフォーマンスの向上にはトレードオフがあります。 優れた機能にはよりコストがかかりますが、それに見合うだけの有益な利点がもたらされます。 トレードオフに関する包括的なガイドは次の場所にあります。

- [SQL Server でのインメモリ OLTP 機能の採用計画](../../relational-databases/in-memory-oltp/plan-your-adoption-of-in-memory-oltp-features-in-sql-server.md)

このセクションの残りの部分では、主要な計画とトレードオフの考慮事項の一部を示します。
  
<a name="trade-offs-of-memory-optimized-tables-37d"></a>  
  
### <a name="trade-offs-of-memory-optimized-tables"></a>メモリ最適化テーブルのトレードオフ  
  
  
**メモリの推定:** メモリ最適化テーブルが消費するアクティブ メモリの量を見積もる必要があります。 コンピューター システムに、メモリ最適化テーブルをホストするのに十分なメモリ容量が必要です。 詳細については、次の項目を参照してください。  
  
- [メモリ使用量の監視とトラブルシューティング](../../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)  
- [メモリ最適化テーブルのメモリ必要量の推定](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md)  
- [メモリ最適化テーブルのテーブルと行のサイズ](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
**大規模テーブルのパーティション分割:** 大量のアクティブ メモリの需要を満たす方法の 1 つは、大規模なテーブルをパーティション分割して、 *使用中の最近の* データ行を格納する部分 (メモリ内) と、出荷済みや完了済みの注文など、 *使用していない古い* 行を格納する部分 (ディスク上) に分けることです。 このパーティション分割は、手動で設計して実装します。 次のチュートリアルを参照してください。  
  
- [アプリケーション レベルのパーティション分割](../../relational-databases/in-memory-oltp/application-level-partitioning.md)  
- [メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン](../../relational-databases/in-memory-oltp/application-pattern-for-partitioning-memory-optimized-tables.md)  
  
  
<a name="trade-offs-of-native-procs-38p"></a>  
  
### <a name="trade-offs-of-native-procs"></a>ネイティブ プロシージャのトレードオフ  
  
  
- ネイティブ コンパイル ストアド プロシージャは、ディスク ベース テーブルにアクセスできません。 ネイティブ プロシージャは、メモリ最適化テーブルにのみアクセスできます。  
- サーバーまたはデータベースがオンラインに戻った後、初めてネイティブ プロシージャを実行するときは、そのネイティブ プロシージャを一度再コンパイルする必要があります。 そのため、ネイティブ プロシージャが実行するまでに遅延が発生します。  
  
  
<a name="advanced-considerations-for-memory-optimized-tables-39n"></a>  
  
## <a name="advanced-considerations-for-memory-optimized-tables"></a>メモリ最適化テーブルに関する高度な考慮事項  
  
  
[メモリ最適化テーブルのインデックス](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md) は、従来のディスク上のテーブルのインデックスとはいくつかの点が異なります。  
  
- [ハッシュ インデックス](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) は、メモリ最適化テーブルでのみ使用できます。  
  
  
計画したメモリ最適化テーブルとインデックスのための十分なアクティブ メモリがあることを確認する必要があります。 次のチュートリアルを参照してください。  
  
- [メモリ最適化オブジェクト用ストレージの作成と管理](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
メモリ最適化テーブルは DURABILITY = SCHEMA_ONLY で宣言できます。  
  
- この構文は、データベースがオフラインになったときにメモリ最適化テーブルからすべてのデータを破棄するようシステムに指示します。 テーブル定義のみが保持されます。  
- データベースがオンラインに復帰すると、メモリ最適化テーブルがアクティブ メモリに読み込まれ、データは空になります。  
- 数千の行が含まれている場合は、tempdb の [#temporary テーブルよりも](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md) SCHEMA_ONLY テーブルの方が適していることがあります。  
  
  
テーブル変数をメモリ最適化として宣言することもできます。 次のチュートリアルを参照してください。  
  
- [メモリ最適化を使用した一時テーブルとテーブル変数の高速化](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)  
  
  
  
<a name="advanced-considerations-for-natively-compiled-modules-40k"></a>  
  
## <a name="advanced-considerations-for-natively-compiled-modules"></a>ネイティブ コンパイル モジュールに関する高度な考慮事項  
  
  
Transact-SQL で使用可能なネイティブ コンパイル モジュールの種類:  
  
- ネイティブ コンパイル ストアド プロシージャ (ネイティブ プロシージャ)。  
- スカラーのネイティブ コンパイル [ユーザー定義関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)。  
- ネイティブ コンパイル トリガー (ネイティブ トリガー)。  
  - メモリ最適化テーブルでは、ネイティブ コンパイル トリガーのみが許可されます。  
- ネイティブ コンパイル [テーブル値関数](../../relational-databases/user-defined-functions/create-user-defined-functions-database-engine.md)。  
  - [Improving temp table and table variable performance using memory optimization](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/21/improving-temp-table-and-table-variable-performance-using-memory-optimization/)  
  
  
ネイティブ コンパイルのユーザー定義関数 (UDF) は、解釈された UDF よりも高速で実行されます。 UDF に関するいくつかの考慮事項を以下に示します。  
  
- T-SQL SELECT で UDF を使用する場合は、返される行ごとに常に 1 回 UDF が呼び出されます。  
  - UDF はインラインで実行されることはなく、常に呼び出されます。  
  - コンパイル済みであるかどうかは、すべての UDF で繰り返される呼び出しのオーバーヘッドに比べると、あまり重要ではありません。  
  - それでも、UDF 呼び出しのオーバーヘッドは、多くの場合、実用レベルでは許容可能です。  
  
ネイティブ UDF のパフォーマンスに関するテスト データと説明については、以下を参照してください。  
  
  - [Soften the RBAR impact with Native Compiled UDFs in SQL Server 2016](https://blogs.msdn.microsoft.com/sqlcat/2016/02/17/soften-the-rbar-impact-with-native-compiled-udfs-in-sql-server-2016/)  
  - [Gail Shaw によるブログ記事](http://sqlinthewild.co.za/index.php/2016/01/12/natively-compiled-user-defined-functions/)(2016 年 1 月投稿)。  
  
  
<a name="documentation-guide-for-memory-optimized-tables-41z"></a>  
  
## <a name="documentation-guide-for-memory-optimized-tables"></a>メモリ最適化テーブルのドキュメント ガイド  
  
  
メモリ最適化テーブルの特別な考慮事項について説明するその他の資料へのリンクを示します。  
  
- [インメモリ OLTP への移行](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  - [テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)  
  - SQL Server Management Studio のトランザクション パフォーマンス分析レポートは、インメモリ OLTP によってデータベース アプリケーションのパフォーマンスが向上するかどうかを評価するために役立ちます。  
  - [メモリ最適化アドバイザー](../../relational-databases/in-memory-oltp/memory-optimization-advisor.md) を使用すると、ディスク ベース データベース テーブルをインメモリ OLTP に簡単に移行できます。   
- [メモリ最適化テーブルのバックアップ、復元、復旧](http://msdn.microsoft.com/library/3f083347-0fbb-4b19-a6fb-1818d545e281)  
  - メモリ最適化テーブルで使用されるストレージはメモリ内にあるときのサイズを大きく上回ることがあり、データベースのバックアップのサイズに影響します。  
- [メモリ最適化テーブルでのトランザクション](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md)  
  - メモリ最適化テーブルでのトランザクションに関する、T-SQL の再試行ロジックの情報が含まれます。  
- [Transact-SQL によるインメモリ OLTP のサポート](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)  
  - メモリ最適化テーブルとネイティブ プロシージャでの T-SQL とデータ型のサポート状況を示します。  
- [Bind a Database with Memory-Optimized Tables to a Resource Pool](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)(メモリ最適化テーブルを持つデータベースのリソース プールへのバインド) - オプションの高度な考慮事項について説明しています。  
  
  
  
<a name="documentation-guide-for-native-procs-42b"></a>  
  
## <a name="documentation-guide-for-native-procs"></a>ネイティブ プロシージャのドキュメント ガイド  
  
  
  
<a name="related-links-43f"></a>  
  
## <a name="related-links"></a>関連リンク  
  
- 最初の記事: [インメモリ OLTP (インメモリ最適化)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
インメモリ OLTP を使用して実現できるパフォーマンスの向上を実証するためのコードを提供する記事は以下のとおりです。  
  
- 「[実証: インメモリ OLTP によるパフォーマンスの向上](../../relational-databases/in-memory-oltp/demonstration-performance-improvement-of-in-memory-oltp.md) 」には、大幅なパフォーマンス向上が望める小規模なデモが用意されています。  
- 「[Sample Database for In-Memory OLTP](../../relational-databases/in-memory-oltp/sample-database-for-in-memory-oltp.md) 」 (インメモリ OLTP のサンプル データベース) には、より大規模なデモが用意されています。  
  
  
  
\<!--  
  
e1328615-6b59-4473-8a8d-4f360f73187d、dn817827.aspx、「列ストアを使用したリアルタイム運用分析の概要」  
  
f98af4a5-4523-43b1-be8d-1b03c3217839、gg492088.aspx、「列ストア インデックス ガイド」  
  
14dddf81-b502-49dc-a6b6-d18b1ae32d2b、dn133165.aspx、「メモリ最適化テーブル」  
  
d5ed432c-10c5-4e4f-883c-ef4d1fa32366、dn133184.aspx、「ネイティブ コンパイル ストアド プロシージャ」  
  
14106cc9-816b-493a-bcb9-fe66a1cd4630、dn639109.aspx、「メモリ最適化ファイルグループ」  
  
f222b1d5-d2fa-4269-8294-4575a0e78636、dn465873.aspx、「メモリ最適化テーブルを持つデータベースのリソース プールへのバインド」  
  
86805eeb-6972-45d8-8369-16ededc535c7、dn511012.aspx、「メモリ最適化テーブルのインデックス」  
  
16ef63a4-367a-46ac-917d-9eebc81ab29b、dn133166.aspx、「メモリ最適化テーブルでのインデックス使用のガイドライン」  
  
e3f8009c-319d-4d7b-8993-828e55ccde11、dn246937.aspx、「インメモリ OLTP でサポートされていない Transact-SQL の構造」  
  
2cd07d26-a1f1-4034-8d6f-f196eed1b763、dn133169.aspx、「メモリ最適化テーブルでのトランザクション」  
注: mt668425.aspx 「メモリ最適化テーブルでのトランザクションの動作およびガイドライン」を参照 (直ちに置き換え)  
f2a35c37-4449-49ee-8bba-928028f1de66、dn169141.aspx、「メモリ最適化テーブルでのトランザクションの再試行ロジックのガイドライン」  
  
7a458b9c-3423-4e24-823d-99573544c877、dn465869.aspx、「メモリ使用量の監視とトラブルシューティング」  
  
5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8、dn282389.aspx、「メモリ最適化テーブルのメモリ必要量の推定」  
  
b0a248a4-4488-4cc8-89fc-46906a8c24a1、dn205318.aspx、「メモリ最適化テーブルのテーブルと行のサイズ」  
  
162d1392-39d2-4436-a4d9-ee5c47864c5a、dn296452.aspx、「アプリケーション レベルのパーティション分割」  
  
3f867763-a8e6-413a-b015-20e9672cc4d1、dn133171.aspx、「メモリ最適化テーブルのパーティション分割に関するアプリケーションのパターン」  
  
86805eeb-6972-45d8-8369-16ededc535c7、dn511012.aspx、「メモリ最適化テーブルのインデックス」  
  
d82f21fa-6be1-4723-a72e-f2526fafd1b6、dn465872.aspx、「メモリ最適化 OLTP のメモリ管理」  
  
622aabe6-95c7-42cc-8768-ac2e679c5089、dn133174.aspx、「メモリ最適化オブジェクト用ストレージの作成と管理」  
  
bd102e95-53e2-4da6-9b8b-0e4f02d286d3、dn535766.aspx、「メモリ最適化テーブル変数」、「メモリ最適化テーブルのテーブル変数」  
廃止。 代わりに、38512a22-7e63-436f-9c13-dde7cf5c2202、mt718711.aspx、「メモリ最適化を使用した一時テーブルとテーブル変数の高速化」を参照。  
  
  
f0d5dd10-73fd-4e05-9177-07f56552bdf7、ms191320.aspx、「ユーザー定義関数の作成 (データベース エンジン)」、「テーブル値関数」  
  
d2546e40-fdfc-414b-8196-76ed1f124bf5、dn935012.aspx、「インメモリ OLTP でのユーザー定義のスカラー関数」、「ユーザー定義のスカラー関数」  
  
405cdac5-a0d4-47a4-9180-82876b773b82、dn247639.aspx、「インメモリ OLTP への移行」  
  
3f083347-0fbb-4b19-a6fb-1818d545e281、dn624160.aspx、「メモリ最適化テーブルのバックアップ、復元、復旧」  
  
690b70b7-5be1-4014-af97-54e531997839、dn269114.aspx、「メモリ最適化テーブルの変更」  
  
  
b1cc7c30-1747-4c21-88ac-e95a5e58baac、dn133080.aspx、「インメモリ OLTP 向けの新規および更新されたプロパティ、システム ビュー、ストアド プロシージャ、待機の種類、DMV」  
より多くのメモリが使用されます。 と呼ばれています。 と呼ばれています。 と呼ばれています。 より多くのメモリが使用されます。  
参照: 「Transact-SQL によるインメモリ OLTP のサポート」  
  
  
c1ef96f1-290d-4952-8369-2f49f27afee2、dn205133.aspx、「テーブルまたはストアド プロシージャをインメモリ OLTP に移植する必要があるかどうかの確認」  
  
181989c2-9636-415a-bd1d-d304fc920b8a、dn284308.aspx、「メモリ最適化アドバイザー」  
  
55548cb2-77a8-4953-8b5a-f2778a4f13cf、dn452282.aspx、「ネイティブ コンパイル ストアド プロシージャのパフォーマンスの監視」  
  
d3898a47-2985-4a08-bc70-fd8331a01b7b、dn358355.aspx、「ネイティブ コンパイル アドバイザー」  
  
f43faad4-2182-4b43-a76a-0e3b405816d1、dn296678.aspx、「ネイティブ コンパイル ストアド プロシージャの移行に関する問題」  
  
e1d03d74-2572-4a55-afd6-7edf0bc28bdb、dn133186.aspx、「インメモリ OLTP (インメモリ最適化)」  
  
c6def45d-d2d4-4d24-8068-fab4cd94d8cc、dn530757.aspx、「実証: インメモリ OLTP によるパフォーマンスの向上」  
  
405cdac5-a0d4-47a4-9180-82876b773b82、dn247639.aspx、「インメモリ OLTP への移行」  
  
f76fbd84-df59-4404-806b-8ecb4497c9cc、bb522682.aspx、「ALTER DATABASE の SET オプション (Transact-SQL)」  
  
e6b34010-cf62-4f65-bbdf-117f291cde7b、dn452286.aspx、「ネイティブ コンパイル ストアド プロシージャの作成」  
  
df347f9b-b950-4e3a-85f4-b9f21735eae3、mt465764.aspx、「インメモリ OLTP のサンプル データベース」  
  
38512a22-7e63-436f-9c13-dde7cf5c2202、mt718711.aspx、「メモリ最適化を使用した一時テーブルとテーブル変数の高速化」  
  
38512a22-7e63-436f-9c13-dde7cf5c2202、mt718711.aspx、「メモリ最適化を使用した一時テーブルとテーブル変数の高速化」  
  
  
  
  
H1 # クイック スタート 1: トランザクション ワークロードを高速化するためのインメモリ テクノロジ  
{1c25a164-547d-43c4-8484-6b5ee3cbaf3a} (大文字)  
mt718711.aspx (MSDN)  
  
GeneMi , 2016-05-07  00:07am  
-->  
  
  
  


