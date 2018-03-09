---
title: "更新 - リレーショナル データベース ドキュメント | Microsoft Docs"
description: "最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。"
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 02/03/2018
ms.openlocfilehash: 38f9ee55137c54adddb07fbe9f3b74dd43d51a3a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *"更新日の範囲:"* &nbsp; **2017 年 12 月 3 日**&nbsp;から&nbsp;**2018 年 2 月 3 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server または SQL Database に JSON ドキュメントを格納する](json/store-json-documents-in-sql-tables.md)
2. [SQL 脆弱性評価](security/sql-vulnerability-assessment.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [データベース ファイルの初期化](#TitleNum_1)
2. [tempdb データベース](#TitleNum_2)
3. [SQL Server の JSON データ](#TitleNum_3)
4. [レッスン 1: データベース エンジンへの接続](#TitleNum_4)
5. [トランザクション ログ ファイルのサイズの管理](#TitleNum_5)
6. [bcp_bind](#TitleNum_6)
7. [SQL Server インデックス デザイン ガイド](#TitleNum_7)
8. [sp_execute_external_script (Transact-SQL)](#TitleNum_8)
9. [主キーの作成](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-database-file-initializationdatabasesdatabase-instant-file-initializationmd"></a>1.&nbsp; [データベース ファイルの初期化](databases/database-instant-file-initialization.md)

*更新日: 2018 年 1 月 23 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([次へ](#TitleNum_2))

<!-- Source markdown line 81.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5f2aa53a8b43d4c43e0602cf945cb7c7028a27d 04c261c6588af1f53cda2fce3e9a86167c50b686  (PR=4702  ,  Filename=database-instant-file-initialization.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=3206a31870f8febab7d1718fa59fe0590d4d45db) -->



```
Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.
```

**適用対象:** SQL Server (SQL Server 2012 SP4 以降、SQL Server 2014 SP2、SQL Server 2016 から SQL Server 2017)

**セキュリティに関する考慮事項**

ファイルの瞬時初期化 (IFI) を利用するとき、削除されたディスクの内容は、新しいデータがファイルに書き込まれるときにのみ上書きされるため、他のデータがデータ ファイルのその領域に書き込まれるまで、許可されていないプリンシパルが削除された内容にアクセスする可能性があります。 データベース ファイルが SQL Server のインスタンスにアタッチされている間は、ファイルに対する随意アクセス制御リスト (DACL) により、このような情報漏えいのリスクは軽減されます。 この DACL により、SQL Server サービス アカウントとローカル管理者のみにファイル アクセスが許可されます。 ただし、ファイルがデタッチされると、SE\_MANAGE\_VOLUME_NAME が付与されていないユーザーまたはサービスからアクセスされる可能性があります。 データベースのバックアップ時にも同様の懸案事項があります。バックアップ ファイルが適切な DACL で保護されていない場合、許可されていないユーザーやサービスが削除された内容を利用できるようになることがあります。

もう 1 つの考慮事項は、IFI を使用してファイルが拡張された場合、SQL Server 管理者が未加工のページ コンテンツにアクセスして、以前削除されたコンテンツを表示する可能性があることです。

データベース ファイルが記憶域ネットワークでホストされている場合、記憶域ネットワークで常に新しいページが事前に初期化されているものとして示される可能性もあり、オペレーティング システムでページが再初期化されると不要なオーバーヘッドが発生する可能性があります。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>2. &nbsp; [tempdb データベース](databases/tempdb-database.md)

*更新日: 2018 年 1 月 17 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 100.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d 3257c92d6e2a88968fc44e5f6262c02cd0624635  (PR=0  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



 これらのデータベース オプションの説明は、「[ALTER DATABASE の SET オプション (Transact-SQL)](databases/../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。

**SQL Database の Tempdb データベース**


|SLO|最大 Tempdb データ ファイル サイズ (MB)|tempdb データ ファイルの数|最大 tempdb データ サイズ (MB)|
|---|---:|---:|---:|
|[標準]|14,225|@shouldalert|14,225|
|S0|14,225|@shouldalert|14,225|
|S1|14,225|@shouldalert|14,225|
|S2|14,225| @shouldalert|14,225|
|S3|32,768|@shouldalert|32,768|
|S4|32,768|2|65,536|
|S6|32,768|3|98,304|
|S7|32,768|6|196,608|
|S9|32,768|12|393,216|
|S12|32,768|12|393,216|
|P1|32,768|12|393,216|
|P2|32,768|12|393,216|
|P4|32,768|12|393,216|
|P6|32,768|12|393,216|
|P11|32,768|12|393,216|
|P15|32,768|12|393,216|
|Premium エラスティック プール (すべての DTU 構成)|14,225|12|170,700|
|Standard エラスティック プール (すべての DTU 構成)|14,225|12|170,700|
|Basic エラスティック プール (すべての DTU 構成)|14,225|12|170,700|
||||




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>3.&nbsp; [SQL Server の JSON データ](json/json-data-sql-server.md)

*更新日: 2018 年 2 月 1 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 62dd9c68d8cb72d6bf51b941a0731224514f0a7f 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5  (PR=4783  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=73f18ae24a9a48234bf997ee9a2ef441bc4918b9) -->



-   [GeoJSON データを SQL Server 2016 に読み込む](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/)

**SQL クエリで JSON データを分析する**

レポート作成のために JSON データをフィルター処理または集計する必要がある場合は、**OPENJSON** を使用して JSON をリレーショナル形式に変換できます。 その後、標準の Transact-SQL と組み込み関数を使ってレポートを用意することができます。

```
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date
FROM   SalesOrderRecord AS Tab
          CROSS APPLY
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')
           WITH (
              Number   varchar(200) N'$.Order.Number',
              Date     datetime     N'$.Order.Date',
              Customer varchar(200) N'$.AccountNumber',
              Quantity int          N'$.Item.Quantity'
           )
  AS SalesOrderJsonData
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-lesson-1-connecting-to-the-database-enginelesson-1-connecting-to-the-database-enginemd"></a>4.&nbsp; [レッスン 1: データベース エンジンへの接続](lesson-1-connecting-to-the-database-engine.md)

*更新日: 2017 年 12 月 13 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_3) | [次へ](#TitleNum_5))

<!-- Source markdown line 79.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c070935895450fd2ea054e2be9e1c48f7dc2b6c 0c386e3d47fb7f8f1e63b9301f0cafec2bc88ab0  (PR=4282  ,  Filename=lesson-1-connecting-to-the-database-engine.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=6e016a4ffd28b09456008f40ff88aef3d911c7ba) -->



2.  **[データベース エンジン]**を選択します。

    ![オブジェクト エクスプ ローラー](../relational-databases/media/object-explorer.png)

3.  **[サーバー名]** ボックスに、データベース エンジンのインスタンスの名前を入力します。 SQL Server の既定のインスタンスでは、サーバー名はコンピューター名です。 SQL Server の名前付きインスタンスでは、サーバー名は *<コンピューター名>***\\***<インスタンス名>* となります (**ACCTG_SRVR\SQLEXPRESS** など)。 次のスクリーンショットは、"PracticeComputer" という名前のコンピューター上の、既定の (名前のない) SQL Server インスタンスへの接続を示しています。 Windows にログオンしているユーザーは、Contoso ドメインの Mary です。 Windows 認証を使用する場合は、ユーザー名を変更することはできません。

    ![connect-to-server](../relational-databases/media/connect-to-server.png)

4.  **[接続]**をクリックします。

> [!NOTE]
> このチュートリアルでは、SQL Server を初めて使い、接続時に特別な問題がないことを想定しています。 このような前提はほとんどのユーザーにとって十分であり、このチュートリアルが単純であるのはこのためです。 詳細なトラブルシューティングの手順については、「 [SQL Server データベース エンジンへの接続のトラブルシューティング](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)」を参照してください。

**<a name="additional"></a>追加接続の認証**

ここまでの作業で、管理者として SQL Server に接続できました。次に行う最初の作業の 1 つに、他のユーザーの接続の認証があります。 これには、ログインを作成し、そのログインに対し、ユーザーとしてデータベースにアクセスすることを認証します。 ログインは Windows 認証ログインまたは SQL Server 認証ログインです。Windows 認証ログインには Windows の資格情報が使用されます。SQL Server 認証ログインは Windows の資格情報に依存せず、認証情報は SQL Server に保存されます。 可能であれば、Windows 認証を使用します。



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-manage-the-size-of-the-transaction-log-filelogsmanage-the-size-of-the-transaction-log-filemd"></a>5.&nbsp; [トランザクション ログ ファイルのサイズの管理](logs/manage-the-size-of-the-transaction-log-file.md)

*更新日: 2018 年 1 月 17 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_4) | [次へ](#TitleNum_6))

<!-- Source markdown line 105.  ms.author= "jhubbard".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5847b31cf8f6003a380f0c8aaa289efdc55be678 84e45320d81db218cde17fbf8b9668a9ac3805a7  (PR=0  ,  Filename=manage-the-size-of-the-transaction-log-file.md  ,  Dirpath=docs\relational-databases\logs\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



-   増分が少ないと小さな [VLF](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) が過度に生成され、パフォーマンスが低下します。 指定されたインスタンスにおいて、すべてのデータベースの現在のトランザクション ログ サイズに最適な VLF 配布と必要なサイズを得るために必要な増分を決定するには、この[スクリプト](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs)をご覧ください。

-   増分が大きいと大きな [VLF](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) が生成される回数が極めて少なく、やはりパフォーマンスに影響が出ます。 指定されたインスタンスにおいて、すべてのデータベースの現在のトランザクション ログ サイズに最適な VLF 配布と必要なサイズを得るために必要な増分を決定するには、この[スクリプト](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs)をご覧ください。

-   自動拡張を有効にしても、増加が遅く、クエリのニーズを満たせなければ、トランザクション ログがいっぱいになったというメッセージが表示されます。 増分変更の詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41; の File および Filegroup オプション](logs/../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)」を参照してください。

-   データベースにログ ファイルが複数存在すると、パフォーマンスが向上しません。トランザクション ログ ファイルでは、同じファイル グループのデータ ファイルのように[比例配分](logs/../../relational-databases/pages-and-extents-architecture-guide.md#ProportionalFill)を利用することがないためです。

-   ログ ファイルは自動的に圧縮するように設定できます。 ただし、これは**推奨されません**。**auto_shrink** データベース プロパティは既定で FALSE に設定されています。 **auto_shrink** を TRUE に設定すると、ファイル領域の 25% を超える領域が未使用の場合にのみ、自動圧縮によってファイルのサイズが縮小されます。



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-bcpbindnative-client-odbc-extensions-bulk-copy-functionsbcp-bindmd"></a>6. &nbsp; [bcp_bind](native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)

*更新日: 2018 年 1 月 30 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_5) | [次へ](#TitleNum_7))

<!-- Source markdown line 127.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d50791cef948ce8b3066438e317ab4d34d535258 e6f70559e7237cfc86dfc5746d218c08bec52af6  (PR=4762  ,  Filename=bcp-bind.md  ,  Dirpath=docs\relational-databases\native-client-odbc-extensions-bulk-copy-functions\  ,  MergeCommitSha40=60006e90d03fdb75b282bbc0dad3d40571bacacc) -->



 次の表では、有効な列挙データ型と対応する ODBC C データ型の一覧を示します。

|eDataType|C 型|
|-----------------------|------------|
|SQLTEXT|char *|
|SQLNTEXT|wchar_t *|
|SQLCHARACTER|char *|
|SQLBIGCHAR|char *|
|SQLVARCHAR|char *|
|SQLBIGVARCHAR|char *|
|SQLNCHAR|wchar_t *|
|SQLNVARCHAR|wchar_t *|
|SQLBINARY|unsigned char *|
|SQLBIGBINARY|unsigned char *|
|SQLVARBINARY|unsigned char *|
|SQLBIGVARBINARY|unsigned char *|
|SQLBIT|char|
|SQLBITN|char|
|SQLINT1|char|
|SQLINT2|short int|
|SQLINT4|ssNoversion|
|SQLINT8|_int64|
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|
|SQLFLT4|FLOAT|
|SQLFLT8|FLOAT|
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|
|SQLDECIMALN|SQL_NUMERIC_STRUCT|
|SQLNUMERICN|SQL_NUMERIC_STRUCT|
|SQLMONEY|DBMONEY|
|SQLMONEY4|DBMONEY4|
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|
|SQLTIMEN|SQL_SS_TIME2_STRUCT|
|SQLDATEN|SQL_DATE_STRUCT|
|SQLDATETIM4|DBDATETIM4|
|SQLDATETIME|DBDATETIME|
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|
|SQLIMAGE|unsigned char *|
|SQLUDT|unsigned char *|
|SQLUNIQUEID|SQLGUID|
|SQLVARIANT|*以下を除く任意のデータ型:*<br />-   text<br />-   ntext<br />-   image<br />-   varchar(max)<br />-   varbinary(max)<br />-   nvarchar(max)<br />-   xml<br />-   timestamp|
|SQLXML|*サポートされる C のデータ型*<br />-   char*<br />-   wchar_t *<br />-   unsigned char *|



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-sql-server-index-design-guidesql-server-index-design-guidemd"></a>7.&nbsp; [SQL Server インデックス デザイン ガイド](sql-server-index-design-guide.md)

*更新日: 2018 年 1 月 2 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_6) | [次へ](#TitleNum_8))

<!-- Source markdown line 700.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bd09c9e66cd3cf5f3ebebe7ffa6e937978353169 8e5cbbf0063971676a8bafefba75aa5c7c28be61  (PR=0  ,  Filename=sql-server-index-design-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=74daee358fef75a25d75c69d971d08536c5bd2be) -->



SQL Server 2016 以降、更新可能な**非クラスター化列ストア インデックスを、行ストア テーブル**に作成できます。 列ストア インデックスは、データのコピーを格納するため、追加のストレージが必要です。 ただし、列ストア インデックス内のデータは、行ストア テーブルが必要とするサイズよりも小さいサイズに圧縮されます。  これにより、同時に、列ストア インデックスの分析と行ストア インデックスのトランザクションを同時に実行できます。 行ストア テーブルでデータが変更されると列ストアが更新されます。したがって、両方のインデックスが、同じデータに対して作業を行うことになります。

SQL Server 2016 以降、列ストア インデックスでは、**1 つ以上の非クラスター化行ストア インデックス**を使用できます。 これにより、基になる列ストアで、効率的なテーブル シークを実行できます。 他のオプションも使用できます。 たとえば、行ストア テーブルで UNIQUE 制約を使用することで、主キー制約を適用できます。 一意でない値は行ストア テーブルに挿入できないため、SQL Server でその値を列ストアに挿入することはできません。

**パフォーマンスに関する考慮事項**


-   非クラスター化列ストア インデックスの定義で、フィルター適用条件の使用をサポートします。 OLTP テーブルに列ストア インデックスを追加することによるパフォーマンスへの影響を最小限に抑えるには、フィルター条件を使って、用して、運用ワークロードのコールド データのみに、非クラスター化列ストア インデックスを作成します。

-   インメモリ テーブルでは、列ストア インデックスを 1 つ使用できます。 これは、テーブルの作成時に作成することも、後で [ALTER TABLE &#40;Transact-SQL&#41;](../t-sql/statements/alter-table-transact-sql.md) を使用して追加することもできます。 SQL Server 2016 より前のバージョンでは、列ストア インデックスを保持できたのはディスク ベースのテーブルのみでした。

詳細については、「[列ストア インデックス - クエリ パフォーマンス](../relational-databases/indexes/columnstore-indexes-query-performance.md)」を参照してください。

**設計のガイドライン**


-   行ストア テーブルで、更新可能な非クラスター化列ストア インデックスを 1 つ使用できます。 SQL Server 2014 より前のバージョンでは、非クラスター化列ストア インデックスは読み取り専用でした。



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-spexecuteexternalscript-transact-sqlsystem-stored-proceduressp-execute-external-script-transact-sqlmd"></a>8. &nbsp; [sp_execute_external_script (Transact-SQL)](system-stored-procedures/sp-execute-external-script-transact-sql.md)

*更新日: 2018 年 1 月 23 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_7) | [次へ](#TitleNum_9))

<!-- Source markdown line 207.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0ee4d591ae9d9a5c015eec98aad9ccbb86268761 ac9b439c23ffae5fcc77639de6ff955763cf5844  (PR=4696  ,  Filename=sp-execute-external-script-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=d7dcbcebbf416298f838a39dd5de6a46ca9f77aa) -->



Python を使って似たモデルを生成するには、言語識別子を `@language=N'R'` から `@language = N'Python'` に変更し、`@script` 引数を必要に応じて修正します。 そうしないと、すべてのパラメーターが R と同じように機能します。

**C.Python モデルを作成し、それからスコアを生成する**


この例では、\_execute\_external\_script を使って簡単な Python モデルでスコアを生成する方法を示します。

```
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

**Input query to generate the customer data**

DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders`

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

**Get data from input query**

customer_data = my_input_data

**Define the model**

n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Python コードで使われている列見出しは、SQL Server への出力ではありません。そのため、WITH RESULTS ステートメントを使って、SQL で使う列名とデータ型を指定します。

スコアリングには、ネイティブな [PREDICT](system-stored-procedures/../../t-sql/queries/predict-transact-sql.md) 関数を使うこともできます。通常、これは Python や R のランタイムを呼び出さないので高速です。




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-create-primary-keystablescreate-primary-keysmd"></a>9.&nbsp; [主キーの作成](tables/create-primary-keys.md)

*更新日: 2018 年 1 月 18 日*&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;([前へ](#TitleNum_8))

<!-- Source markdown line 102.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d18b485f314cc005d624cab8a51650d3b8f55f89 9bd2e9453206e8940d30b0a01c43f9d8e1aed606  (PR=4652  ,  Filename=create-primary-keys.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**新しいテーブルに非クラスター化インデックスの主キーを作成するには**


1.  **オブジェクト エクスプローラー**で、データベース エンジンのインスタンスに接続します。

2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。

3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 次の例では、テーブルを作成して `CustomerID` 列に主キーを、`TransactionID` にクラスター化インデックスを定義します。

```
    USE AdventureWorks2012;
    GO
    CREATE TABLE Production.TransactionHistoryArchive1
    (
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)
    );
    GO

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
```







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域


- [新規 + 更新 (1 + 3):&nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (12 + 1): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (6 + 2):&nbsp;**Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (15 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (2 + 9):&nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (1 + 0):&nbsp;**SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 1):&nbsp;**SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (1 + 1):&nbsp;**Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 2):&nbsp;**SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2):&nbsp;**Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域


- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


