---
title: "基数推定 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 10/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e6ef57f8467e87b97024fc08b4916ac4f8e7752b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="cardinality-estimation-sql-server"></a>基数推定 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  
この記事では、SQL システムに最適な基数推定 (CE) 構成を評価し選択する方法を示しています。 最も正確なので、ほとんどのシステムで最新の CE のメリットを享受できます。 CE はクエリが返す可能性のある行の数を予測します。 クエリ オプティマイザーは基数予測を使用して、最適なクエリ プランを生成します。 通常は、正確な CE を使用するほど、より最適なクエリ プランが得られます。  
  
アプリケーション システムには、新しい CE が原因で低速のプランに変更された重要なクエリが含まれている可能性があります。 そのようなクエリは、次のいずれかのようになります。  
  
- OLTP クエリ。頻繁に実行され、その複数のインスタンスがしばしば同時に実行されます。  
- SELECT。OLTP 営業時間中に実行される大量の集計と一緒に実行されます。  
  
新規の CE で低速で実行するクエリを識別するための手法があります。 そして、パフォーマンスの問題に対処する方法のオプションもあります。  
  
  
## <a name="versions-of-the-ce"></a>CE のバージョン  
  
 1998 年には、CE の主要な更新プログラムは、互換性レベルが 70 の Microsoft SQL Server 7.0 の一部でした。 以降の更新プログラムは、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 (互換性レベルが 120 と 130) に含まれていました。 レベル 120 と 130 の CE 更新プログラムには、最新のデータ ウェアハウスのワークロードと OLTP (オンライン トランザクション処理) で適正に機能する前提条件とアルゴリズムが組み込まれています。  
  
 **互換性レベル:** [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)に次の Transact-SQL コードを使用して、データベースが特定のレベルであることを確認します。  

```tsql  
SELECT ServerProperty('ProductVersion');  
go  
  
ALTER DATABASE <yourDatabase>  
    SET COMPATIBILITY_LEVEL = 130;  
go  
  
SELECT    d.name, d.compatibility_level  
    FROM  sys.databases AS d  
    WHERE d.name = 'yourDatabase';  
go  
```  
  
 互換性レベルが 120 に設定されている SQL Server データベースの場合、トレース フラグ 9481 をアクティブにすると、システムは強制的にレベル 70 の CE を使用します。  
  
 **レガシ CE:** 互換性レベルが 130 に設定されている SQL Server データベースの場合、 [スコープ構成](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) に関する次の Transact-SQL ステートメントを使用して、レベル 70 の CE をアクティブにすることができます。
  
```tsql  
ALTER DATABASE
    SCOPED CONFIGURATION  
        SET LEGACY_CARDINALITY_ESTIMATION = ON;  
go  
  
SELECT  name, value  
    FROM  sys.database_scoped_configurations  
    WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
```  
  
 **クエリ ストア:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 で開始されたクエリ ストアは、クエリのパフォーマンスを確認するための便利なツールです。  SQL Server Management studio (SSMS.exe) では、データベース ノードの下の **オブジェクト エクスプローラー** に、 **クエリ ストア** ノードが表示されます (クエリ ストアが ON の場合)。  
  
```tsql  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE = ON;  
go  
  
SELECT  
        q.actual_state_desc    AS [actual_state_desc-ofQueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
    FROM  
        sys.database_query_store_options  AS q;  
go  
  
ALTER DATABASE <yourDatabase>  
    SET QUERY_STORE CLEAR;  
```  
  
 *ヒント:* 最新リリースの [(SSMS.exe)](http://msdn.microsoft.com/library/mt238290.aspx)を毎月インストールすることをお勧めします。  
  
 CE の基数予測を追跡するための別のオプションは、 **query_optimizer_estimate_cardinality**という名前の拡張イベントを使用することです。  次の T-SQL コードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行します。 これは C:\Temp\ に .xel ファイルを書き込みます (ただし、パスを変更することができます)。 .xel ファイルを SSMS で開くと、ユーザー フレンドリな方法で詳細情報が表示されます。  
  
```tsql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
    ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
go  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
    ON SERVER  
    STATE = START;  --STOP;  
go  
```  
  
 Azure SQL Database 向けに調整された拡張イベントの詳細については、「 [SQL データベースの拡張イベント](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/)」を参照してください。  
  
  
## <a name="steps-to-assess-the-ce-version"></a>CE のバージョンを評価する手順  
  
 次に示す手順を使用して、最も重要なクエリの中に、最新の CE で適切に機能しないものがあるかどうかを評価できます。 一部の手順は、前のセクションで説明されたコード サンプルを実行すると実行されます。  
  
1.  SSMS を開きます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースが、利用できる最も高い互換性レベルに設定されていることを確認してください。  
  
2.  次の準備作業を実行します。  
  
    1.  SSMS を開きます。  
  
    2.  T-SQL を実行して、  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースが、利用できる最も高い互換性レベルに設定されていることを確認してください。  
  
    3.  データベースがその LEGACY_CARDINALITY_ESTIMATION 構成を無効にしたことを確認します。  
  
    4.  クエリ ストアをクリアします。 もちろん、クエリ ストアが ON であることを確認します。  
  
    5.  次のステートメントを実行します: \`SET NoCount OFF;`  
  
3.  次のステートメントを実行します: \`SET STATISTICS XML ON;`  
  
4.  重要なクエリを実行します。  
  
5.  **[メッセージ]** タブの結果ウィンドウで、影響を受けた行の実際の数を確認してください。  
  
6.  **[結果]** タブの結果ウィンドウで、XML 形式の統計情報を含むセルをダブルクリックします。 グラフィックのクエリ プランが表示されます。  
  
7.  グラフィックのクエリ プランで最初のボックスを右クリックし、 **[プロパティ]**をクリックします。  
  
8.  別の構成と後で比較するために、次のプロパティの値を記録してください:  
  
    -   **CardinalityEstimationModelVersion**。  
  
    -   **推定される行の数**。  
  
    -   **I/O の推定コスト**と、行数の予測ではなく、実際のパフォーマンスを含む *推定* プロパティ。  
  
    -   **論理操作** と **物理操作**。 *並列処理* は有効な値です。  
  
    -   **実際の実行モード**。 *バッチ* は、 *行*より適切で、有効な値です。  
  
9. 行の推定数と行の実際の数とを比較します。 CE は 1% (前後)、または 10% 程度、不正確ですか?  
  
10. 次を実行します: \`SET STATISTICS XML OFF;`  
  
11. T-SQL を実行して、データベースの互換性レベルを 1 レベルずつ下げます (例: 130 から 120 に下げる)。  
  
12. すべての非準備ステップを再実行します。  
  
13. 2 つの実行からの CE プロパティ値を比較します。  
  
    - 最新の CE での不正確さの割合は、以前の CE での不正確さの割合より小さいですか?  
  
14. 最後に、2 つの実行からのさまざまなパフォーマンス プロパティ値を比較します。  
  
    -   クエリは 2 つの異なる CE 見積もりでの異なるプランを使用しましたか?  
  
    -   最新の CE でのクエリ実行速度は低速でしたか?  
  
    -   古い CE で別のプランを使用してクエリの動作が向上するのでない限り、恐らく最新の CE を使用したいと思われるでしょう。  
  
    -   ただし、クエリが古い CE でより高速なプランで実行している場合は、システムで高速なプランを強制的に使用し、CE を無視することを検討してください。 これが、1 つの例外で高速のプランを維持しながらも、すべてに対して最新の CE を保持できる方法です。  
  
## <a name="how-to-activate-the-best-query-plan"></a>最適なクエリ プランをアクティブにする方法  
  
新規の CE で低速のクエリ プランが、クエリで生成されるとします。 高速なプランをアクティブにするいくつかのオプションを次に示します。  
  
データベース全体に対して、互換性レベルを利用可能な最新の値より低い値に設定できます。  
  
- これにより、古い CE がアクティブになりますが、すべてのクエリが、正確性が低下した以前の CE の影響を受けることになります。  
  
- さらに、古いレベルでは、クエリ オプティマイザーでの優れた機能強化も失われます。  
  
LEGACY_CARDINALITY_ESTIMATION を使用すると、クエリ オプティマイザーの機能強化を維持したまま、データベース全体が古い CE を使用するようにできます。  
  
最適のコントロールとしては、SQL システムがテスト中に古い CE で生成されたプランを *強制的に* 使用するようにできます。 優先するプランを *固定* した後、データベース全体が最新の互換性レベルと CE を使用するように設定できます。 このオプションについて、次に詳しく説明します。  
  
### <a name="how-to-force-a-particular-query-plan"></a>特定のクエリ プランを強制的に実行する方法  
  
クエリ ストアでは、特定のクエリ プランを使用するようシステムを強制するさまざまな方法を示します。  
  
- **sp_query_store_force_plan**を実行します。  
  
- SSMS で、 **[クエリ ストア]** ノードを展開し、 **[トップ リソース コンシューマー ノード]**を右クリックし、 **[トップ リソース コンシューマー ノードの表示]**をクリックします。 **[プランの強制]** と **[プランを強制しない]**というラベルのボタンが表示されます。  
  
 クエリ ストアの詳細については、「 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)」を参照してください。  
  
  
## <a name="descriptions-of-advance-ce"></a>アドバンス CE の説明  
  
このセクションでは、最近のリリースで CE に実装された拡張機能からメリットを享受できるクエリの例について説明します。 これは、ユーザー側で特定の操作が要求されていない背景情報です。  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>例 A。CE は、統計が最後に収集されたときよりも、最大値が高くなる可能性があることを理解しています  
  
たとえば、OrderTable の統計が最後に収集されたのが 2016-04-30 で、OrderAddedDate の最大値が 2016-04-30 であるとします。 互換性レベル 120 (およびより高いレベル） の CE は、 *昇順* データを持つ OrderTable の列が、統計によって記録された最大値よりも大きい値を持つ可能性があることを理解しています。 これを理解すると、次のような SQL SELECT のクエリ プランの機能を改善できます。  
  
```tsql  
SELECT CustomerId, OrderAddedDate  
    FROM OrderTable  
    WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>例 B。CE は、同じテーブル上のフィルターにかけられた述語が頻繁に関連付けられることを理解しています  
  
次の SELECT では、フィルターにかけられた述語が Make と Model に表示されます。 Honda が Civic を作っているので、Make が 'Honda' の場合、Model が 'Civic' の可能性があることをユーザーは直感的に理解します。  
  
レベル 120 の CE は、同じテーブルの 2 つの列、Make と Model の間に相関関係がある可能性があることを理解します。 CE はクエリで返される行数のより正確な見積もりを行い、クエリ オプティマイザーがより最適なプランを生成します。  
  
```tsql  
SELECT Model_Year, Purchase_Price  
    FROM dbo.Cars  
    WHERE  
        Make  = 'Honda'  AND  
        Model = 'Civic';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tables"></a>例 C。CE は異なるテーブルからフィルターにかけられた述語の間に、もはや相関関係がないと想定します  
  
最近のワークロードと実際のビジネス データに関する最新の調査によって、異なるテーブルからの述語フィルターは、通常互いに関連していないことが明らかになりました。 次のクエリでは、CE は s.type と r.date 間の相関関係がないと想定します。 そのため CE は、返される行数の推定値を低く指定します。  
  
```tsql  
SELECT s.ticket, s.customer, r.store  
    FROM  
                   dbo.Sales    AS s  
        CROSS JOIN dbo.Returns  AS r  
    WHERE  
        s.ticket = r.ticket  AND  
        s.type   = 'toy'     AND  
        r.date   = '2016-05-11';  
```  
  
  
## <a name="see-also"></a>参照  
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)  
  


