---
title: "SQL Server 2014 リリース ノート | Microsoft Docs"
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-server-2014
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4c4922-80b3-4be3-bf71-228247f97004
caps.latest.revision: 100
author: byham
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0ca391c25a462a5f30d6a9bc51b4541f77adfd48
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-2014-release-notes"></a>SQL Server 2014 リリース ノート
このリリース ノートでは、 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]のインストールやトラブルシューティングを行う前に知っておく必要がある、既知の問題について説明しています。  
  
## <a name="top"></a>目次  
[1.0 インストールの準備](#BeforeInstall)  
  
[2.0 製品ドキュメント](#ProdDoc)  
  
[3.0 データベース エンジン](#DBEngine)  
  
[4.0 Reporting Services](#SSRS)  
  
[5.0 Microsoft Azure Virtual Machines 上の SQL Server 2014](#AzureVM)  
  
[6.0 Analysis Services](#SSAS)  
  
[7.0 Data Quality Services](#DQS)  
  
[8.0 アップグレード アドバイザー](#UA)  
  
## <a name="BeforeInstall"></a>1.0 インストールの準備  
  
### <a name="11-limitations-and-restrictions-in-sql-server-2014-rtm"></a>1.1 SQL Server 2014 RTM の制限事項と制約事項  
  
#### <a name="111-general-limitations-and-restrictions"></a>1.1.1 一般的な制限事項と制約事項  
  
1.  Microsoft SQL Server 2014 CTP 1 から Microsoft SQL Server 2014 RTM へのアップグレードはサポートされていません。  
  
2.  SQL Server 2014 CTP 1 と SQL Server 2014 RTM のサイド バイ サイド インストールはサポートされていません。  
  
3.  SQL Server 2014 RTM への SQL Server 2014 CTP 1 データベースのアタッチまたは復元はサポートされていません。  
  
**回避策:** ありません。  
  
#### <a name="12-considerations-for-upgrading-sql-server-2014-ctp-2-to-sql-server-2014-rtm-and-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2 SQL Server 2014 CTP 2 から SQL Server 2014 RTM へのアップグレード、および SQL Server 2014 RTM から SQL Server 2014 CTP 2 へのダウングレードに関する考慮事項  
  
#### <a name="121-upgrading-from-sql-server-2014-ctp-2-to-sql-server-rtm-is-fully-supported"></a>1.2.1 SQL Server 2014 CTP 2 から SQL Server RTM へのアップグレードを完全サポート  
具体的には、次のことを実行できます。  
  
1.  SQL Server 2014 RTM インスタンスに SQL Server 2014 CTP 2 データベースをアタッチ。  
  
2.  SQL Server 2014 CTP 2 で作成したデータベース バックアップを SQL Server 2014 RTM インスタンスに復元。  
  
3.  SQL Server 2014 RTM へのインプレース アップグレード。  
  
4.  SQL Server 2014 RTM へのローリング アップグレード。 ローリング アップグレードを開始する前に、手動フェールオーバー モードに切り替える必要があります。 詳細については、「 [ダウンタイムとデータ損失を最小限に抑えた可用性グループ サーバーのアップグレードおよび更新](http://msdn.microsoft.com/library/dn178483.aspx) 」を参照してください。  
  
5.  SQL Server 2014 CTP 2 にインストールされたトランザクション パフォーマンス コレクション セットによって収集されたデータを、SQL Server 2014 RTM の SQL Server Management Studio で表示することはできません。その逆も同じです。 SQL Server 2014 CTP 2 にインストールされたコレクション セットによって収集されたデータを表示するには、SQL Server 2014 CTP 2 の SQL Server Management Studio を使用します。また、SQL Server 2014 RTM にインストールされたコレクション セットによって収集されたデータを表示するには、SQL Server 2014 RTM の SQL Server Management Studio を使用します。  
  
### <a name="122-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2.2 SQL Server 2014 RTM から SQL Server 2014 CTP 2 へのダウングレード  
これはサポートされていません。  
  
**回避策:** ダウングレードを実行するための回避策はありません。 SQL Server 2014 RTM にアップグレードする前に、データベースをバックアップすることをお勧めします。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="13-incorrect-version-of-streaminsight-client-on-sql-server-2014-mediaisocab"></a>1.3 SQL Server 2014 メディア/ISO/CAB 上の不正なバージョンの StreamInsight クライアント  
SQL Server メディア/ISO/CAB 上に間違ったバージョンの StreamInsight.msi および StreamInsightClient.msi があります (パスは StreamInsight\\\<Architecture\>\\\<Language ID\>)。  
  
**回避策:** [SQL Server 2014 用 Feature Pack のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=306709)から正しいバージョンをダウンロードしてインストールしてください。  
  
## <a name="ProdDoc"></a>2.0 製品ドキュメント  
  
### <a name="21-report-builder-content-is-not-available-in-some-languages"></a>2.1 レポート ビルダーのコンテンツがいくつかの言語で使用できない  
**問題点:** レポート ビルダーのコンテンツは、次の言語では使用できません。  
  
-   ギリシャ語 (el-GR)  
  
-   ノルウェー語 (ボークモール) (nb-NO)  
  
-   フィンランド語 (fi FI)  
  
-   デンマーク語 (da DK)  
  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]では、このコンテンツは製品に付属する CHM ファイルから入手でき、上記の言語でも使用可能でした。 現在 CHM ファイルは製品に付属しておらず、レポート ビルダーのコンテンツは MSDN でのみ使用できます。 MSDN では、これらの言語はサポートされていません。 レポート ビルダーは TechNet からも削除され、上記のサポートされる言語では使用できなくなりました。  
  
**回避策:** ありません。  
  
### <a name="22-powerpivot-content-is-not-available-in-some-languages"></a>2.2 PowerPivot のコンテンツがいくつかの言語で使用できない  
**問題点:** Power Pivot のコンテンツは、次の言語では使用できません。  
  
-   ギリシャ語 (el-GR)  
  
-   ノルウェー語 (ボークモール) (nb-NO)  
  
-   フィンランド語 (fi FI)  
  
-   デンマーク語 (da DK)  
  
-   チェコ語 (cs-CZ)  
  
-   ハンガリー語 (hu-HU)  
  
-   オランダ語 (オランダ) (nl-NL)  
  
-   ポーランド語 (pl-PL)  
  
-   スウェーデン語 (sv-SE)  
  
-   トルコ語 (tr-TR)  
  
-   ポルトガル語 (ポルトガル) (pt-PT)  
  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]では、このコンテンツは TechNet から入手でき、上記の言語でも使用可能でした。 このコンテンツは TechNet から削除され、上記のサポートされる言語では使用できなくなりました。  
  
**回避策:** ありません。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="DBEngine"></a>3.0 データベース エンジン  
  
### <a name="31-changes-made-for-standard-edition-in-sql-server-2014-rtm"></a>3.1 SQL Server 2014 RTM の Standard Edition に加えられた変更  
SQL Server 2014 Standard では、次の点が変更されています。  
  
-   バッファー プール拡張機能により、構成済みのメモリの最大 4 倍のサイズを使用できます。  
  
-   最大メモリは 64 GB から 128 GB に拡大されました。  
  
### <a name="32-in-memory-oltp-issues"></a>3.2 インメモリ OLTP 問題  
  
#### <a name="321-memory-optimization-advisor-flags-default-constraints-as-incompatible"></a>3.2.1 メモリ最適化アドバイザーは既定の制約に対して互換性なしのフラグを設定  
**問題点:** SQL Server Management Studio のメモリ最適化アドバイザーは、すべての既定の制約に対して、互換性なしというフラグを設定します。 既定の制約すべてが、メモリ最適化テーブルでサポートされているわけではありません。アドバイザーは、既定の制約のうち、サポートされている種類とサポートされていない種類を区別しません。 サポートされている既定の制約として、すべての定数や、ネイティブ コンパイル ストアド プロシージャ内でサポートされている式と組み込み関数を挙げることができます。 ネイティブ コンパイル ストアド プロシージャでサポートされる関数の一覧については、「 [ネイティブ コンパイル ストアド プロシージャでサポートされる構造](http://msdn.microsoft.com/library/dn452279(v=sql.120).aspx)」を参照してください。  
  
**回避策:** 障害となる問題を識別する目的でアドバイザーを使用する場合は、互換性のある既定の制約に関する表示を無視してください。 メモリ最適化アドバイザーを使用して、互換性のある既定の制約を含み、障害となる他の問題が存在しないテーブルを移行する場合は、次の手順を実行します:  
  
1.  テーブル定義から既定の制約を削除します。  
  
2.  アドバイザーを使用して、テーブル上で移行スクリプトを生成します。  
  
3.  移行スクリプトに、既定の制約を再度追加します。  
  
4.  移行スクリプトを実行します。  
  
#### <a name="322-informational-message-file-access-denied-incorrectly-reported-as-an-error-in-the-sql-server-2014-error-log"></a>3.2.2 情報メッセージ "ファイルのアクセスが拒否されました。" が、SQL Server 2014 のエラー ログに誤ってエラーとして報告される  
**問題点:** メモリ最適化テーブルを含むデータベースがあるサーバーを再起動すると、SQL Server 2014 のエラー ログに次の種類のエラー メッセージが出力されることがあります。  
  
```  
[ERROR]Unable to delete file C:\Program Files\Microsoft SQL   
Server\....old.dll. This error may be due to a previous failure to unload   
memory-optimized table DLLs.  
```  
  
実際は、このメッセージは情報提供だけを目的としており、ユーザー操作は不要です。  
  
**回避策:** ありません。 これは情報メッセージです。  
  
#### <a name="323-missing-index-details-incorrectly-report-included-columns-for-memory-optimized-table"></a>3.2.3 欠落インデックスの詳細で、メモリ最適化テーブルに対応する付加列が誤って報告される  
**問題点:** SQL Server 2014 がメモリ最適化テーブルに対するクエリで欠落インデックスを検出した場合は、SHOWPLAN_XML 内で欠落インデックスが報告され、sys.dm_db_missing_index_details などでも欠落インデックス DMV が報告されます。 場合によっては、欠落インデックスの詳細に、付加列が含まれています。 メモリ最適化テーブルのすべてのインデックスにはすべての列が暗黙的に含まれているため、メモリ最適化インデックスで付加列を明示的に指定することは許可されません。  
  
**回避策:** メモリ最適化テーブルのインデックスでは、INCLUDE 句を指定しないでください。  
  
#### <a name="324-missing-index-details-omit-missing-indexes-if-a-hash-index-exists-but-is-not-suitable-for-the-query"></a>3.2.4 ハッシュ インデックスが存在していてもクエリに適していない場合は、欠落インデックスの詳細で欠落インデックスが省略される  
**問題点:** クエリ内で参照されているメモリ最適化テーブルの列でハッシュ インデックスを使用しているが、クエリでインデックスを使用できない場合は、SQL Server 2014 で SHOWPLAN_XML 内や DMV sys.dm_db_missing_index_details 内の欠落インデックスが報告されない場合があります。  
  
特に、インデックス キー列のサブセットが関係する等値述語がクエリに含まれている場合や、インデックス キー列が関係する不等値述語がクエリに含まれている場合は、HASH インデックスをそのまま使用することはできず、クエリを効率的に実行するために別のインデックスが必要になります。  
  
**回避策:** ハッシュ インデックスを使用している場合は、クエリとクエリ プランを検討し、インデックス キーのサブセットに対する Index Seek 操作や、不等値述語に対する Index Seek 操作によってクエリに利点がもたらされるかどうかを判断します。 インデックス キーのサブセットに対するシークを実行する必要がある場合は、NONCLUSTERED インデックスを使用するか、シークする必要のある正確な列に対応する HASH インデックスを使用します。 不等値述語に対するシークを実行する必要がある場合は、HASH の代わりに NONCLUSTERED インデックスを使用します。  
  
#### <a name="325-failure-when-using-a-memory-optimized-table-and-memory-optimized-table-variable-in-the-same-query-if-the-database-option-readcommittedsnapshot-is-set-to-on"></a>3.2.5 データベース オプション READ_COMMITTED_SNAPSHOT を ON に設定した場合、メモリ最適化テーブルとメモリ最適化テーブル変数を同じクエリで使用したときにエラーが発生する  
**問題点:** データベース オプション READ_COMMITTED_SNAPSHOT を ON に設定し、ユーザー トランザクションのコンテキスト外にある同じステートメントで、メモリ最適化テーブルとメモリ最適化されたテーブル変数の両方にアクセスした場合、次のエラー メッセージが表示される可能性があります。  
  
```  
Msg 41359  
A query that accesses memory optimized tables using the READ COMMITTED  
isolation level, cannot access disk based tables when the database option  
READ_COMMITTED_SNAPSHOT is set to ON. Provide a supported isolation level  
for the memory optimized table using a table hint, such as WITH (SNAPSHOT).  
```  
  
**回避策:** テーブル変数と共にテーブル ヒント WITH (SNAPSHOT) を使用するか、データベース オプション MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT を ON に設定して、次のステートメントを使用します。  
  
```  
ALTER DATABASE CURRENT   
SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
```  
  
#### <a name="326-procedure-and-query-execution-statistics-for-natively-compiled-stored-procedures-record-worker-time-in-multiples-of-1000"></a>3.2.6 ネイティブ コンパイル ストアド プロシージャに関するプロシージャとクエリ実行の統計で、ワーカー時間が 1,000 の倍数で記録される  
**問題点:** sp_xtp_control_proc_exec_stats または sp_xtp_control_query_exec_stats を使用してネイティブ コンパイル ストアド プロシージャに対するプロシージャまたはクエリ実行の統計の収集を有効にした後、DMV sys.dm_exec_procedure_stats と sys.dm_exec_query_stats 内で、*_worker_time が 1,000 の倍数で報告されます。 ワーカー時間が 500 ミリ秒未満のクエリ実行では、worker_time として 0 が報告されます。  
  
**回避策:** ありません。 ネイティブ コンパイル ストアド プロシージャの実行時間が短いクエリに対応する実行統計 DMV 内で報告された worker_time を信頼しないでください。  
  
#### <a name="327-error-with-showplanxml-for-natively-compiled-stored-procedures-that-contain-long-expressions"></a>3.2.7 長い式を含むネイティブ コンパイル ストアド プロシージャに対応する SHOWPLAN_XML にエラーが出力される  
**問題点:** ネイティブ コンパイル ストアド プロシージャに長い式が含まれていて、そのプロシージャに対応する SET SHOWPLAN_XML を取得する状況で、T-SQL オプション SET SHOWPLAN_XML ON を使用する場合、または Management Studio で [推定実行プランの表示] オプションを使用する場合、次のエラーが発生する可能性があります。  
  
```  
Msg 41322. MAT/PIT export/import encountered a failure for memory  
optimized table or natively compiled stored procedure with object ID  
278292051 in database ID 6. The error code was  
0xc00cee81.  
```  
  
**回避策:** 2 つの回避策が推奨されます。  
  
1.  次の例のように、式にかっこを追加します。  
  
    次の表記の代わりに、  
  
    ```  
    SELECT @v0 + @v1 + @v2 + ... + @v199  
    ```  
  
    次のように記述します。  
  
    ```  
    SELECT((@v0 + ... + @v49) + (@v50 + ... + @v99)) + ((@v100 + ... + @v149) + (@v150 + ... + @v199))  
    ```  
  
2.  SHOWPLAN を対象にして、わずかに簡略化した式を使用する 2 番目のプロシージャを作成します。プランの全般的な形式は同じままにします。 たとえば、次の表記の代わりに、  
  
    ```  
    SELECT @v0 +@v1 +@v2 +...+@v199  
    ```  
  
    次のように記述します。  
  
    ```  
    SELECT @v0 +@v1  
    ```  
  
#### <a name="328-using-a-string-parameter-or-variable-with-datepart-and-related-functions-in-a-natively-compiled-stored-procedure-results-in-an-error"></a>3.2.8 ネイティブ コンパイル ストアド プロシージャ内にある DATEPART とそれに関連する関数で文字列パラメーターまたは文字列変数を使用するとエラーが発生する  
**問題点:** ネイティブ コンパイル ストアド プロシージャ内で組み込み関数 DATEPART、DAY、MONTH、YEAR と共に、(var)char または n(var)char のような文字列データ型のパラメーターまたは変数を使用すると、データ型 datetimeoffset がネイティブ コンパイル ストアド プロシージャ内でサポートされていないことを示すエラー メッセージが出力されます。  
  
**回避策:** 文字列パラメーターまたは文字列変数に対して、新しい変数型である datetime2 を割り当て、DATEPART、DAY、MONTH、または YEAR 関数を使用します。 例:  
  
```  
DECLARE @d datetime2 = @string  
DATEPART(weekday, @d)  
```  
  
#### <a name="329-native-compilation-advisor-flags-delete-from-clauses-incorrectly"></a>3.2.9 ネイティブ コンパイル アドバイザーが DELETE FROM 句に対して誤ってフラグを設定する  
**問題点:** ネイティブ コンパイル アドバイザーが、ストアド プロシージャ内の DELETE FROM 句に対して互換性なしのフラグを誤って設定します。  
  
**回避策:** ありません。  
  
### <a name="33-register-through-ssms-adds-dac-meta-data-with-mismatched-instance-ids"></a>3.3 SSMS を使用して登録を行うと、不一致のインスタンス ID を持つ DAC メタデータが追加される  
**問題点:** SQL Server Management Studio を使用してデータ層アプリケーション パッケージ (.dacpac) を登録または削除すると、sysdac* テーブルが正しく更新されず、データベースに対して dacpac 履歴のクエリを実行することができません。  sysdac_history_internal と sysdac_instances_internal の instance_id が一致せず、結合が許可されません。  
  
**回避策:** [データ層アプリケーション フレームワーク](https://www.microsoft.com/download/details.aspx?id=42295)の Feature Pack の再配布で、この問題点は修正されています。  更新プログラムを適用した後、すべての新しい履歴エントリは sysdac_instances_internal テーブル内の instance_id の一覧に含まれる値を使用します。  
  
instance_id の値の不一致という問題が既に発生している場合は、不一致の値を修正する唯一の方法は、MSDB データベースへ書き込む特権を持つユーザーとしてサーバーに接続し、instance_id の値を更新して一致させることです。  同じデータベースに対して登録イベントと登録解除イベントが複数発生していた場合は、時刻と日付を参照し、どのレコードが現在の instance_id の値と一致しているかを確認する必要があります。  
  
1.  SQL Server Management Studio で、MSDB に対する更新権限を持つログインを使用して、サーバーに接続します。  
  
2.  MSDB データベースを使用して、新しいクエリを開きます。  
  
3.  次のクエリを実行し、すべてのアクティブな dac インスタンスを表示します。  修正対象のインスタンスを見つけ、instance_id を書き留めます。  
  
    `select * from` sysdac_instances_internal  
  
4.  次のクエリを実行し、すべての履歴エントリを表示します。  
  
    `select * from` sysdac_history_internal  
  
5.  修正するインスタンスに対応する行を特定します。  
  
6.  (sysdac_instances_internal テーブルで) sysdac_history_internal.instance_id の値を、手順 3 で書き留めた値に更新します。  
  
    `update` sysdac_history_internal `set` instance_id = '\<手順 3 で書き留めた値\>' `where` \<更新しようとする行に一致する式\>  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="SSRS"></a>4.0 Reporting Services  
  
### <a name="41-the-sql-server-2012-reporting-services-native-mode-report-server-cannot-run-side-by-side-with-sql-server-2014-reporting-services-sharepoint-components"></a>4.1 SQL Server 2012 Reporting Services ネイティブ モード レポート サーバーを SQL Server 2014 Reporting Services SharePoint コンポーネントとサイド バイ サイドで実行できない  
**問題点:**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モードの Windows サービス SQL Server Reporting Services (ReportingServicesService.exe) の起動に失敗します。  
  
**回避策:**  [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint コンポーネントをアンインストールし、Microsoft SQL Server 2012 Reporting Services の Windows サービスを再起動します。  
  
**詳細情報:**  
  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モードは、次のいずれのものともサイド バイ サイドで実行することはできません。  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 製品用アドイン  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共有サービス  
  
サイド バイ サイド インストールでは、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モード Windows Service を起動することはできません。 次のようなエラー メッセージが Windows イベント ログに記録されます。  
  
```  
Log Name:   Application  
Source:          Report Server (<SQL instance ID>)  
Event ID:        117  
Task Category:   Startup/Shutdown  
Level:           Error  
Keywords:        Classic  
Description:     The report server database is an invalid version.  
  
Log Name:      Application  
Source:        Report Server (<SQL instance ID>)  
Event ID:      107  
Task Category: Management  
Level:         Error  
Keywords:      Classic  
Description:   Report Server (DENALI) cannot connect to the report server database.  
```  
  
詳細については、「 [SQL Server 2014 Reporting Services の役立つヒントおよびトラブルシューティング](http://go.microsoft.com/fwlink/?LinkID=391254)」を参照してください。  
  
### <a name="42-required-upgrade-order-for-multi-node-sharepoint-farm-to-sql-server-2014-reporting-services"></a>4.2 SQL Server 2014 Reporting Services を使用する複数ノードの SharePoint ファームで必要なアップグレードの順序  
**問題点:** SharePoint 製品用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインのすべてのインスタンスをアップグレードする前に、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共有サービスのインスタンスをアップグレードした場合は、複数ノード ファームでレポートを表示できなくなります。  
  
**回避策:** 複数ノードの SharePoint ファームで、次の手順を実行します。  
  
1.  最初に、SharePoint 製品用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインのすべてのインスタンスをアップグレードします。  
  
2.  次に、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共有サービスのすべてのインスタンスをアップグレードします。  
  
詳細については、「 [SQL Server 2014 Reporting Services の役立つヒントおよびトラブルシューティング](http://go.microsoft.com/fwlink/?LinkID=391254)」を参照してください。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="AzureVM"></a>5.0 Microsoft Azure Virtual Machines 上の SQL Server 2014 RTM  
  
### <a name="51-the-add-azure-replica-wizard-returns-an-error-when-configuring-an-availability-group-listener-in-windows-azure"></a>5.1 Windows Azure で可用性グループ リスナーを構成するときに Azure のレプリカ追加ウィザードでエラーが返される  
**問題点:** 可用性グループ にリスナーが存在する場合は、Windows Azure でリスナーを構成しようとしたときに、Azure のレプリカ追加ウィザードでエラーが返されます。  
  
Azure サブネットを含め、可用性グループのレプリカをホストしているすべてのサブネットで、可用性グループ リスナーに 1 つの IP アドレスを割り当てることが必要とされるのが原因です。  
  
**回避策:**  
  
1.  リスナーのページで、可用性グループ レプリカをホストする Azure サブネット内にある未使用の静的 IP アドレスを、可用性グループ リスナーに割り当てます。  
  
    この結果、ウィザードは Windows Azure 内でレプリカの追加を完了することができます。  
  
2.  ウィザードが完了した後、 [チュートリアル: Windows Azure AlwaysOn 可用性グループのリスナー構成](http://msdn.microsoft.com/library/dn376546.aspx)で説明されているように、Windows Azure 内のリスナー構成を完了する必要があります。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="SSAS"></a>6.0 Analysis Services  
  
### <a name="61-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2010-new-farm-configured-with-sql-server-2014"></a>6.1 SQL Server 2014 で構成された SharePoint 2010 の新しいファーム用に MSOLAP.5 のダウンロード、インストール、登録が必要  
**問題点:**  
  
-   SQL Server 2014 RTM の配置で構成された SharePoint 2010 ファームでは、接続文字列で参照されているプロバイダーがインストールされていないことが原因で、PowerPivot ブックをデータ モデルに接続できません。  
  
**回避策:**  
  
1.  [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] Feature Pack から MSOLAP.5 プロバイダーをダウンロードします。 Excel Services を実行しているアプリケーション サーバーにプロバイダーをインストールします。 詳細については、「 [Microsoft SQL Server 2012 SP1 用 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580)」の「Microsoft Analysis Services OLE DB Provider for Microsoft SQL Server 2012 SP1」を参照してください。  
  
2.  MSOLAP.5 を信頼できるプロバイダーとして SharePoint Excel Services に登録します。 詳細については、「 [Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](http://technet.microsoft.com/library/hh758436.aspx)」を参照してください。  
  
**詳細情報:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には MSOLAP.6 が含まれます。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] と [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssGemini](../includes/ssgemini-md.md)] のブックでは MSOLAP.5 が使用されます。 Excel Services を実行しているコンピューターに MSOLAP.5 がインストールされていない場合は、Excel Services はデータ モデルを読み込むことができません。  
  
### <a name="62-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2013-new-farm-configured-with-sql-server-2014"></a>6.2 SQL Server 2014 で構成された SharePoint 2013 の新しいファーム用に MSOLAP.5 のダウンロード、インストール、および登録が必要  
**問題点:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] の配置で構成された SharePoint 2013 ファームでは、接続文字列で参照されているプロバイダーがインストールされていないことが原因で、MSOLAP.5 プロバイダーを参照する Excel ブックから表形式のデータ モデルに接続することはできません。  
  
**回避策:**  
  
1.  [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] Feature Pack から MSOLAP.5 プロバイダーをダウンロードします。 Excel Services を実行しているアプリケーション サーバーにプロバイダーをインストールします。 詳細については、「 [Microsoft SQL Server 2012 SP1 用 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580)」の「Microsoft Analysis Services OLE DB Provider for Microsoft SQL Server 2012 SP1」を参照してください。  
  
2.  MSOLAP.5 を信頼できるプロバイダーとして SharePoint Excel Services に登録します。 詳細については、「 [Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](http://technet.microsoft.com/library/hh758436.aspx)」を参照してください。  
  
**詳細情報:**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] には MSOLAP.6 が含まれます。 ただし、SQL Server 2014 PowerPivot ブックでは MSOLAP.5 が使用されます。 Excel Services を実行しているコンピューターに MSOLAP.5 がインストールされていない場合は、Excel Services はデータ モデルを読み込むことができません。  
  
### <a name="63-corrupt-data-refresh-schedules"></a>6.3 データ更新スケジュールの破損  
**問題点:**  
  
-   更新スケジュールを更新すると、スケジュールが壊れて使用できなくなります。  
  
**回避策:**  
  
1.  Microsoft Excel で、カスタムの詳細プロパティをクリアします。 サポート技術情報 [KB 2927748](http://support.microsoft.com/kb/2927748)の「回避策」を参照してください。  
  
**詳細情報:**  
  
-   ブックのデータ更新スケジュールを更新すると、更新スケジュールのシリアル化された長さが元のスケジュールより小さい場合、バッファー サイズが正しく更新されず、新しいスケジュール情報が古いスケジュール情報とマージされるため、スケジュールが破損します。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="DQS"></a>7.0 Data Quality Services  
  
### <a name="71-no-cross-version-support-for-data-quality-services-in-master-data-services"></a>7.1 バージョンの異なる Master Data Services での Data Quality Service はサポートされない  
**問題点:** 次のシナリオはサポートされていません。  
  
-   Data Quality Services 2012 がインストールされている SQL Server 2012 内にある SQL Server データベース エンジンのデータベースでの Master Data Services 2014 のホスティング。  
  
-   Data Quality Services 2014 がインストールされている SQL Server 2014 内にある SQL Server データベース エンジンのデータベースでの Master Data Services 2012 のホスティング。  
  
**回避策:** データベース エンジンのデータベース、および Data Quality Services と同じバージョンの Master Data Services を使用してください。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  
## <a name="UA"></a>8.0 アップグレード アドバイザーの問題点  
  
### <a name="81--sql-server-2014-upgrade-advisor-reports-irrelevant-upgrade-issues-for-sql-server-reporting-services"></a>8.1 SQL Server 2014 アップグレード アドバイザーが SQL Server Reporting Services に関係のないアップグレードの問題点を報告する  
**問題点:** SQL Server 2014 メディアに収録されている SQL Server Upgrade Advisor (SSUA) が SQL Server Reporting Services サーバーを分析するときに、不適切な複数のエラーを報告します。  
  
**回避策:** [SSUA に対応する SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=306709)の一部として提供される SQL Server アップグレード アドバイザーで、この問題が解決されます。  
  
### <a name="82--sql-server-2014-upgrade-advisor-reports-an-error-when-analyzing-sql-server-integration-services-server"></a>8.2 SQL Server 2014 アップグレード アドバイザーで SQL Server Integration Services サーバーを分析するときにエラーが報告される  
**問題点:** SQL Server 2014 メディアに収録されている SQL Server Upgrade Advisor (SSUA) が、SQL Server Integration Services サーバーを分析するときにエラーを報告します。  ユーザーに対して表示されるエラーは、次のようなものです。  
  
```  
The installed version of Integration Services does not support Upgrade Advisor.   
The assembly information is "Microsoft.SqlServer.ManagedDTS, Version=11.0.0.0,   
Culture=neutral, PublicKeyToken=89845dcd8080cc91  
```  
  
**回避策:** [SSUA に対応する SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=306709)の一部として提供される SQL Server アップグレード アドバイザーで、この問題が解決されます。  
  
![[トップに戻る] リンクで使用される矢印アイコン](../release-notes/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン")[トップ](#top)  
  

