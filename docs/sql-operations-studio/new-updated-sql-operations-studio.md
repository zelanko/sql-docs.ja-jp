---
title: 更新済み - SQL 操作 Studio docs |Microsoft ドキュメント
description: 最近変更したドキュメントについては、SQL 操作 Studio の更新されたコンテンツのスニペットを表示します。
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssops
ms.date: 04/28/2018
ms.openlocfilehash: 074ed6176480655d9d87a55eb87cbb76b3011b7e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-operations-studio-docs"></a>新規または最近の更新: SQL 操作 Studio docs



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新プログラムの日付範囲:* &nbsp; **2018-02-03** &nbsp;対&nbsp; **2018-04-28**
- *サブジェクト領域:* &nbsp; **SQL 操作 Studio**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


- [SQL 操作 Studio (プレビュー) の機能を拡張します。](extensions.md)

<!-- GeneMi:  I MANUALLY replace the ugly !INCLUDE with the name from inside the includes file. -->


&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [ダウンロードして SQL 操作 Studio (プレビュー) のインストール](#TitleNum_1)
2. [SQL 操作 Studio (プレビュー) のリリース ノート](#TitleNum_2)
3. [チュートリアル: 追加、 *5 速度が遅かったクエリ*データベース ダッシュ ボードにウィジェットをサンプル](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-and-install-sql-operations-studio-previewdownloadmd"></a>1.&nbsp; [ダウンロードして SQL 操作 Studio (プレビュー) のインストール](download.md)

*最終更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6b4f80ad54c599e4354303a736f62e9715f99a32 18b22f464bbd8676348248ba5717b71acbab1c0d  (PR=5676  ,  Filename=download.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



   **Debian のインストール:**
```
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
```

   **rpm インストール:**
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

### <a name="2-nbsp-sql-operations-studio-preview-release-notesrelease-notesmd"></a>2.&nbsp; [SQL 操作 Studio (プレビュー) のリリース ノート](release-notes.md)

*最終更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e2901d8a197f375f7d10ec93cbc9320362bf9278 0dde1aceceb339cb4cacd744e469f3d85d589668  (PR=5676  ,  Filename=release-notes.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[年 4 月のパブリック プレビューのダウンロード]**


**年 4 月 2018 (年 4 月のパブリック プレビュー)**


リリース日: 2018 年 4 月 25日バージョン: 0.28.6

*年 4 月のパブリック プレビュー*バグの修正プログラムと機能強化が含まれています。

- SQL エージェント プレビュー拡張機能が改善されました。
- 保護されている管理者を保存するための大規模で保護されたファイルのサポートの向上と > SQL 操作 Studio 内で 256 個のファイルです。
- 一度に複数開いている終端要素を使用するターミナル分割を統合します。
- 高速インストールが、スタートアップに時間の削減インストール ディスク上のファイル数フィートを印刷します。
- GitHub の問題を修正し続けます。
   - 修正[発行 37](https://github.com/Microsoft/sqlopsstudio/issues/37): グラフ ビューアーは、エラーをスローするときに予期しない動作が発生します。
   - 修正[462 を発行](https://github.com/Microsoft/sqlopsstudio/issues/462): 機能の要求: 既定で展開するサーバー グループのオプションです。
   - 修正[発行 606](https://github.com/Microsoft/sqlopsstudio/issues/606): intellisense、'update' コマンドの不適切な提案します。
   - 修正[967 を発行](https://github.com/Microsoft/sqlopsstudio/issues/967): クエリ プランを想定して、結果グリッドで XML プラン表示を選択するとします。
   - 修正[1023 を発行](https://github.com/Microsoft/sqlopsstudio/issues/1023): flyfishingdba から ms_foreachdb 呼び出しの角かっこを追加します。
   - 修正[発行 1048](https://github.com/Microsoft/sqlopsstudio/issues/1048): ログイン前の SSL や TLS ハンドシェイク エラーです。
   - 修正[発行 1050](https://github.com/Microsoft/sqlopsstudio/issues/1050): クリア insights がエラーを表示する前に表示します。
   - 修正[発行 1057](https://github.com/Microsoft/sqlopsstudio/issues/1057): 復元とウィジェット エクスプ ローラーで新しいクエリのアクションが破損しています。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboardtutorial-qds-sql-servermd"></a>3.&nbsp; [チュートリアル: 追加、 *5 速度が遅かったクエリ*データベース ダッシュ ボードにウィジェットをサンプル](tutorial-qds-sql-server.md)

*最終更新日: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2))

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

- [新しい + 更新 (11 + 6): &nbsp; &nbsp; **SQL の Advanced Analytics** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (18 + 0): &nbsp; &nbsp; **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (218 + 14): **SQL への接続**docs](../connect/new-updated-connect.md)
- [新しい + 更新 (14 + 0): &nbsp; &nbsp; **SQL のデータベース エンジン**docs](../database-engine/new-updated-database-engine.md)
- [新しい + 更新 (3 + 2): &nbsp; &nbsp; **sql Integration Services** docs](../integration-services/new-updated-integration-services.md)
- [新しい + 更新 (3 + 3): &nbsp; &nbsp; **SQL の Linux** docs](../linux/new-updated-linux.md)
- [新しい + 更新 (7 + 10): &nbsp; &nbsp;**リレーショナル データベースを SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [新しい + 更新 (0 + 2): &nbsp; &nbsp; **sql Reporting Services** docs](../reporting-services/new-updated-reporting-services.md)
- [新しい + 更新 (1 + 3): &nbsp; &nbsp; **SQL 操作 Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新しい + 更新 (2 + 3): &nbsp; &nbsp; **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (1 + 1): &nbsp; &nbsp; **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新しい + 更新 (5 + 2): &nbsp; &nbsp; **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新しい + 更新 (0 + 2): &nbsp; &nbsp; **TRANSACT-SQL** docs](../t-sql/new-updated-t-sql.md)
- [新しい + 更新 (1 + 1): &nbsp; &nbsp; **Tools for SQL** docs](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域

- [新しい + 更新 (0 0 以降): **sql 分析プラットフォーム システム**docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (0 0 以降): **SQL 用の PowerShell** docs](../powershell/new-updated-powershell.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../samples/new-updated-samples.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)

