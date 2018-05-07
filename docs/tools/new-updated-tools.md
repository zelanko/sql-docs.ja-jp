---
title: 更新済み - SQL Server 用ツールのドキュメント | Microsoft Docs
description: Microsoft SQL Server 用ツールの最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: tools
ms.date: 04/28/2018
ms.openlocfilehash: 0547653c4fc2d8bd04f851b843e74fd9ec78d2ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MTE
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-tools-for-sql-server"></a>新規または最近更新された: SQL Server のツール



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *サブジェクト領域:* &nbsp; **Tools for SQL Server**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


- [SQL Server の mssql cli コマンド ライン クエリ ツール](mssql-cli.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

- [bcp ユーティリティ](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-bcp-utilitybcp-utilitymd"></a>1. &nbsp; [bcp ユーティリティ](bcp-utility.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 189.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c85e6c6ff13ad20f432ead67febfc48c784f3f9a 27de3822192fc64f0d99b4dbc21f05a3e4def186  (PR=5676  ,  Filename=bcp-utility.md  ,  Dirpath=docs\tools\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**-G**<a name="G"></a> このスイッチは、Azure SQL Database または Azure SQL Data Warehouse に接続し、Azure Active Directory 認証を使用してユーザーを認証するように指定する場合に、クライアントによって使用されます。 -G スイッチが必要です[バージョン 14.0.3008.27 以降](http://go.microsoft.com/fwlink/?LinkID=825643)です。 バージョンを判断するには、bcp -v を実行します。 詳細については、次を参照してください。 [Azure Active Directory 認証を使用する SQL データベースまたは SQL Data Warehouse での認証](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication)です。

> [!TIP]
>  Bcp のバージョンが Azure Active Directory 認証 (AAD) の型のサポートを含むかどうかにチェックする**bcp--** (bcp\<領域 >\<dash >\<dash >)-g の一覧であることを確認使用可能な引数。

- **Azure Active Directory のユーザー名とパスワード:**

    Azure Active Directory のユーザー名とパスワードを使用には、 **-G** オプションを指定します。ユーザー名とパスワードは、 **-U** オプションと **-P** オプションを指定する方法でも使用できます。

    次の例は、Azure AD のユーザー名を使用してデータをエクスポートし、ここでユーザー名とパスワードは、AAD 資格情報のパスワード。 例では、エクスポート テーブル`bcptest`データベースから`testdb`Azure サーバーから`aadserver.database.windows.net`ファイルにデータを格納および`c:\last\data1.dat`:
```
    bcp bcptest out "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```

    The following example imports data using Azure AD Username and Password where user and password is an AAD credential. The example imports data from file `c:\last\data1.dat` into table `bcptest` for database `testdb` on Azure server `aadserver.database.windows.net` using Azure AD User/Password:
```
    bcp bcptest in "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```



- **Azure Active Directory 統合**

    Azure Active Directory 統合認証の場合、ユーザー名とパスワードなしで **-G** オプションを指定します。 この構成では、現在の Windows ユーザー アカウント (で bcp コマンドが実行されているアカウント) が Azure AD と統合されていることを前提としています。







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

