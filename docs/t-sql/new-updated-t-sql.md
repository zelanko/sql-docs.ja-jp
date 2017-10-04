---
title: "更新済み - T-SQL docs |Microsoft ドキュメント"
description: "最近変更したドキュメントについては、TRANSACT-SQL の更新されたコンテンツのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.workload: t-sql
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 4d48c7df783ebe50f7b5d7fe3e72bef91559006e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="new-and-recently-updated-transact-sql-docs"></a>新規または最近の更新: TRANSACT-SQL のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-09-11** &nbsp;対&nbsp; **2017 年-09-27**
- *サブジェクト領域:* &nbsp; **T-SQL**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


***今回は新しい記事はありません。***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [sql_variant 型 (TRANSACT-SQL)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sqlvariant-transact-sqldata-typessql-variant-transact-sqlmd"></a>1. &nbsp; [sql_variant 型 (TRANSACT-SQL)](data-types/sql-variant-transact-sql.md)

*最終更新日: 2017 年-09-13* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 111.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 659578de7de33d8672ceb9542093862107d13526 c80026de2b0deedab3722a874e9124c2cfefa049  (PR=0  ,  Filename=sql-variant-transact-sql.md  ,  Dirpath=docs\t-sql\data-types\  ,  MergeCommitSha40=5cd78481b3fac55ec34b59e7b1ad25e0e14d2a00) -->



**使用例**


**A.テーブルで、sql_variant 型の使用**

 次の例では、sql_variant データ型を持つテーブルを作成します。 例を取得し、`SQL_VARIANT_PROPERTY`については、`colA`値`46279.1`場所`colB`  =`1689`こと、`tableA`が`colA`型である`sql_variant`と`colB`.

```
CREATE   TABLE tableA(colA sql_variant, colB int)
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'
FROM      tableA
WHERE      colB = 1689
```

 ..!テキストの NotShown--ssResult--./../includes/ssresult-md.md)] がそれぞれ 3 つの値のことに注意してください、 **sql_variant**です。

```
Base Type    Precision    Scale
---------    ---------    -----
decimal      8           2

(1 row(s) affected)
```

**B.変数として、sql_variant 型の使用**

 次の例では、sql_variant データ型を使用して変数を作成し、取得し、`SQL_VARIANT_PROPERTY`という名前の変数に関する情報@v1です。

```
DECLARE @v1 sql_variant;
SET @v1 = 'ABC';
SELECT @v1;
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');
```








## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (0 + 1): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (0 + 1): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (4 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (17 + 0): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (3 + 0): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (1 + 1):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (2 + 0): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 1): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新しい + 更新 (0 0 以降): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新しい + 更新 (0 0 以降): **Tools for SQL** docs](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



