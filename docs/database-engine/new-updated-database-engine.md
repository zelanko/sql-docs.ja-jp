---
title: "更新 - データベース エンジン ドキュメント | Microsoft Docs"
description: "最近変更されたデータベース エンジンに関するドキュメントで更新されたコンテンツのスニペットを示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: barbkess
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: database-engine
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 09/27/2017
ms.author: genemi
ms.openlocfilehash: dc4a5516662b200b4224facbb4c9cf4588c1b42e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="new-and-recently-updated-database-engine-docs"></a>新規ドキュメントと最近更新されたドキュメント: データベース エンジン ドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 11 日**&nbsp;から &nbsp; **2017 年 9 月 27 日**
- *件名:* &nbsp; **データベース エンジン**




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server のインスタンスへの機能の追加 (セットアップ)](install-windows/add-features-to-an-instance-of-sql-server-setup.md)
2. [コマンド プロンプトからの SQL Server のインストール](install-windows/install-sql-server-from-the-command-prompt.md)
3. [構成ファイルを使用した SQL Server のインストール](install-windows/install-sql-server-using-a-configuration-file.md)
4. [ビジネス継続性とデータベースの復旧 - SQL Server](sql-server-business-continuity-dr.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [コマンド プロンプトからの更新プログラムのインストール](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-installing-updates-from-the-command-promptinstall-windowsinstalling-updates-from-the-command-promptmd"></a>1.&nbsp; [コマンド プロンプトからの更新プログラムのインストール](install-windows/installing-updates-from-the-command-prompt.md)

*更新日: 2017 年 9 月 12 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 48.  ms.author= "mikeray".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 04abb23d0682c23654a55e7926d2140f0b6ae408 a4bb1e27ae99460a66da72848ace1417b148f85c  (PR=3122  ,  Filename=installing-updates-from-the-command-prompt.md  ,  Dirpath=docs\database-engine\install-windows\  ,  MergeCommitSha40=1df54edd5857ac2816fa4b164d268835d9713638) -->



- コンピューター上の ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] のすべてのインスタンス、..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] のようなすべての共有コンポーネント、管理ツールを更新します。

```
    <package_name>.exe /qs /IAcceptSQLServerLicenseTerms /Action=Patch /AllInstances.
```

- ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] の単一のインスタンス、..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] のようなすべての共有コンポーネント、管理ツールから更新プログラムを削除します。

```
    <package_name>.exe /qs /Action=RemovePatch /InstanceName=MyInstance.
```

- ..!NCLUDE-NotShown--ssISnoversion--../../includes/ssisnoversion-md.md)] のような ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] の共有コンポーネントのみ、および管理ツールから更新プログラムを削除します。

```
    <package_name>.exe /qs /Action=RemovePatch
```







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (0 + 1): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (4 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (17 + 0): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (3 + 0): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 1): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 1): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


