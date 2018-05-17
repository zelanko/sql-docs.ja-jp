---
title: 更新 - リレーショナル データベース ドキュメント | Microsoft Docs
description: 最近変更されたリレーショナル データベースに関するドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: relational-databases
ms.date: 04/28/2018
ms.openlocfilehash: a885befe2411a76dc8c68bf2a7b543a838a52877
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>新規または最近の更新: リレーショナル データベース ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *対象領域:* &nbsp; **リレーショナル データベース**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [結合 (SQL Server)](performance/joins.md)
2. [サブクエリ (SQL Server)](performance/subqueries.md)
3. [Always On 可用性グループのレプリケーション ディストリビューション データベースを設定する](replication/configure-distribution-availability-group.md)
4. [SQL データの検出と分類](security/sql-data-discovery-and-classification.md)
5. [トランザクションのロックおよび行のバージョン管理ガイド](sql-server-transaction-locking-and-row-versioning-guide.md)
6. [sys.dm_os_job_object (Azure SQL Database)](system-dynamic-management-views/sys-dm-os-job-object-transact-sql.md)
7. [Filestream および FileTable システム ストアド プロシージャ (Transact-SQL)](system-stored-procedures/filestream-and-filetable-system-stored-procedures.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [フォーマット ファイルを使用したテーブル列のスキップ (SQL Server)](#TitleNum_1)
2. [SQL Server の JSON データ](#TitleNum_2)
3. [クエリ処理アーキテクチャ ガイド](#TitleNum_3)
4. [チュートリアル: レプリケーション用の SQL Server の準備 - パブリッシャー、ディストリビューター、サブスクライバー](#TitleNum_4)
5. [チュートリアル: 2 つの常時接続サーバー間のレプリケーション (トランザクション) を構成する ](#TitleNum_5)
6. [チュートリアル: サーバーとモバイル クライアントの間のレプリケーション (マージ) を構成する](#TitleNum_6)
7. [フルテキスト検索でのクエリ](#TitleNum_7)
8. [Azure SQL Database および Data Warehouse 用の Bring Your Own Key サポートによる Transparent Data Encryption](#TitleNum_8)
9. [PowerShell と CLI: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする](#TitleNum_9)
10. [変更データ キャプチャについて (SQL Server)](#TitleNum_10)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-use-a-format-file-to-skip-a-table-column-sql-serverimport-exportuse-a-format-file-to-skip-a-table-column-sql-servermd"></a>1.&nbsp; [フォーマット ファイルを使用したテーブル列のスキップ (SQL Server)](import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 221.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 167916d79c5de1e7f13990cb7acc41ceb541b9a7 cb92eb201292294e3397879c98f353fba45f1c1c  (PR=0  ,  Filename=use-a-format-file-to-skip-a-table-column-sql-server.md  ,  Dirpath=docs\relational-databases\import-export\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**OPENROWSET(BULK...) の使用**


`OPENROWSET(BULK...)` を使用してテーブル列をスキップするために XML フォーマット ファイルを使用するには、次のように選択リストおよび対象テーブルの列リストを明示的に指定する必要があります。

```
    INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)
```

次の例では、 `OPENROWSET` 一括行セット プロバイダーと `myTestSkipCol2.xml` フォーマット ファイルを使用します。 この例では、 `myTestSkipCol2.dat` データ ファイルを `myTestSkipCol` テーブルに一括インポートします。 必要に応じて、ステートメントでは、選択リストおよびターゲット テーブルの列の一覧を明示的に指定します。

SSMS で、次のコードを実行します。 お使いのコンピューターのサンプル ファイルがある場所のファイル システム パスを更新します。

```
USE WideWorldImporters;
GO
INSERT INTO myTestSkipCol
  (Col1,Col3)
    SELECT Col1,Col3
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',
      FORMATFILE='C:\myTestSkipCol2.Xml'
       ) as t1 ;
GO
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>2.&nbsp; [SQL Server の JSON データ](json/json-data-sql-server.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 145.  ms.author= "jovanpop".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5 e2f2e8b4732779b3f24561cc0c4da3a958f4edbb  (PR=0  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



JSON ドキュメントには、サブ要素と、標準のリレーショナル列に直接マップできないデータ階層があります。 ここでは、親エンティティとサブ配列を結合することで JSON 階層をフラット化することができます。

次の例では、配列内の 2 番目のオブジェクトは、個人のスキルを表すサブ配列を持っています。 追加の `OPENJSON` 関数呼び出しを使用してすべてのサブオブジェクトを解析できます。

```
DECLARE @json NVARCHAR(MAX)
SET @json =
N'[
       { "id" : 2,"info": { "name": "John", "surname": "Smith" }, "age": 25 },
       { "id" : 5,"info": { "name": "Jane", "surname": "Smith", "skills": ["SQL", "C#", "Azure"] }, "dob": "2005-11-04T12:00:00" }
 ]'

SELECT *
FROM OPENJSON(@json)
  WITH (id int 'strict $.id',
        firstName nvarchar(50) '$.info.name', lastName nvarchar(50) '$.info.surname',
        age int, dateOfBirth datetime2 '$.dob',
    skills nvarchar(max) '$.skills' as json)
    outer apply openjson( a.skills )
                     with ( skill nvarchar(8) '$' ) as b
```
**skills** 配列は、最初の `OPENJSON` で元の JSON テキスト フラグメントとして返され、`APPLY` 演算子を使用して別の `OPENJSON` 関数に渡されます。 2 番目の `OPENJSON` 関数は、JSON 配列を解析し、最初の `OPENJSON` の結果と結合される 1 つの列の行セットとして文字列値を返します。
このクエリの結果は、次の表のようになります。

**結果**

|id|firstName|lastName|age|dateOfBirth|skill|
|--------|---------------|--------------|---------|-----------------|----------|
|2|John|Smith|25|||
|5|Jane|Smith||2005-11-04T12:00:00|SQL|
|5|Jane|Smith||2005-11-04T12:00:00|C#|
|5|Jane|Smith||2005-11-04T12:00:00|Azure|

`OUTER APPLY OPENJSON` は、最初のレベルのエンティティをサブ配列と結合し、フラット化された結果セットを返します。 結合により、すべてのスキルで 2 番目の行が繰り返されます。




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-query-processing-architecture-guidequery-processing-architecture-guidemd"></a>3.&nbsp; [クエリ処理アーキテクチャ ガイド](query-processing-architecture-guide.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 34.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 96d91b39acdb2f32aaff323e374e92d6f229d241 2c1d2f8585632ada174388399782dc3ed2721dba  (PR=0  ,  Filename=query-processing-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**論理演算子の優先順位**


1 つのステートメントで複数の論理演算子を使用すると、最初に `NOT` が評価され、次に `AND`、最後に `OR` が評価されます。 算術演算子、およびビット演算子は論理演算子より前に処理されます。 詳細については、「[Operator Precedence (Transact-SQL)]」(演算子の順位 (Transact-SQL)) を参照してください。

次の例では、色の条件が製品モデル 21 には該当しますが、製品モデル 20 には該当しません。これは、`AND` が `OR` よりも優先されるためです。

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR ProductModelID = 21
  AND Color = 'Red';
GO
```

`OR` が必ず最初に評価されるように、かっこを付け加えることでクエリの意味を変えることができます。 次のクエリでは、モデル 20 とモデル 21 で赤色の製品のみが検索されます。

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE (ProductModelID = 20 OR ProductModelID = 21)
  AND Color = 'Red';
GO
```

必要でない場合でもかっこを使用すると、クエリが読みやすくなり、演算子の優先順位が原因の微妙な間違いを犯す可能性が減少します。 かっこを使用することでパフォーマンスが大幅に低下することはありません。 次の例は、元の例と構文は同じですが、元の例よりも読みやすくなっています。

```
SELECT ProductID, ProductModelID
FROM Production.Product
WHERE ProductModelID = 20 OR (ProductModelID = 21
  AND Color = 'Red');
GO
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriberreplicationtutorial-preparing-the-server-for-replicationmd"></a>4.&nbsp; [チュートリアル: レプリケーション用の SQL Server の準備 - パブリッシャー、ディストリビューター、サブスクライバー](replication/tutorial-preparing-the-server-for-replication.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_3) | [次へ](#TitleNum_5))

<!-- Source markdown line 56.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6e5caedacff193ce79bdd98708ae1b9dc91f0a8f 9f7af4d3f8b1cffd048db2a5b29fc9e6013f5ed2  (PR=0  ,  Filename=tutorial-preparing-the-server-for-replication.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



- [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する方法の詳細については、「[SSMS を使用してデータベース バックアップを復元する](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)」を参照してください。

>[!NOTE]
> - 3 つ以上離れたバージョンの SQL Server では、レプリケーションはサポートされていません。 詳細については、「[Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/)」(Repl トポロジでサポートされている SQL バージョン) を参照してください。
> - *{Included-Content-Goes-Here}* では、固定サーバー ロール **sysadmin** のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。 sysadmin ロールの詳細については、「[サーバー レベルのロール](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/server-level-roles)」を参照してください。


**このチュートリアルの推定所要時間: 30 分**

**レプリケーション用の Windows アカウントの作成**

このセクションでは、レプリケーション エージェントを実行するための Windows アカウントを作成します。 また、次のエージェントを実行するための別の Windows アカウントをローカル サーバー上に作成します。

|エージェント|場所|アカウント名|
|---------|------------|----------------|
|スナップショット エージェント|パブリッシャー|<*machine_name*>\repl_snapshot|



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-tutorial-configure-replication-between-two-fully-connected-servers-transactionalreplicationtutorial-replicating-data-between-continuously-connected-serversmd"></a>5.&nbsp; [チュートリアル: 2 つの常時接続サーバー間のレプリケーション (トランザクション) を構成する](replication/tutorial-replicating-data-between-continuously-connected-servers.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_4) | [次へ](#TitleNum_6))

<!-- Source markdown line 162.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0d74f984d0ffc01cce0376837e6d94df3c5654d7 4ecf4d724286130927dd43687d6845059af6f9b7  (PR=0  ,  Filename=tutorial-replicating-data-between-continuously-connected-servers.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**トランザクション パブリケーションへのサブスクリプションの作成**

このセクションでは、前の手順で作成したパブリケーションにサブスクライバーを追加します。 このチュートリアルでは、リモート サブスクライバー (NODE2\SQL2016) を使用しますが、サブスクリプションはローカルでパブリッシャーに追加することもできます。

**サブスクリプションを作成するには**


1.  *{Included-Content-Goes-Here}* でパブリッシャーに接続して、サーバー ノードを展開し、**[レプリケーション]** フォルダーを展開します。

2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** パブリケーションを右クリックして、**[新しいサブスクリプション]** を選択します。  サブスクリプションの新規作成ウィザードが起動します。

    [新しいサブスクリプション]

3.  [パブリケーション] ページで **[AdvWorksProductTrans]** を選択し、**[次へ]** を選択します。

    Tran パブリッシャーの選択

4.  [ディストリビューション エージェントの場所] ページで、**[ディストリビューターですべてのエージェントを実行する]** を選択し、**[次へ]** を選択します。  プル サブスクリプションとプッシュ サブスクリプションの詳細については、「[パブリケーションのサブスクライブ](https://docs.microsoft.com/sql/relational-databases/replication/subscribe-to-publications)」を参照してください。

    ディストリビューターでエージェントを実行する

5.  [サブスクライバー] ページでサブスクライバー インスタンスの名前が表示されない場合は、**[サブスクライバーの追加]** を選択し、ドロップダウン リストから **[SQL Server サブスクライバーの追加]** を選択します。 これにより **[サーバーへの接続]** ダイアログ ボックスが表示されます。 サブスクライバー インスタンス名を入力し、**[接続]** を選択します。



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-tutorial-configure-replication-between-a-server-and-mobile-clients-mergereplicationtutorial-replicating-data-with-mobile-clientsmd"></a>6.&nbsp; [チュートリアル: サーバーとモバイル クライアントの間のレプリケーション (マージ) を構成する](replication/tutorial-replicating-data-with-mobile-clients.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_5) | [次へ](#TitleNum_7))

<!-- Source markdown line 93.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0eed78dfe83c88358c030539a2b25d11ef5ec2d3 79b2a3f32c940fede94b11ad2a3ef8a00b911a39  (PR=0  ,  Filename=tutorial-replicating-data-with-mobile-clients.md  ,  Dirpath=docs\relational-databases\replication\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



Employee テーブルには、hierarchyid データ型を持つ列 (OrganizationNode) が含まれています。これは、SQL 2017 でレプリケーションに対してのみサポートされています。 SQL 2017 より前のビルドを使用している場合は、双方向のレプリケーションでこの列を使用するとデータ損失の可能性があることを通知するメッセージが画面の下部に表示されます。 このチュートリアルでは、このメッセージは無視してかまいません。 ただし、このデータ型は、サポートされているビルドを使用している場合を除き、実稼働環境でレプリケートしないでください。 hierarchyid データ型のレプリケーションに関する詳細は、「[レプリケートされたテーブルでの hierarchyid 列の使用](https://docs.microsoft.com/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables)」を参照してください。


-  [テーブル行のフィルター選択] ページで、**[追加]**、**[フィルターの追加]** の順に選択します。

-  **[フィルターの追加]** ダイアログ ボックスの **[フィルターを適用するテーブルを選択します。]** で、**[Employee (HumanResources)]** を選択します。 **[LoginID]** 列を選択し、右矢印を選択して、この列をフィルター選択クエリの WHERE 句に追加します。さらに、WHERE 句を次のように修正します。

    ```
    WHERE [LoginID] = HOST_NAME()
    ```

    A. **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** を選択して、**[OK]** を選択します。

    フィルターの追加



- **[テーブル行のフィルター選択]** ページで、**[Employee (Human Resources)]**、**[追加]** の順に選択し、**[選択したフィルターを拡張するために結合を追加する]** を選択します。

    A. **[結合の追加]** ダイアログ ボックスで、**[結合テーブル]** の下の **[Sales.SalesOrderHeader]** を選択します。 **[JOIN ステートメントを手動で作成する]** を選択し、次のように JOIN ステートメントを完成させます。



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-query-with-full-text-searchsearchquery-with-full-text-searchmd"></a>7.&nbsp; [フルテキスト検索でのクエリ](search/query-with-full-text-search.md)

*更新日: 2018 年 4 月 13 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_6) | [次へ](#TitleNum_8))

<!-- Source markdown line 247.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5ec67b56aa0a6eadadbcfa8b73b6726e75eca2bb 4eb108b202d3dd035a312bac7872cf02bcf31cfa  (PR=0  ,  Filename=query-with-full-text-search.md  ,  Dirpath=docs\relational-databases\search\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**生成語検索に関する詳細情報**


*変化形*は、動詞のさまざまな時制および活用、または名詞の単数形と複数形です。

たとえば、"drive" という語の変化形を検索します。 テーブルのさまざまな行に、"drive"、"drives"、"drove"、"driving"、および "driven" が含まれている場合、これらはどれも drive という語から変化して生成されているので結果セットに入ります。

[FREETEXT] および [FREETEXTTABLE] は、指定されたすべての語の変化形の語句を既定で検索します。 [CONTAINS] および [CONTAINSTABLE] は、省略可能な `INFLECTIONAL` 引数をサポートしています。

**特定の語のシノニムの検索**


*類義語辞典*は、ユーザー指定の用語のシノニムを定義します。 類義語辞典ファイルの詳細については、「[フルテキスト検索に使用する類義語辞典ファイルの構成と管理]」を参照してください。

たとえば、エントリ "{car, automobile, truck, van}" が類義語辞典に追加されると、"car" という語の類義語形式を検索できます。 "automobile"、"truck"、"van"、または "car" という語は、"car" という語を含むシノニムの拡張セットに属しているため、クエリ処理されるテーブルの行のうち、これらのいずれかの語を含むすべての行が結果セットに表示されます。

[FREETEXT] と [FREETEXTTABLE] は、類義語辞典を既定で使用します。 [CONTAINS] および [CONTAINSTABLE] は、省略可能な `THESAURUS` 引数をサポートしています。



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-transparent-data-encryption-with-bring-your-own-key-support-for-azure-sql-database-and-data-warehousesecurityencryptiontransparent-data-encryption-byok-azure-sqlmd"></a>8.&nbsp; [Azure SQL Database および Data Warehouse 用の Bring Your Own Key サポートによる Transparent Data Encryption](security/encryption/transparent-data-encryption-byok-azure-sql.md)

*更新日: 2018 年 4 月 24 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_7) | [次へ](#TitleNum_9))

<!-- Source markdown line 110.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9527658848d430bf0148be84474a75b232cbd112 70ed2a129c580962384f808e8526673957f00d2c  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**Azure Key Vault を使用して Geo-DR を構成する方法**


暗号化されたデータベースの TDE プロテクターの高可用性を維持するには、既存のまたは目的の SQL Database フェールオーバー グループまたはアクティブな geo レプリケーション インスタンスに基づいて、冗長な Azure Key Vault を構成する必要があります。  geo レプリケーションされたサーバーごとに、個別のキー コンテナーが必要で、同じ Azure リージョンにそのサーバーと併置する必要があります。 プライマリ データベースは、1 つのリージョンの停止のためにアクセス不可になり、フェールオーバーがトリガーされた場合は、セカンダリ データベースが、セカンダリ キー コンテナーを使用して引き継ぐことができます。

geo レプリケーションされた Azure SQL データベースの場合、Azure Key Vault の次の構成が必要です。
- 地域内にキー コンテナーがあるプライマリ データベースとセカンダリデータベースを 1 つずつ。
- 少なくとも 1 つのセカンダリが必要です。最大 4 つのセカンダリがサポートされます。
- セカンダリのセカンダリ (チェーン) はサポートされていません。

次のセクションでは、セットアップと構成手順について詳しく説明します。

**Azure Key Vault の構成手順**


- [PowerShell](https://docs.microsoft.com/powershell/azure/install-azurerm-ps?view=azurermps-5.6.0) のインストール
- キー コンテナーで [PowerShell で “soft-delete” プロパティを有効にする](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-powershell) (このオプションは AKV ポータルからはまだ使用できませんが、SQL で必要です) を使用して 2 つの異なる領域に 2 つの Azure Key Vault を作成します。
- 両方の Azure Key Vault は、キーのバックアップと復元が機能するために、同じ Azure Geo で使用できる 2 つのリージョンに配置する必要があります。  SQL Geo DR の要件を満たすために、2 つのキー コンテナーを異なる Geo に配置する必要がある場合は、オンプレミス HSM からキーをインポートすることができる [BYOK プロセス](https://docs.microsoft.com/azure/key-vault/key-vault-hsm-protected-keys)に従います。



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-powershell-and-cli-enable-transparent-data-encryption-using-your-own-key-from-azure-key-vaultsecurityencryptiontransparent-data-encryption-byok-azure-sql-configuremd"></a>9.&nbsp; [PowerShell と CLI: Azure Key Vault の自分のキーを使用して Transparent Data Encryption を有効にする](security/encryption/transparent-data-encryption-byok-azure-sql-configure.md)

*更新日: 2018 年 4 月 24 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_8) | [次へ](#TitleNum_10))

<!-- Source markdown line 196.  ms.author= "aliceku".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a0e00f5701d9a493f503a477c69097ce65aba174 721e8fb856a55ee1e8e9e7fc06036a03adab647b  (PR=5662  ,  Filename=transparent-data-encryption-byok-azure-sql-configure.md  ,  Dirpath=docs\relational-databases\security\encryption\  ,  MergeCommitSha40=91a9c812739a1c9a6ec9e7b8cda71ee1f5adae3d) -->



**CLI の前提条件**


- Azure サブスクリプションを所有し、そのサブスクリプションの管理者である必要があります。
- [推奨されますが、省略可能] TDE プロテクター キー マテリアルのローカル コピーを作成するためのハードウェア セキュリティ モジュール (HSM) またはローカル キー ストア。
- コマンド ライン インターフェイス バージョン 2.0 以降。 最新バージョンをインストールして Azure サブスクリプションに接続する方法については、[Azure クロスプラットフォーム コマンド ライン インターフェイス 2.0 のインストールと構成](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)に関するページを参照してください。
- TDE に使用する Azure Key Vault とキーを作成します。
   - [CLI 2.0 を使用した Key Vault の管理](https://docs.microsoft.com/azure/key-vault/key-vault-manage-with-cli2)
   - [ハードウェア セキュリティ モジュール (HSM) と Key Vault の使用手順](https://docs.microsoft.com/azure/key-vault/key-vault-get-started#a-idhsmaif-you-want-to-use-a-hardware-security-module-hsm)
 - キー コンテナーには、TDE で使用する次のプロパティが含まれている必要があります。
   - [論理的な削除](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete)
   - [CLI で Key Vault の論理的な削除を使用する方法](https://docs.microsoft.com/azure/key-vault/key-vault-soft-delete-cli)
- TDE に使用するには、キーに次の属性が必要です。
   - 有効期限がない
   - 無効ではない
   - *キーの取得*、*キーのラップ*、*キーのラップ解除*操作を実行できる

**サーバーを作成し、サーバーに Azure AD ID を割り当てる**

      cli
      # create server (with identity) and database



&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-about-change-data-capture-sql-servertrack-changesabout-change-data-capture-sql-servermd"></a>10.&nbsp; [変更データ キャプチャについて (SQL Server)](track-changes/about-change-data-capture-sql-server.md)

*更新日: 2018 年 4 月 17 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_9))

<!-- Source markdown line 112.  ms.author= "jroth".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 588bff652adefd719e799e9777a416b70184c5f8 77ebdbb1b98b24054d5c5afbb3f1d40e94d1e6bc  (PR=5574  ,  Filename=about-change-data-capture-sql-server.md  ,  Dirpath=docs\relational-databases\track-changes\  ,  MergeCommitSha40=bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68) -->



**データベースとテーブルの照合順序が違う場合の対応**


データベースの照合順序と、変更データ キャプチャ用に構成されたテーブルの列の照合順序が異なる状況について認識しておくことが重要です。 CDC は、中間記憶域を使用して、サイド テーブルを設定します。 テーブルにデータベースの照合順序とは異なる照合順序を持つ CHAR または VARCHAR 型の列があり、これらの列に非 ASCII 文字 (2 バイト DBCS 文字など) が格納される場合、CDC は変更されたデータとベース テーブル内のデータの整合性を維持できない可能性があります。 これは、中間記憶域の変数には照合順序を関連付けることができないためです。

変更キャプチャ データとベース テーブルの整合性を保つには、次のいずれかの方法を検討してください。

- 非 ASCII データを格納する列には NCHAR または NVARCHAR データ型を使用します。

- または、列とデータベースに同じ照合順序を使用します。

たとえば、SQL_Latin1_General_CP1_CI_AS の照合順序を使用するデータベースがある場合について、次のようなテーブルを考えます。

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 VARCHAR(10) collate Chinese_PRC_CI_AI)
```

列 C2 の照合順序が異なるので (Chinese_PRC_CI_AI)、この列に対するバイナリ データの CDC は失敗する可能性があります。 この問題を回避するには、NVARCHAR を使用します。

```
CREATE TABLE T1(
     C1 INT PRIMARY KEY,
     C2 NVARCHAR(10) collate Chinese_PRC_CI_AI --Unicode data type, CDC works well with this data type)
```







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域

- [新規 + 更新 (11 + 6): &nbsp; &nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (18 + 0): &nbsp; &nbsp;**SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (218 + 14):**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (14 + 0): &nbsp; &nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (3 + 2): &nbsp; &nbsp; **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (3 + 3): &nbsp; &nbsp; **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (7 + 10): &nbsp; &nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 3): &nbsp; &nbsp; **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **Tools for SQL** に関するドキュメント](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域

- [新規 + 更新 (0 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../samples/new-updated-samples.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)

