---
title: 更新済み - SQL Operations Studio docs |Microsoft ドキュメント
description: 最近変更したドキュメントについては、SQL Operations Studio の更新されたコンテンツのスニペットを表示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 84ee3d7d346c8cddbf5251e0d63bb2ae222defb3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083454"
---
# <a name="new-and-recently-updated-sql-operations-studio-docs"></a>新規または最近の更新: SQL Operations Studio docs



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 時折不完全な書式設定の抜粋が表示されたり、ソース記事からマークダウンとして表示されたりすることがあります。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- "*更新日の範囲:* " &nbsp; **2018 年 2 月 3 日** &nbsp;から&nbsp; **2018 年 4 月 28 日**
- *サブジェクト領域:* &nbsp; **SQL Operations Studio**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


- [SQL Operations Studio (プレビュー) の機能を拡張します。](extensions.md)

<!-- GeneMi:  I MANUALLY replace the ugly !INCLUDE with the name from inside the includes file. -->


&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切られて表示されます。 また、元の記事の中で、重要なマークダウン構文に覆われた抜粋が区切られて表示されることもあります。 したがってこれらの抜粋は、一般的なガイダンスとしてのみ使用されます。 抜粋からは、その記事をクリックして訪れるに足るものであるか、ということだけを知ることができます。

これらおよびその他の理由によって、これらの抜粋からコードをコピーせず、テキストの抜粋を確かな事実として受け取らないようにしてください。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [ダウンロードして SQL Operations Studio (プレビュー) のインストール](#TitleNum_1)
2. [SQL Operations Studio (プレビュー) のリリース ノート](#TitleNum_2)
3. [チュートリアル: 追加、 *5 つの最も低速なクエリ*データベース ダッシュ ボードにサンプルのウィジェット](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-and-install-sql-operations-studio-previewdownloadmd"></a>1.&nbsp; [ダウンロードして SQL Operations Studio (プレビュー) のインストール](download.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次へ](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6b4f80ad54c599e4354303a736f62e9715f99a32 18b22f464bbd8676348248ba5717b71acbab1c0d  (PR=5676  ,  Filename=download.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



   **Debian のインストール:**
```
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
```

   **rpm のインストール:**
```
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
```

   **tar.gz インストール:**



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-operations-studio-preview-release-notesrelease-notesmd"></a>2.&nbsp; [SQL Operations Studio (プレビュー) のリリース ノート](release-notes.md)

*更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e2901d8a197f375f7d10ec93cbc9320362bf9278 0dde1aceceb339cb4cacd744e469f3d85d589668  (PR=5676  ,  Filename=release-notes.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[年 4 月のパブリック プレビューをダウンロードする]**


**2018 年 4 月 (年 4 月のパブリック プレビュー)**


リリース日: 2018 年 4 月 25 日のバージョン: 0.28.6

*年 4 月のパブリック プレビュー*バグ修正と改善が含まれています。

- SQL エージェント プレビュー拡張機能の改善。
- 保護されている管理者を保存するための大規模で保護されたファイルのサポートの向上と > SQL Operations Studio 内で 256 個のファイルです。
- 統合ターミナルを一度に複数のオープン端末で作業を分割します。
- 高速インストールおよびスタートアップに時間の削減インストール ディスク上のファイル数フィートを印刷します。
- 続行すると、GitHub の問題を修正します。
   - 修正[発行 37](https://github.com/Microsoft/sqlopsstudio/issues/37): グラフ ビューアーは、エラーをスローするときに予期しない動作が発生します。
   - 修正[462 発行](https://github.com/Microsoft/sqlopsstudio/issues/462): 機能の要求: 既定で展開するサーバー グループのオプション。
   - 修正[発行 606](https://github.com/Microsoft/sqlopsstudio/issues/606): intellisense、'update' コマンドの不適切な修正候補。
   - 修正[967 を発行](https://github.com/Microsoft/sqlopsstudio/issues/967): クエリ プランを予想される結果のグリッドで XML プラン表示を選択するとします。
   - 修正[発行 1023](https://github.com/Microsoft/sqlopsstudio/issues/1023): flyfishingdba から ms_foreachdb 呼び出しに角かっこを追加します。
   - 修正[発行 1048](https://github.com/Microsoft/sqlopsstudio/issues/1048): ログイン前の SSL や TLS ハンドシェイク エラー。
   - 修正[発行 1050](https://github.com/Microsoft/sqlopsstudio/issues/1050): クリア insights は、エラーを表示する前に表示します。
   - 修正[発行 1057](https://github.com/Microsoft/sqlopsstudio/issues/1057): 復元とエクスプ ローラー ウィジェットで新しいクエリのアクションが壊れています。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboardtutorial-qds-sql-servermd"></a>3.&nbsp; [チュートリアル: 追加、 *5 つの最も低速なクエリ*データベース ダッシュ ボードにサンプルのウィジェット](tutorial-qds-sql-server.md)

*更新日: 2018 年 4 月 25 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([前へ](#TitleNum_2))

<!-- Source markdown line 94.  ms.author= "erickang".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bc128acd966898cafc04381d7d83187d28466052 a47bf93ea4165618e0e514d7900ce1461f691aae  (PR=5676  ,  Filename=tutorial-qds-sql-server.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }







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
- [新しい + 更新 (1 + 3): &nbsp; &nbsp; **SQL Operations Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): &nbsp; &nbsp; **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 1): &nbsp; &nbsp; **Tools for SQL** に関するドキュメント](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域

- [新規 + 更新 (0 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../samples/new-updated-samples.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)

