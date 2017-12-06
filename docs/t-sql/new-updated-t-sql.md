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
ms.date: 12/02/2017
ms.author: genemi
ms.workload: t-sql
ms.openlocfilehash: 33c50454f34c1902ea7f7dedc9ecb0a54f99ce24
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>新規または最近の更新: TRANSACT-SQL のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017 年-09-28** &nbsp;対&nbsp; **2017 年-12-02**
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

1. [円記号 (行の連結) (TRANSACT-SQL)](#TitleNum_1)
2. [選択 - ORDER BY 句 (TRANSACT-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-backslash-line-continuation-transact-sqllanguage-elementssql-server-utilities-statements-backslashmd"></a>1.&nbsp;[円記号 (行の連結) (TRANSACT-SQL)](language-elements/sql-server-utilities-statements-backslash.md)

*最終更新日: 2017 年-11-15* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 83.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9484441710ac9a083a554ffadb59a3b7e92484b3 19b9c37c65ba462a32067c80e81a920eeb339851  (PR=3966  ,  Filename=sql-server-utilities-statements-backslash.md  ,  Dirpath=docs\t-sql\language-elements\  ,  MergeCommitSha40=b0c223ba0f78af5eb76948e68e2d1aab2e7b80c1) -->



**B.バイナリ文字列の分割**


次の例では、円記号と復帰を使用して、バイナリ文字列を 2 つの行に分割します。

```
SELECT 0xabc\
def AS [ColumnResult];

```

 ..!テキストの NotShown--ssResult--./../includes/ssresult-md.md)]

```
 ColumnResult
 ------------
 0xABCDEF
```




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-select---order-by-clause-transact-sqlqueriesselect-order-by-clause-transact-sqlmd"></a>2.&nbsp;[選択 - ORDER BY 句 (TRANSACT-SQL)](queries/select-order-by-clause-transact-sql.md)

*最終更新日: 2017 年 1-10-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1))

<!-- Source markdown line 481.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b8d7bc7bab46e914eb2facf6c654a5944383077e de7e4f3f7826011e273120a2b6b08af4d263a510  (PR=3663  ,  Filename=select-order-by-clause-transact-sql.md  ,  Dirpath=docs\t-sql\queries\  ,  MergeCommitSha40=e9caa51a68c2f03fb9f3a0354b5eab1eed43bdf1) -->



**<a name="Union"></a>Order BY 句を使用して、和集合を EXCEPT、および INTERSECT**

 クエリで UNION、EXCEPT、または INTERSECT 演算子を使用する場合は、ORDER BY 句をステートメントの末尾に指定する必要があります。この場合、結合されたクエリの結果が並べ替えられます。 赤または黄色と組み合わせてこの種類は、すべての製品を返す例を次の列によって一覧`ListPrice`です。

```sql
USE AdventureWorks2012;
GO
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Red'
-- ORDER BY cannot be specified here.
UNION ALL
SELECT Name, Color, ListPrice
FROM Production.Product
WHERE Color = 'Yellow'
ORDER BY ListPrice ASC;

```

**例:.. です。テキストの NotShown--ssSDWfull--./../includes/sssdwfull-md.md)]、.. です。テキストの NotShown--ssPDW--./../includes/sspdw-md.md)]**








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


