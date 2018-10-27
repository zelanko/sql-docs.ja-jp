---
title: データベースの Analysis Services の Consistency Checker (DBCC) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5314c18f7626ee631d7d0b59ad8d9c004a33148b
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147867"
---
# <a name="database-consistency-checker-dbcc-for-analysis-services"></a>Analysis Services 用 database Consistency Checker (DBCC)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  DBCC には、Analysis Services インスタンスの多次元および表形式データベース向けに、オンデマンドのデータベース検証機能が用意されています。 SQL Server Management Studio (SSMS) の MDX または XMLA クエリ ウィンドウで DBCC を実行し、SSMS の SQL Server Profiler または xEvent セッションで DBCC 出力をトレースできます。  
このコマンドはオブジェクト定義を受け取り、空の結果セットを返します。オブジェクトが破損している場合は詳細なエラー情報を返します。   この記事では、コマンドの実行方法、結果の解釈方法、発生した問題に対処する方法について説明します。  
  
 表形式データベースの場合、DBCC で実行する整合性チェックは、データベースの再読み込み、同期、復元のたびに自動実行される組み込みの検証と同等です。  対照的に、多次元データベースの整合性チェックは、オンデマンドで DBCC を実行した場合にのみ実行されます。  
  
 検証チェックの範囲は、モードによって異なります。表形式データベースの方が、チェック範囲が広くなります。  
 DBCC の作業負荷の特性も、サーバー モードによって異なります。 多次元データベースに対するチェック操作には、ディスクからのデータの読み込み、実際のインデックスと比較するための一時的なインデックスの構築、という処理が含まれます。そのため、完了までの時間が大幅に長くなります。  
  
 DBCC のコマンド構文には、チェックするデータベースの種類に固有のオブジェクト メタデータを使用します。  
  
-   多次元 + SQL Server 2016 以前の表形式 1100 または 1103 互換性レベルデータベースについては、 **cubeID**、 **measuregroupID**、 **partitionID**などの多次元モデリング構成体を参照してください。  
  
-   新しい表形式モデル データベースの互換性レベル 1200 以上から成る記述子のようなメタデータ**TableName**と**PartitionName**します。  
  
 データベースが SQL Server 2016 インスタンス上で実行されている限り、Analysis Services 用 DBCC はあらゆる互換性レベルのあらゆる Analysis Services データベースで実行されます。 各データベースの種類に合わせた適切なコマンド構文を使用する点にのみ気を付けてください。  
  
> [!NOTE]  
>  [DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md) を使い慣れている場合、Analysis Services の DBCC のスコープがかなり狭いことに気づくでしょう。 Analysis Services の DBCC は、データベース全体、または個々のオブジェクトでデータの破損が発生した場合にのみ、レポートする単一のコマンドです。 情報収集など、他のタスクも考慮している場合は、AMO PowerShell または XMLA スクリプトを代わりに使用してください。 詳細情報のリンクについては、「 [Monitor an Analysis Services Instance](../../analysis-services/instances/monitor-an-analysis-services-instance.md) 」を参照してください。  
  
## <a name="permission-requirements"></a>権限の要件  
 コマンドを実行するには、Analysis Services データベース管理者またはサーバー管理者 (サーバー ロールのメンバー) の権限が必要です。 手順については、「[Grant database permissions (Analysis Services)](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)」(データベース アクセス許可を付与する (Analysis Services)) または「[Grant server admin rights to an  Analysis Services instance](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)」(Analysis Services インスタンスにサーバー管理者権限を付与する) を参照してください。  
  
## <a name="command-syntax"></a>コマンドの構文 
 1200 の表形式データベースとより高い互換性レベル表形式メタデータ オブジェクト定義を使用します。 次の例は、SQL Server 2016 機能レベルで作成した表形式データベースの完全な DBCC 構文です。  
  
 2 つの構文の主な違いがない新しい XMLA 名前空間を含める\<オブジェクト > 要素、および no\<モデル > 要素 (あるデータベースごとに 1 つだけではまだモデル)。  
  
```  
<DBCC xmlns="http://schemas.microsoft.com/analysisservices/2014/engine">  
     <DatabaseID>MyTabular1200DB_7811b5d8-c407-4203-8793-12e16c3d1b9b</DatabaseID>  
     <TableName>FactSales</TableName>  
     <PartitionName>FactSales 4</PartitionName>  
</DBCC>  
```  
  
 表名、パーティション名など、下位のオブジェクトを省略して、スキーマ全体をチェックすることができます。  
  
 各オブジェクトのプロパティ ページでは、Management Studio からオブジェクト名と DatabaseID を取得できます。  
  
## <a name="command-syntax-for-multidimensional-and-tabular-110x-databases"></a>多次元および表形式の 110x データベースのコマンド構文  
 DBCC は、表形式の 1100 と 1103 データベースと同様に、多次元に同じ構文を使用しています。 データベース全体など、特定のデータ オブジェクトに対して DBCC を実行できます。 オブジェクト定義の詳細については、「[Object 要素 (XMLA)](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)」を参照してください。  
  
```  
<DBCC xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
     <Object>  
          <DatabaseID>AdventureWorksDW2014Multidimensional-EE</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
          <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
          <PartitionID>Internet_Sales_2006</PartitionID>  
     </Object>  
</DBCC>  
  
```  
  
 オブジェクト チェーンよりも上位のオブジェクトに対して DBCC を実行するには、不要な下位の ID 要素を削除します。  
  
```  
<DBCC xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
     <Object>  
          <DatabaseID>AdventureWorksDW2014Multidimensional-EE</DatabaseID>  
          <CubeID>Adventure Works</CubeID>  
     </Object>  
</DBCC>  
  
```  
  
 表形式 110x データベースの場合、オブジェクト定義構文は、Process コマンドの構文後にモデル化されます (特に、表をディメンションとメジャー グループにマッピングにマッピングする方法)。  
  
-   **CubeID** は、モデル ID ( **Model**) にマッピングされます。  
  
-   **MeasureGroupID** は、テーブル ID にマッピングされます。  
  
-   **PartitionID** は、パーティション ID にマッピングされます。  
  
## <a name="usage"></a>使用方法  
 SQL Server Management Studio では、MDX または XMLA クエリ ウィンドウを使用して DBCC を呼び出すことができます。 また、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Profiler または Analysis Services xEvents を使用して DBCC の出力を確認することができます。 SSAS DBCC メッセージは、Windows アプリケーション イベント ログまたは msmdsrv.log ファイルにレポートされないので、注意してください。  
  
 DBCC は、物理データの破損だけでなく、孤立したメンバーがセグメントに存在する場合に発生する論理データの破損もチェックします。 DBCC を実行する前に、データベースを処理する必要があります。 リモート、空、または未処理のパーティションはスキップされます。  
  
 コマンドは読み取りトランザクションで実行されるので、強制コミット タイムアウトで終了させることができます。 複数のパーティション チェックが並列実行されます。  
  
 場合によっては、最後のサービスが再起動した後に発生した破損エラーを取得するために、サービスの再起動が必要です。 サーバーに再接続するだけでは、変更を取得できません。  
  
### <a name="run-dbcc-commands-in-management-studio"></a>Management Studio で DBCC コマンドを実行する  
 アドホック クエリの場合、SQL Server Management Studio で MDX または XMLA クエリ ウィンドウを開きます。 この操作を行うには、データベースをクリックし、 **[新しいクエリ]** | **[XMLA]** の順にクリックしてコマンドを実行し、出力を読み取ります。  
  
 ![Management Studio での DBCC XML コマンド](../../analysis-services/instances/media/ssas-dbcc-ssms.gif "Management Studio での XML の DBCC コマンド")  
  
 問題が検出されなかった場合、[結果] タブには空の結果セットも表示されます (スクリーンショットを参照してください)。  
  
 [メッセージ] タブには詳細情報が表示されますが、小さいデータベースの場合、常に信頼できるとは限りません。 ステータス メッセージは省略されることがあるので、コマンドの完了が記述されていても、各オブジェクトのステータス チェック メッセージが含まれていない可能性があります。 一般的なメッセージ レポートは、以下のような内容です。  
  
 **キューブ検証チェック用に DBCC からレポートされるメッセージ**  
  
```  
Executing the query ...  
READS, 0  
READ_KB, 0  
WRITES, 0  
WRITE_KB, 0  
CPU_TIME_MS, 0  
ROWS_SCANNED, 0  
ROWS_RETURNED, 0  
  
<DBCC xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
<Object>  
<DatabaseID>AdventureWorksDW2014Multidimensional-EE</DatabaseID>  
<CubeID>Adventure Works</CubeID>  
</Object>  
</DBCC>  
Started checking segment indexes for the 'Internet_Sales_2011' partition.  
Started checking segment indexes for the 'Internet_Sales_2012' partition.  
Finished checking segment indexes for the 'Internet_Sales_2011' partition.  
Started checking segment indexes for the 'Internet_Sales_2013' partition.  
Finished checking segment indexes for the 'Internet_Sales_2012' partition.  
Started checking segment indexes for the 'Internet_Sales_2014' partition.  
Started checking segment indexes for the 'Internet_Orders_2011' partition.  
Finished checking segment indexes for the 'Internet_Sales_2014' partition.  
Started checking segment indexes for the 'Internet_Orders_2012' partition.  
Started checking segment indexes for the 'Internet_Orders_2013' partition.  
Finished checking segment indexes for the 'Internet_Orders_2012' partition.  
...   
Run complete  
  
```  
  
 **初期バージョンの Analysis Services に対して DBCC を実行したときの出力**  
  
 DBCC は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスで実行されているデータベースでのみサポートされます。 古いシステムでコマンドを実行すると、このエラーが返されます。  
  
```  
Executing the query ...  
The DBCC element at line 7, column 87 (namespace http://schemas.microsoft.com/analysisservices/2003/engine) cannot appear under Envelope/Body/Execute/Command.  
Execution complete  
  
```  
  
### <a name="trace-dbcc-output-in-sql-server-profiler-2016"></a>SQL Server Profiler 2016 で DBCC の出力をトレースする  
 Profiler トレースで、Progress Reports イベント (Progress Report Begin、Progress Report Current、Progress Report End、Progress Report Error) を含む DBCC の出力を確認できます。  
  
1.  トレースを開始します。 SQL Server Profiler と Analysis Services を併用する方法のヘルプについては、「 [Use SQL Server Profiler to Monitor Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md) 」を参照してください。  
  
2.  **Command Begin** と **Command End** に加え、 **Progress Report** イベントのいずれかまたはすべてを選択します。  
  
3.  前のセクションで説明した構文を使用して、Management Studio の XMLA または MDX クエリ ウィンドウで DBCC コマンドを実行します。  
  
4.  SQL Server Profiler で、DBCC アクティビティは、DBCC のイベント サブクラスを持つ **Command** イベントで示されます。  
  
     ![ssas-dbcc-profiler-eventsubclass](../../analysis-services/instances/media/ssas-dbcc-profiler-eventsubclass.PNG "ssas-dbcc-profiler-eventsubclass")  
  
     イベント コード 32 は、DBCC の実行です。  
  
     イベント コード 64 は、個々のオブジェクトに対する DBCC 進行状況レポートです。  
  
     イベント コード 63 は、多次元オブジェクトのセグメント チェックです。  
  
     どちらのイベント サブクラスでも、DBCC で返されたメッセージの **TextData** 値を確認します。  
  
     ステータス メッセージの始まり"の整合性をチェック\<オブジェクト >"、"Started checking\<オブジェクト >"、または"Finished checking\<オブジェクト >"。  
  
    > [!NOTE]  
    >  CTP 3.0 では、オブジェクトは内部名で識別されます。 など、Categories 階層は、H$ カテゴリ - として互い\<objectID >。 内部名は、今後の CTP でユーザー フレンドリ名で置き換えられます。  
  
     エラー メッセージを以下に示します。  
  
### <a name="trace-dbcc-output-in-an-xevent-session-in-ssms"></a>SSMS の xEvent セッションで DBCC 出力をトレースする  
 拡張イベント セッションは、Profiler イベントまたは xEvents の両方を使用できます。 **Command** イベントと **Progress Report** イベントの追加に関するガイダンスについては、前のセクションを参照してください。  
  
1.  セッションを開始するには、データベースを右クリックし、**[管理]** >**[拡張イベント]** >  **[セッション]** > **[新しいセッション]** の順にクリックします。 詳細については、「  [Monitor Analysis Services with SQL Server Extended Events](../../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) 」を参照してください。  
  
2.  Profiler イベント カテゴリの **Progress Report** イベントのいずれかまたはすべて、または PureXevent カテゴリの **RequestProgress** イベントを選択します。  
  
3.  前のセクションで説明した構文を使用して、Management Studio の XMLA または MDX クエリ ウィンドウで DBCC コマンドを実行します。  
  
4.  SSMS で Sessions フォルダーを更新します。 セッション名を右クリックし、**[ライブ データの監視]** をクリックします。  
  
5.  DBCC から返されたメッセージの TextData 値を確認します。  TextData は、event フィールドのプロパティです。イベントから返されたステータスとエラー メッセージを示します。  
  
     ステータス メッセージの始まり"の整合性をチェック\<オブジェクト >"、"Started checking\<オブジェクト >"、または"Finished checking\<オブジェクト >"。  
  
     エラー メッセージを以下に示します。  
  
## <a name="reference-consistency-checks-and-errors-for-multidimensional-databases"></a>参照: 多次元データベースの整合性チェックとエラー  
 多次元データベースの場合、パターン インデックスのみが検証されます。  DBCC は、実行中に各パーティションの一時インデックスを構築し、ディスクに保存されたインデックスと比較します。  一時インデックスの構築には、ディスク上にあるパーティション データのすべてのデータを読み取ってから、比較のために一時インデックスをメモリに保持する必要があります。 追加のワークロードがあると、DBCC の実行中のディスク IO とメモリ消費量が大幅に増える可能性があります。  
  
 多次元インデックス破損の検出には、次のチェックが含まれます。 この表のエラーは、オブジェクト レベルのエラーが発生した場合に xEvent または Profiler トレースに出現します。  
  
||||  
|-|-|-|  
|**オブジェクト**|**DBCC チェックの説明**|**失敗時のエラー**|  
|パーティション インデックス|チェックセグメントの統計情報とインデックス。<br /><br /> 一部パーティション インデックスの各メンバーの ID を、ディスクに格納されているパーティションの統計情報と比較します。  ディスクに格納されているパーティション インデックスの統計情報の範囲外のデータ ID 値である一時インデックスにメンバーが見つかった場合、インデックスの統計情報は破損していると考えられます。|パーティション セグメント統計が破損しています。|  
|パーティション インデックス|メタデータを検証します。<br /><br /> 一時インデックスの各メンバーが、ディスクのセグメントのインデックス ヘッダー ファイルに含まれることを検証します。|パーティション セグメントが破損しています。|  
|パーティション インデックス|セグメントをスキャンして、物理的な破損を検索します。<br /><br /> 一時インデックスの各メンバーについて、ディスク上のインデックス ファイルを読み取り、インデックス レコードのサイズが一致することを検証し、同じデータ ページが、現在のメンバーと同じレコードを持っているというフラグが付けられていることを検証します。|パーティション セグメントが破損しています。|  
  
## <a name="reference-consistency-checks-and-errors-for-tabular-databases"></a>参照: 表形式データベースの整合性チェックとエラー  
 次の表は、表形式オブジェクトで実行されるすべての整合性チェックと、チェックの結果が破損だった場合に発生するエラーの一覧です。 この表のエラーは、オブジェクト レベルのエラーが発生した場合に xEvent または Profiler トレースに出現します。  
  
||||  
|-|-|-|  
|**オブジェクト**|**DBCC チェックの説明**|**失敗時のエラー**|  
|[データベース]|データベース内のテーブル数をチェックします。  0 未満の値は破損を示します。|格納層が破損しています。 '%{parent/}' データベースのテーブルのコレクションが破損しています。|  
|[データベース]|参照整合性の追跡のために使用された内部構造をチェックし、サイズが正しくない場合にエラーをスローします。|データベース ファイルが整合性チェックに合格しませんでした。|  
|テーブル|テーブルが Dimension テーブルか Fact テーブルかを決定するために使用される内部値をチェックします。  既知の範囲を外れる値は、破損していることを示します。|テーブル統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|テーブル|テーブルのセグメント マップ内のパーティション数が、テーブルに定義されているパーティション数と同じかどうかをチェックします。|格納層が破損しています。 '%{parent/}' テーブルのパーティションのコレクションが破損しています。|  
|テーブル|Excel 2010 用 PowerPivot で作成またはインポートした表形式データベースで、パーティション数が 2 以上の場合、エラーが発生します。パーティションのサポートが以降のバージョンで追加され、それが破損を示すためです。|セグメント マップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|パーティション|各パーティションについて、データのセグメント数と、セグメントに含まれるデータの各セグメントのレコード数が、セグメントのインデックスに格納されている値と一致することを検証します。|セグメント マップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|パーティション|合計レコード、セグメント、またはセグメントごとのレコードの数が有効ではない場合 (0 未満)、またはセグメント数が、合計レコード数に基づいて必要と計算されたセグメント数と一致しない場合、エラーが発生します。|セグメント マップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|リレーションシップ|リレーションシップに関するデータの格納に使用される構造にレコードが含まれない場合、またはリレーションシップに使用されるテーブルの名前が空の場合は、エラーが発生します。|リレーションシップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|リレーションシップ|主テーブル、プライマリ列、外部テーブル、外部列の名前が設定され、リレーションシップに関係する列とテーブルにアクセスできることを検証します。<br /><br /> 関係する列の型が有効であり、主キーと外部キー値のインデックスが有効な参照構造になることを検証します。|リレーションシップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|Hieararchy|階層の並べ替え順序が認識可能な値ではない場合、エラーが発生します。|'%{hier/}' 階層のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|Hieararchy|階層に対して実行されるチェックは、使用する階層マッピング スキームの内部型に応じて変わります。<br /><br /> すべての階層について、処理済みの状態が正しいこと、データ ID から階層位置への変換に使用される階層ストアが存在することがチェックされます。<br /><br /> これらすべてのチェックに合格すると、階層構造全体につい、階層内の各位置が正しいメンバーを指していることを検証します。<br />いずれかのテストに失敗すると、エラーが発生します。|'%{hier/}' 階層のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|ユーザー定義の階層|階層レベル名が設定されていることを確認します。<br /><br /> 階層が処理された場合、内部階層データストアの形式が正しいことをチェックします。  内部階層ストアに、無効なデータ値が含まれていないことを検証します。<br /><br /> 階層が未処理とマークされている場合、その状態が古いデータ構造に適用され、階層のすべてのレベルは空とマークされていることを確認します。|'%{hier/}' 階層のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列に使用されているエンコーディングが既知の値に設定されていない場合、エラーが発生します。|列統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|メモリ内のエンジンによって列が圧縮されているかどうかを確認します。|列統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|既知の値について、列の圧縮の種類をチェックします。|列統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列 "tokenization" が既知の値に設定されていない場合、エラーが発生します。|列統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列データ ディクショナリに格納される id の範囲が、データ ディクショナリの値の数と一致しない場合、または許容範囲外の場合、エラーが発生します。|データ辞書のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列のデータ セグメント数が、属しているテーブルのデータ セグメント数と一致していることを確認します。|格納層が破損しています。 '%{parent/}' 列のセグメントのコレクションが破損しています。|  
|[列]|データ列のパーティション数が、列のデータ セグメント マップのパーティション数と一致することを確認します。|セグメント マップのチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列セグメントのレコード数が、その列セグメントのインデックスに格納されているレコード数と一致することを検証します。|格納層が破損しています。 '%{parent/}' 列のセグメントのコレクションが破損しています。|  
|[列]|列にセグメント統計がない場合、エラーが発生します。|セグメント統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|[列]|列に圧縮情報またはセグメント記憶域がない場合、エラーが発生します。|データベース ファイルが整合性チェックに合格しませんでした。|  
|[列]|列のセグメント統計が、最小データ ID、最大データ ID、個別の値数、行数、または NULL 値の存在に関する実際の列値と一致しない場合、エラーがレポートされます。|セグメント統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|ColumnSegment|最小データ ID または最大データ ID が、NULL のシステム予約値よりも小さい場合、列セグメント情報を破損とマークします。|セグメント統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|ColumnSegment|このセグメントの行がない場合、列の最小データ値と最大データ値を NULL のシステム予約値に設定する必要があります。  値が null でない場合、エラーが発生します。|セグメント統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|ColumnSegment|列に行があり、null 以外の値が少なくとも 1 つある場合、列の最小データ id と最大データ id が NULL のシステム予約値よりも大きいことをチェックします。|セグメント統計のチェック中に、データベース整合性チェック (DBCC) が失敗しました。|  
|Internal|ストア トークン化ヒントが設定され、ストアが処理されている場合は内部テーブルの有効なポインターがあることを検証します。  ストアが処理されていない場合、すべてのポインターが null であることを確認します。<br />null ではないポインターがある場合、汎用的な DBCC エラーが返されます。|データベース ファイルが整合性チェックに合格しませんでした。|  
|DBCC データベース|データベース スキーマにテーブルがないか、1 つ以上のテーブルにアクセスできない場合、エラーが発生します。|格納層が破損しています。 '%{parent/}' データベースのテーブルのコレクションが破損しています。|  
|DBCC データベース|テーブルが一時的とマークされているか、型が不明な場合、エラーが発生します。|無効なテーブルの種類が見つかりました。|  
|DBCC データベース|テーブルのリレーションシップ数が負の数の場合、またはいずれかのテーブルにリレーションシップが定義され、対応するリレーションシップ構造が見つからない場合、エラーが発生します。|格納層が破損しています。 '%{parent/}' テーブルのリレーションシップのコレクションが破損しています。|  
|DBCC データベース|データベースの互換性レベルが 1050 (SQL Server 2008 R2/PowerPivot v1.0) で、リレーションシップ数がモデル内のテーブル数を超える場合、データベースを破損とマークします。|データベース ファイルが整合性チェックに合格しませんでした。|  
|DBCC テーブル|テーブルの検証時に、列数が 0 未満かどうかをチェックし、true の場合はエラーが発生します。  テーブルの列の列ストアが NULL の場合にもエラーが発生します。|格納層が破損しています。 '%{parent/}' テーブルの列のコレクションが破損しています。|  
|DBCC パーティション|検証対象のパーティションが属するテーブルをチェックします。テーブルの列数が 0 未満の場合、そのテーブルの Columns コレクションが破損していることを示します。 テーブルの列の列ストアが NULL の場合にもエラーが発生します。|格納層が破損しています。 '%{parent/}' テーブルの列のコレクションが破損しています。|  
|DBCC パーティション|選択したパーティションについて各列をループし、パーティションの各セグメントに、列セグメント構造への有効なリンクがあることをチェックします。  セグメントに NULL のリンクがある場合、パーティションは破損していると見なされます。|格納層が破損しています。 '%{parent/}' 列のセグメントのコレクションが破損しています。|  
|[列]|列の型が有効ではない場合、エラーを返します。|無効なセグメントの種類が見つかりました。|  
|[列]|列のセグメント数について、列に負の数がある場合、またはセグメントの列セグメント構造のポインターに NULL リンクがある場合、エラーを返します。|格納層が破損しています。 '%{parent/}' 列のセグメントのコレクションが破損しています。|  
|DBCC コマンド|DBCC コマンドは、DBCC 処理の進行中に複数のステータス メッセージをレポートします。  オブジェクトのデータベース、テーブル、または列の名前を含める処理を開始する前、各オブジェクトのチェックが完了した後に、ステータス メッセージがレポートされます。|整合性をチェック、 \<objectname > \<objecttype >。 フェーズ: 確認前処理。<br /><br /> 整合性をチェック、 \<objectname > \<objecttype >。 フェーズ: 確認後処理。|  
  
## <a name="common-resolutions-for-error-conditions"></a>エラー条件の一般的な解決方法  
 次のエラーが SQL Server Management Studio または msmdsrv.log ファイルに表示されます。 このエラーは、1 つ以上のチェックが合格しなかった場合に発生します。 エラーによっては、オブジェクトを再処理する、ソリューションを削除して再配置する、またはデータベースを復元するという解決策が推奨されます。  
  
|[エラー]|問題点|解決策|  
|-----------|-----------|----------------|  
|**メタデータ マネージャーのエラー**<br /><br /> オブジェクト参照 '\<objectID >' が無効です。 オブジェクト参照がメタデータ クラス階層の構造と一致しません。|コマンドの形式が正しくない|コマンドの構文を確認します。 最も高い可能性として、1 つ以上の親オブジェクトを指定せず、下位のオブジェクトを含めました。|  
|**メタデータ マネージャーのエラー**<br /><br /> いずれか、\<オブジェクト > の ID を持つ '\<objectID >' に存在しません、 \<parentobject > の ID を持つ'\<parentobjectID >'、か、ユーザーに、オブジェクトへのアクセス許可がありません。|インデックスの破損 (多次元)|オブジェクトと依存するすべてのオブジェクトを再処理します。|  
|**パーティションの整合性チェック中に発生したエラー**<br /><br /> 整合性をチェック中にエラーが発生しました、\<パーティション名 > のパーティション、\<メジャー グループ名 > のメジャー グループ、\<キューブ名 > からキューブ、\<データベース名 > データベース。 破損を修復するには、パーティションまたはインデックスを再処理してください。|インデックスの破損 (多次元)|オブジェクトと依存するすべてのオブジェクトを再処理します。|  
|**パーティション セグメント統計の破損**|インデックスの破損 (多次元)|オブジェクトと依存するすべてのオブジェクトを再処理します。|  
|**パーティション セグメントの破損**|メタデータの破損 (多次元または表形式)|プロジェクトを削除してから再配置するか、バックアップから復元して再処理します。<br /><br /> 手順については、ブログの投稿「 [How to handle corruption in Analysis Services database](http://blogs.msdn.com/b/karang/archive/2010/08/11/how-to-deal-with-corruption-in-analysis-services.aspx) 」(Analysis Services データベースで破損を処理する方法) を参照してください。|  
|**テーブル メタデータの破損**<br /><br /> テーブル\<テーブル名 > メタデータ ファイルが破損しています。 メイン テーブルが DataFileList ノードに見つかりません。|メタデータの破損 (表形式のみ)|プロジェクトを削除してから再配置するか、バックアップから復元して再処理します。<br /><br /> 手順については、ブログの投稿「 [How to handle corruption in Analysis Services database](http://blogs.msdn.com/b/karang/archive/2010/08/11/how-to-deal-with-corruption-in-analysis-services.aspx) 」(Analysis Services データベースで破損を処理する方法) を参照してください。|  
|**格納層の破損**<br /><br /> ストレージ層の破損: コレクションの\<型名 > で\<親名 >\<親型 > が破損しています。|メタデータの破損 (表形式のみ)|プロジェクトを削除してから再配置するか、バックアップから復元して再処理します。<br /><br /> 手順については、ブログの投稿「 [How to handle corruption in Analysis Services database](http://blogs.msdn.com/b/karang/archive/2010/08/11/how-to-deal-with-corruption-in-analysis-services.aspx) 」(Analysis Services データベースで破損を処理する方法) を参照してください。|  
|**システム テーブルが見つからない**<br /><br /> システム テーブル\<テーブル名 > がありません。|オブジェクトの破損 (表形式のみ)|オブジェクトと依存するすべてのオブジェクトを再処理します。|  
|**テーブルの統計情報の破損**<br /><br /> システム テーブルの統計情報\<テーブル名 > がありません。|メタデータの破損 (表形式のみ)|プロジェクトを削除してから再配置するか、バックアップから復元して再処理します。<br /><br /> 手順については、ブログの投稿「 [How to handle corruption in Analysis Services database](http://blogs.msdn.com/b/karang/archive/2010/08/11/how-to-deal-with-corruption-in-analysis-services.aspx) 」(Analysis Services データベースで破損を処理する方法) を参照してください。|  
  
## <a name="disable-automatic-consistency-checks-on-database-load-operations-through--the-msmdsrvini-configuration-file"></a>msmdsrv.ini 構成ファイルによって、データベースの読み込み操作時に自動整合性チェックを無効にします。  
 推奨されない処理ですが、データベースの読み込みイベント時に自動的に実行される組み込みのデータベース整合性チェックを無効にすることができます (表形式データベースのみ)。 無効にするには、msmdsrv.ini ファイルで構成設定を変更する必要があります。  
  
```  
<ConfigurationSettings>  
     <Vertipaq />  
          <DisableConsistencyChecks />  
```  
  
 この設定は構成ファイルに存在しないので、手動で追加する必要があります。  
  
 有効な値は次のとおりです。  
  
-   **-2** (既定値): DBCC は有効です。 サーバーが高度な確実性でエラーを論理的に解決できる場合、修正は自動的に適用されます。 それ以外の場合、エラーがログに記録されます。  
  
-   **-1** : DBCC は部分的に有効です。 RESTORE の場合、およびトランザクションの最後にデータベースの状態をチェックするコミット前検証について、有効です。  
  
-   **0** : DBCC は部分的に有効です。 データベースの整合性チェックは、RESTORE、IMAGELOAD、LOCALCUBELOAD、ATTACH  
         操作中に実行されます。  
  
-   **1** : DBCC は無効です。 データ整合性チェックは無効ですが、逆シリアル化チェックは行われます。  
  
> [!NOTE]  
>  オンデマンドでコマンドを実行する場合、この設定は DBCC に影響がありません。  
  
## <a name="see-also"></a>参照  
 [データベース、テーブル、またはパーティションの処理 (Analysis Services)](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)   
 [多次元モデルの処理 (Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Monitor an Analysis Services Instance](../../analysis-services/instances/monitor-an-analysis-services-instance.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)  
  
  
