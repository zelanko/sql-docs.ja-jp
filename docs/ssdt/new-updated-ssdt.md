---
title: "更新済み - SQL Server 用 SSDT のドキュメント | Microsoft Docs"
description: "Microsoft SQL Server 用 SQL Server Data Tools (SSDT) の最近変更されたドキュメントで更新されたコンテンツのスニペットを示します。"
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
ms.workload: ssdt-sql-server-data-tools
ms.translationtype: HT
ms.sourcegitcommit: 15080827744c19120a8474f3142004c4af7a4064
ms.openlocfilehash: 8ae9a49443525524cf7f6ffceba4fb44984c7052
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>新規および最近の更新: SQL Server Data Tools (SSDT)



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 7 月 18 日**&nbsp;から &nbsp; **2017 年 9 月 11 日**
- *対象領域:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server Data Tools - ライセンス条項](sql-server-data-tools-license-terms-vs2017.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server Data Tools (SSDT) の変更ログ](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1.&nbsp; [SQL Server Data Tools (SSDT) の変更ログ](changelog-for-sql-server-data-tools-ssdt.md)

*更新日: 2017 年 8 月 23 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 23.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 536fe0fe41b023a4186f494a509fa14fcbafccf4 e5bc7b76c1755f5a1af77f6cd63d8e8691dafe7b  (PR=2927  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=71a2cbf181c94c4c1aff877614aadf890b2496e0) -->



**SSDT for Visual Studio 2017 (15.3.0 プレビュー)**

ビルド番号: 14.0.16121.0

**新機能**


このプレビューは、SSDT for Visual Studio 2017 の最初のバージョンです。 このリリースでは、Visual Studio 2017 (15.3 以降) での SQL Server データベース、Analysis Services、Reporting Services、および Integration Services のプロジェクトに対してスタンドアロン Web インストール エクスペリエンスを導入します。


**既知の問題**

- インストーラーはローカライズされていません。
- SSIS はローカライズされていません。
- *ExecuteOutofProcess* が *True* に設定されると、SSIS パッケージ実行タスクはデバッグをサポートしません。 この問題はデバッグにのみ該当します。 DTExec.exe または SSIS カタログを介した保存、展開、実行は影響を受けません。
- すべての変更の一覧については、[changelog--changelog-for-sql-server-data-tools-ssdt.md) をご覧ください。
- [SSDT Connect フィードバック](https://connect.microsoft.com/SQLServer/Feedback) サイトで問題を報告します。
- サード パーティの拡張機能を含む SSIS パッケージは、その他のサーバー バージョンを対象にするように切り替えることはできません。


**SSDT 17.2 for Visual Studio 2015**

ビルド番号: 14.0.61707.300

**新機能**



**AS プロジェクト:**
- 1400 互換性レベル表形式モデルでの高度なセキュリティの [*ロール*] ダイアログでオブジェクト レベルのセキュリティを構成できるようになりました。
- VS2017 の SSDT AS プロジェクトの AS Azure モデルにメール アドレスがないユーザーに対する新しい AAD ロール メンバー選択。
- ADAL 資格情報のキャッシュ動作をカスタマイズするための SSDT AS テーブル プロジェクトでの新しい AS Azure の "Always Prompt" プロジェクト プロパティ。


**バグの修正**


**全般**
- SQL Server 2017 の参照のブランド化が更新されました。

**AS プロジェクト**
- DAX メジャーの変更とその他のモデルの編集をコミットするときのエクスペリエンスを向上させるため、大幅なパフォーマンスの修正が行われました。
- 1400 互換性レベル表形式モデルを使用する Analysis Services プロジェクトでの Power Query 統合で複数の問題を修正しました。
- VS2017 でデザイン集計デザイナーのみが読み込みに失敗する場合がある、多次元プロジェクトの問題を修正しました。







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



