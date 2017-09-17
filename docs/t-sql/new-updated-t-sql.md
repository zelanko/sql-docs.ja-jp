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
ms.date: 09/11/2017
ms.author: genemi
ms.workload: t-sql
ms.translationtype: MT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: fa2ad3f4bc6071c54b9996a893ee584ba215100f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-transact-sql-docs"></a>新規または最近の更新: TRANSACT-SQL のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2017-07-18** &nbsp;対&nbsp; **2017 年-09-11**
- *サブジェクト領域:* &nbsp; **T-SQL**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

次のリンクは、最近追加された新しいアーティクルにジャンプします。


1. [予測 (TRANSACT-SQL)](queries/predict-transact-sql.md)
2. [ALTER 外部ライブラリ (TRANSACT-SQL)](statements/alter-external-library-transact-sql.md)
3. [外部ライブラリ (TRANSACT-SQL) を作成します。](statements/create-external-library-transact-sql.md)
4. [ドロップ外部ライブラリ (TRANSACT-SQL)](statements/drop-external-library-transact-sql.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、大幅な更新が最近発生したアーティクルから収集された更新プログラムの抜粋を表示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この圧縮リストは、抜粋セクションに記載されているすべての更新されたアーティクルへのリンクを提供します。

1. [CAST および CONVERT (TRANSACT-SQL)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-cast-and-convert-transact-sqlfunctionscast-and-convert-transact-sqlmd"></a>1.&nbsp;[CAST および CONVERT (TRANSACT-SQL)](functions/cast-and-convert-transact-sql.md)

*最終更新日: 2017 年-09-08* &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; 

<!-- Source markdown line 647.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b805ecddecda72ffc026c3866b5284a79b69fb3f f2906eaf87c7cdf1409922d4efba8cd1c5635674  (PR=0  ,  Filename=cast-and-convert-transact-sql.md  ,  Dirpath=docs\t-sql\functions\  ,  MergeCommitSha40=b97cc9723d563b19c85661f5ad7049a96fc904ff) -->



**K.CAST を算術演算子を使用して使用します。**

次の例は、製品の単価を割ることによって、1 つの列の計算を計算 (`UnitPrice`) して割引率 (`UnitPriceDiscountPct`)。 この結果に変換される、`int`最も近い整数に丸められた後にデータを入力します。 AdventureWorksDW を使用します。

```
SELECT ProductKey, UnitPrice,UnitPriceDiscountPct,
       CAST(ROUND (UnitPrice*UnitPriceDiscountPct,0) AS int) AS DiscountPrice
FROM dbo.FactResellerSales
WHERE SalesOrderNumber = 'SO47355'
      AND UnitPriceDiscountPct > .02;
```

..!テキストの NotShown--ssResult--./../includes/ssresult-md.md)]

```
ProductKey  UnitPrice  UnitPriceDiscountPct  DiscountPrice
----------  ---------  --------------------  -------------
323         430.6445   0.05                  22
213         18.5043    0.05                  1
456         37.4950    0.10                  4
456         37.4950    0.10                  4
216         18.5043    0.05                  1
```

**L.連結する CAST を使用します。**

次の例では、キャストを使用する文字式を連結します。 AdventureWorksDW を使用します。

```
SELECT 'The list price is ' + CAST(ListPrice AS varchar(12)) AS ListPrice
FROM dbo.DimProduct
WHERE ListPrice BETWEEN 350.00 AND 400.00;
```

..!テキストの NotShown--ssResult--./../includes/ssresult-md.md)]

```
ListPrice
------------------------
The list price is 357.06
The list price is 364.09
The list price is 364.09
The list price is 364.09
The list price is 364.09
```

**M です。キャストを使用して、読みやすいテキストを作成するには**

次の例に変換する、選択リストでキャストを使用して、`Name`列を**char (10)**列です。 AdventureWorksDW を使用します。

```
SELECT DISTINCT CAST(EnglishProductName AS char(10)) AS Name, ListPrice
FROM dbo.DimProduct
WHERE EnglishProductName LIKE 'Long-Sleeve Logo Jersey, M';
```

..!テキストの NotShown--ssResult--./../includes/ssresult-md.md)]







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションには、パブリック GitHub.com リポジトリ内の他のサブジェクト領域で、最近更新されたアーティクルのアーティクルを非常に似ていますが一覧表示されます: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/)です。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新しい + 更新 (3 + 12): **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (5 + 0): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (5 + 1): **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (19 + 82): **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (1 + 8): **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (12 + 1):**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (0 + 1): **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (7 + 1): **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新しい + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (4 + 1): **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)
- [新しい + 更新 (0 + 1): **Tools for SQL** docs](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新しい + 更新 (0 0 以降): **SQL のように、マスター データ サービス (MDS)** docs](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



