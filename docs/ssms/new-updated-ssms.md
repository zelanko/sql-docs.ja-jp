---
title: "更新済み - SQL Server 用 SSMS のドキュメント | Microsoft Docs"
description: "Microsoft SQL Server の SQL Server Management Studio (SSMS) の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。"
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
ms.date: 09/11/2017
ms.author: genemi
ms.workload: ssms-sql-server-management-studio
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 917198902baf85f2bae57c9ade9f8d3e29dea357
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>新規または最近の更新: SQL Server の SQL Server Management Studio (SSMS)



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 7 月 18 日**&nbsp;から &nbsp; **2017 年 9 月 11 日**
- *対象領域:* &nbsp; **SQL Server Management Studio (SSMS)**.




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server Management Studio の出力ウィンドウ](output-window.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server Management Studio (SSMS) のダウンロード](#TitleNum_1)
2. [SQL Server または Azure SQL Database への接続](#TitleNum_2)
3. [SQL Server Management Studio - Changelog (SSMS)](#TitleNum_3)
4. [データベース テーブルの作成と更新](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-sql-server-management-studio-ssmsdownload-sql-server-management-studio-ssmsmd"></a>1.&nbsp; [SQL Server Management Studio (SSMS) のダウンロード](download-sql-server-management-studio-ssms.md)

*更新日: 2017 年 8 月 7 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 63.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 23260f301f86651061b47065bee43d42c92a7be4 0c2178d96b621b96bfcd2fbb782f24792debb407  (PR=2775  ,  Filename=download-sql-server-management-studio-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



SSMS 17.2 は SQL Server Management Studio の最新バージョンです。 SSMS の 17.x 世代は、SQL Server 2008 から SQL Server 2017 までのほぼすべての機能領域をサポートしています。 バージョン 17.x は、SQL Analysis Service PaaS もサポートしています。

バージョン 17.2 の内容:

- Multi-Factor Authentication (MFA)
  - 多要素認証を使用したユニバーサル認証 (UA with MFA) 向けの複数ユーザーの Azure AD 認証
  - 複数ユーザーの認証をサポートするため、MFA を使用したユニバーサル認証用に新しいユーザー資格情報の入力フィールドが追加されました。
- 接続ダイアログ ボックスで、次の 5 つの認証方法がサポートされるようになりました。
  - [Windows 認証]
  - SQL Server 認証 (SQL Server Authentication)
  - Active Directory - Universal with MFA のサポート
  - Active Directory - パスワード
  - Active Directory - 統合

- DacFx のデータベースの Import/Export ウィザードで、MFA を使用したユニバーサル認証が使用できるようになりました。
- API のサポートについては、「[IUniversalAuthProvider インターフェイス](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)」を参照してください。
- MFA を使用した Azure AD ユニバーサル認証で使用される ADAL マネージ ライブラリは、バージョン 3.13.9 にアップグレードされました。
- SQL Database および SQL Data Warehouse の Azure AD 管理者設定をサポートする新しい CLI インターフェイス。

 Active Directory の認証方法の詳細については、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)」と「[SQL Server Management Studio 用に Azure SQL Database の多要素認証を構成する](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)」を参照してください。

- 出力ウィンドウには、オブジェクト エクスプローラー ノードの展開時に実行されるクエリのエントリがあります。
- Azure SQL Databases のビュー デザイナーの有効化
- SSMS でのオブジェクトのスクリプト作成の既定のスクリプト作成オプションが、オブジェクト エクスプローラーから変更されました。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-connect-to-a-sql-server-or-azure-sql-databaseobjectconnect-to-an-instance-from-object-explorermd"></a>2.&nbsp; [SQL Server または Azure SQL Database への接続](object/connect-to-an-instance-from-object-explorer.md)

*更新日: 2017 年 8 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 40.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cfd72893c35c87df96dc8605807e542be28936e2 840981d3a115a15774a8e47ee2f6a0e5c4177b01  (PR=2961  ,  Filename=connect-to-an-instance-from-object-explorer.md  ,  Dirpath=docs\ssms\object\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



   ![firewall--../media/connect-to-server/new-firewall-rule.png)

1. ファイアウォール規則を作成して、サーバーに接続するには、[**OK**] をクリックします。

1. 接続が正常に行われると、**オブジェクト エクスプローラー**にサーバー表示されます。

   ![connected--../media/connect-to-server/connected.png)

**次の手順**


[Design, Create, and Update Tables--../visual-db-tools/design-tables-visual-database-tools.md)

**関連項目**


[SQL Server Management Studio (SSMS)--../sql-server-management-studio-ssms.md) [Download SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)
[Integration Services](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>3.&nbsp; [SQL Server Management Studio - 変更ログ (SSMS)](sql-server-management-studio-changelog-ssms.md)

*更新日: 2017 年 8 月 7 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_2) | [次へ](#TitleNum_4))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1733ce3c556db1e51cb27bf830429f2c42e8f97e 2abb24fd6547e438181039d095cbad027473a57e  (PR=2775  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=3f12671ace99d5fefc199c7b1c2db31e5b3cfade) -->



この記事では、SSMS の現在と以前のバージョンの更新、機能強化、およびバグの修正に関する詳細を提供します。 ダウンロード [previous SSMS versions below--#previous-ssms-releases)

**[SSMS 17.2--download-sql-server-management-studio-ssms.md)**


一般公開 | ビルド番号: 14.0.17177.0

**機能強化**


- Multi-Factor Authentication (MFA)
  - 多要素認証を使用したユニバーサル認証 (UA with MFA) 向けの複数ユーザーの Azure AD 認証
  - 複数ユーザーの認証をサポートするため、MFA を使用したユニバーサル認証用に新しいユーザー資格情報の入力フィールドが追加されました。
- 接続ダイアログ ボックスで、次の 5 つの認証方法がサポートされるようになりました。
  - [Windows 認証]
  - SQL Server 認証 (SQL Server Authentication)
  - Active Directory - Universal with MFA のサポート
  - Active Directory - パスワード
  - Active Directory - 統合

- MFA を使用したユニバーサル認証を使用する DacFx のデータベースのインポート/エクスポート ウィザード。
- API のサポートについては、「[IUniversalAuthProvider インターフェイス](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx)」を参照してください。
- MFA を使用した Azure AD ユニバーサル認証で使用される ADAL マネージ ライブラリは、バージョン 3.13.9 にアップグレードされました。
- SQL Database および SQL Data Warehouse の Azure AD 管理者設定のサポートが実現された新しい CLI インターフェイスの追加。

 Active Directory の認証方法の詳細については、「[SQL Database と SQL Data Warehouse でのユニバーサル認証 (MFA 対応の SSMS サポート)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)」と「[SQL Server Management Studio 用に Azure SQL Database の多要素認証を構成する](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure)」を参照してください。

- 出力ウィンドウには、オブジェクト エクスプローラー ノードの展開時に実行されるクエリのエントリがあります。



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-create-and-update-database-tablesvisual-db-toolsdesign-tables-visual-database-toolsmd"></a>4.&nbsp; [データベース テーブルの作成と更新](visual-db-tools/design-tables-visual-database-tools.md)

*更新日: 2017 年 8 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_3))

<!-- Source markdown line 30.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f63884ac2d04889e70c505cb5262c8dd81d73ee7 4b4c7aa5e8a0548405f02d11a66b722219fa78f0  (PR=2961  ,  Filename=design-tables-visual-database-tools.md  ,  Dirpath=docs\ssms\visual-db-tools\  ,  MergeCommitSha40=21f0cfd102a6fcc44dfc9151750f1b3c936aa053) -->



**テーブルの作成**


1. データベースで **[テーブル]** ノードを右クリックし、**[新規作成]** > **[テーブル]** を選択します。

    ![New table--../media/design-tables/new-table.png)

1. [columns--column-properties-visual-database-tools.md) をテーブルに追加:

    ![design table--../media/design-tables/new-table2.png)

1. デザイナーを閉じて、変更を保存します。

**テーブルを更新する**


1. データベースの **[テーブル]** ノードの下にあるテーブルを右クリックし、**[デザイン]** を選択します。

   ![Update table--../media/design-tables/update-table.png)

1. 目的のテーブル設定を更新します。

   ![--../media/design-tables/update-table2.png)

1. デザイナーを閉じて、変更を保存します。

**関連項目**


[テーブル](http://msdn.microsoft.com/82d7819c-b801-4309-a849-baa63083e83f) [Table Properties &#40;Visual Database Tools&#41;--../../ssms/visual-db-tools/table-properties-visual-database-tools.md) [Column Properties--column-properties-visual-database-tools.md) [Add Columns to a Table--../../relational-databases/tables/add-columns-to-a-table-database-engine.md) [Primary and Foreign Keys--../../relational-databases/tables/primary-and-foreign-key-constraints.md) [Indexes--../../relational-databases/indexes/indexes.md) [Data types (Transact-SQL)--../../t-sql/data-types/data-types-transact-sql.md) [Download SQL Server Management Studio (SSMS)--../download-sql-server-management-studio-ssms.md)







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (3 + 12): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (5 + 0): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (5 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (19 + 82): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (1 + 8): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (12 + 1): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (0 + 1): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (7 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 2): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (1 + 4): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (4 + 1): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (0 + 1): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)



