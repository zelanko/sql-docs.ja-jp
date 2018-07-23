---
title: 更新済み - SQL Server のドキュメント | Microsoft Docs
description: 最近変更された SQL Server に関するドキュメントで更新されたコンテンツのスニペットを示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 3575f65c751d91e2a32cf0acbf76665b42378d6a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084434"
---
# <a name="new-and-recently-updated-sql-server-docs"></a>新規および最近の更新: SQL Server のドキュメント



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *対象領域:* &nbsp; **SQL Server**。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server のドキュメントに投稿する方法](sql-server-docs-contribute.md)
2. [SQL Server のプライバシーの補足情報](sql-server-privacy.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [SQL Server 2012 Service Pack のリリース ノート](#TitleNum_1)
2. [SQL Server 2016 リリース ノート](#TitleNum_2)
3. [SQL Server のドキュメント](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2012-service-pack-release-notessql-server-2012-sp4-release-notesmd"></a>1.&nbsp; [SQL Server 2012 Service Pack のリリース ノート](sql-server-2012-sp4-release-notes.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 57.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ce108992ea942b4a11f30d67a1a52d7f26868caa a6269ba2cb2d3b3b54aebf5087dc4d513e476a96  (PR=5676  ,  Filename=sql-server-2012-sp4-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- **自動ソフト NUMA のパーティション分割**: サーバー レベルでトレース フラグ 8079 が有効になっている場合、SQL 2014 SP2 で自動[ソフト NUMA](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx) パーティション分割が導入されます。 スタートアップ時にトレース フラグ 8079 が有効になっていると、SQL Server 2014 SP2 はハードウェア レイアウトを問い合わせて、NUMA ノードあたり 8 個以上の CPU をレポートするシステムにソフト NUMA を自動的に構成します。 自動ソフト NUMA の動作は、ハイパースレッド (HT/論理プロセッサ) に対応しています。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 自動ソフト NUMA を実稼働環境でオンにする前に、最初にワークロードのパフォーマンスをテストすることをお勧めします。

**Service Pack 3 リリース ノート**


**ダウンロード ページ**

- [SQL Server 2012 SP3 Feature Pack](http://go.microsoft.com/fwlink/?linkid=615935)
- [SQL Server 2012 SP3 Express](http://go.microsoft.com/fwlink/?linkid=692144)

現在インストールされているバージョンに対応したダウンロードするファイルの場所と名前がわかる詳細情報については、「[SQL Server 2012 Service Pack 3 release information](https://support.microsoft.com/help/3072779/sql-server-2012-service-pack-3-release-information)」(SQL Server 2012 Service Pack 3 リリース情報) の「Select the correct file to download」(ダウンロードする正しいファイルの選択) セクションをご覧ください。

**Service Pack 2 リリース ノート**


**ダウンロード ページ**

- [SQL Server 2012 SP2 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=401008)
- [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)

次の表を使用して、現在インストールされているバージョンを基に、ダウンロードするファイルの場所と名前を確認します。 システム要件と基本的なインストール手順が含まれているページをダウンロードします。

|現在のバージョン|操作内容|ダウンロードおよびインストールするバージョン|



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-2016-release-notessql-server-2016-release-notesmd"></a>2.&nbsp; [SQL Server 2016 リリース ノート](sql-server-2016-release-notes.md)

*更新日: 2018 年 4 月 27 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_1) | [次へ](#TitleNum_3))

<!-- Source markdown line 25.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a15210866acf524dae49f3a7fd7957c9ffa6a78a 7257cb2017779242cbb8fa2b562f4b102502e942  (PR=5695  ,  Filename=sql-server-2016-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->



  ここでは、SQL Server 2016 リリースでの制限事項と問題について説明します。Service Pack についても説明します。 新機能については、「 [SQL Server 2016 の新機能](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-2016)」をご覧ください。

- **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)** から SQL Server 2016 をダウンロードする
- Azure Virtual Machine のアイコン: Azure アカウントをすでにお持ちですか?  **[こちら](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** にアクセスして、SQL Server 2016 SP1 がインストール済みの仮想マシンをすぐにご利用いただけます。
- SSMS をダウンロードする: 最新版の SQL Server Management Studio を入手するには、「**[SQL Server Management Studio (SSMS) のダウンロード]**」を参照してください。

**<a name="bkmk_2016sp2"></a>SQL Server 2016 Service Pack 2 (SP2)**


SQL Server 2016 SP2 には、2016 SP1 より後にリリースされた、CU8 まで (CU8 を含む) の累積的な更新プログラムがすべて含まれています。

- [Microsoft ダウンロード: SQL Server 2016 Service Pack 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- 更新プログラムの完全な一覧については、「[SQL Server 2016 Service Pack 2 リリース情報 ](https://support.microsoft.com/help/4052908/sql-server-2016-service-pack-2-release-information)」を参照してください。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-documentationsql-server-technical-documentationmd"></a>3.&nbsp; [SQL Server のドキュメント](sql-server-technical-documentation.md)

*更新日: 2018 年 4 月 27 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_2))

<!-- Source markdown line 77.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0262010ba39785a6d46b42f8469fb17701f13008 c69a83236391d039381a93c65ebbb2efa53e11b8  (PR=5695  ,  Filename=sql-server-technical-documentation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->




<!-- : : : m-r -->
**SQL Server をお試しください。**
- Evaluation Center からダウンロードする: [Windows 用 SQL Server のダウンロード](http://go.microsoft.com/fwlink/?LinkID=829477)
- Evaluation Center からダウンロードする: SQL Server Management Studio (SSMS) のダウンロード
- Evaluation Center からダウンロードする: SQL Server Data Tools (SSDT) のダウンロード
- 仮想マシンの作成: [SQL Server で仮想マシンをすぐにご利用いただけます](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)





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

