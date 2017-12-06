---
title: "SQL Server のドキュメントへの接続の更新 |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、Microsoft SQL Server への接続の更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.workload: connect-to-sql
ms.openlocfilehash: cb0ac4b391559cfac072cff61c9f13b14fe7c952
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-connect-to-sql-server"></a>新規または最近更新された: SQL Server に接続



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-09-28** &nbsp;対&nbsp; **2017 年-12-02**
- *サブジェクト領域:* &nbsp; **SQL Server への接続**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [データ ソース ウィザード画面 1](odbc/windows/dsn-wizard-1.md)
2. [データ ソース ウィザード画面 2](odbc/windows/dsn-wizard-2.md)
3. [データ ソース ウィザード画面 3](odbc/windows/dsn-wizard-3.md)
4. [データ ソース ウィザード画面 4](odbc/windows/dsn-wizard-4.md)
5. [SQL Server ログイン ダイアログ ボックス (ODBC)](odbc/windows/sql-server-login-dialog.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [PDOStatement::bindParam](#TitleNum_1)
2. [PDOStatement::bindValue](#TitleNum_2)
3. [sqlsrv_prepare](#TitleNum_3)
4. [sqlsrv_query](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-pdostatementbindparamphppdostatement-bindparammd"></a>1.&nbsp;[Pdostatement::bindparam](php/pdostatement-bindparam.md)

*最終更新日: 2017 年 1-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 119.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2792d149331f5326f6914721c86687d545685488 e363544e2c6f73277b7f2ca05b9269a4139d1fac  (PR=3663  ,  Filename=pdostatement-bindparam.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。

**例**

このコード サンプルでは、入力パラメーターとして 10 進値をバインドする方法を示します。

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-pdostatementbindvaluephppdostatement-bindvaluemd"></a>2.&nbsp;[PDOStatement::bindValue](php/pdostatement-bindvalue.md)

*最終更新日: 2017 年 1-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 77.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c1d5ff4d5bfdbfbf1635cf14d71b4d583164075a 6cd5fc88860ae9ffca25ee15e8eeaeba29991fda  (PR=3663  ,  Filename=pdostatement-bindvalue.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。

**例**

このコード サンプルでは、入力パラメーターとして 10 進値をバインドする方法を示します。

```php
<?php
$database = "Test";
$server = "(local)";
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");

// Assume TestTable exists with a decimal field
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sqlsrvpreparephpsqlsrv-preparemd"></a>3. &nbsp; [sqlsrv_prepare](php/sqlsrv-prepare.md)

*最終更新日: 2017 年 1-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 219.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 7811e459efec90ef79340375d5fb34364130466b 3d28b3d320dc7fe5df12300da5cb9579abf6839a  (PR=3663  ,  Filename=sqlsrv-prepare.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。

**例**

このコード サンプルでは、入力パラメーターとして 10 進値をバインドする方法を示します。

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect.\n";
    die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sqlsrvqueryphpsqlsrv-querymd"></a>4. &nbsp; [sqlsrv_query](php/sqlsrv-query.md)

*最終更新日: 2017 年 1-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3))

<!-- Source markdown line 163.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07a84878c07af0b6ad7e247337be5b4567ce03c3 127af26a8a054a45dda51d90f43f08652949ba18  (PR=3663  ,  Filename=sqlsrv-query.md  ,  Dirpath=docs\connect\php\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



> [!NOTE]
> 値をバインドするときに、入力として文字列を使用することをお勧め、 [decimal 型または numeric 列](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql)PHP での有効桁数が限られているために、有効桁数と精度を確保する[浮動小数点数](http://php.net/manual/en/language.types.float.php)です。

**例**

このコード サンプルでは、入力パラメーターとして 10 進値をバインドする方法を示します。

```php
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");
$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
     echo "Could not connect.\n";
     die(print_r(sqlsrv_errors(), true));
}

// Assume TestTable exists with a decimal field
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_query($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);

?>
```








## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (3 + 14): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (1 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (87 + 0): **sql 分析プラットフォーム システム**docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (5 + 4): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (0 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (2 + 2): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (10 + 9): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (2 + 4):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (4 + 2): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (0 + 1): **SQL 用のサンプル**docs](../sample/new-updated-sample.md)
- [新しい + 更新 (21 + 0): **SQL 操作 Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新しい + 更新 (5 + 1): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 2): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新しい + 更新 (0 0 以降):**データ移行アシスタント (DMA) sql** docs](../dma/new-updated-dma.md)
- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


