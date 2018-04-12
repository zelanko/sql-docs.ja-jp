---
title: Microsoft SQL Operations Studio (preview) のリリース ノート |Microsoft ドキュメント
description: Microsoft SQL Operations Studio (preview) のリリース ノート
ms.custom: tools|sos
ms.date: 03/28/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba86403e791af25de4f7bcd8b1cbd7b5f188897b
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="sql-operations-studio-preview-release-notes"></a>SQL Operations Studio (preview) のリリース ノート

**[年 3 月のパブリック プレビューをダウンロードします。](download.md)**

## <a name="march-2018-march-public-preview"></a>年 3 月 2018 (パブリック プレビューの年 3 月)

リリース日: 2018 年 3 月 28日  
バージョン: 0.27.3

*年 3 月のパブリック プレビュー*最上位の GitHub の問題に対処が続けられは、機能拡張ストーリーを向上させることに重点を置きます。 具体的には拡張機能マネージャーを有効にすると、ダッシュ ボードの管理の向上および SQL エージェントと insights 拡張機能を提供することです。 このリリースには、次の機能強化が含まれています。

- タブ付き insights と構成ウィンドウをサポートするために、ダッシュ ボードの機能拡張モデルを拡張します。
   - 拡張機能マネージャーでは、拡張機能の簡単な取得できるようにします。
   - ダッシュ ボードから sp_whoisactive 拡張[whoisactive.com](http://www.whoisactive.com)です。
   - 詳細については、「 [SQL Operations Studio の機能拡張](extensions.md)です。
- さらに追加[接続およびオブジェクト エクスプ ローラーの機能拡張 Api](https://github.com/Microsoft/sqlopsstudio/wiki/Extensibility-API)管理します。
- 解決に影響する重要な顧客を継続[GitHub の問題](https://github.com/Microsoft/sqlopsstudio/issues)です。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md)です。


## <a name="february-2018-february-public-preview"></a>2 月 2018 (パブリック プレビューの年 2 月)

リリース日: 2018 年 2 月 15日  
バージョン: 0.26.7

*年 2 月のパブリック プレビュー*いくつかの機能に関する意見および優先度の高いバグの修正が含まれます。 このリリースには、次の機能強化が含まれています。

- 自動更新のインストールの概要を提供する、通知、新しいリリースがダウンロード可能な場合に 
- 接続ダイアログ 'Database' フィールドは、指定したサーバーから設定するデータベースの一覧を含む動的に設定されているドロップダウン リストではようになりました。
- 修正[6 を発行](https://github.com/Microsoft/sqlopsstudio/issues/6): クエリの新しいタブを開くときに接続し、選択したデータベースを保持します。
- 修正[発行 22](https://github.com/Microsoft/sqlopsstudio/issues/22): 'サーバー名' と ' Database Name' には、これらのドロップダウン テキスト ボックスの代わりにしますか?
- 修正[発行 549](https://github.com/Microsoft/sqlopsstudio/issues/549): インストール後に元のアプリケーションで結果サイレント/非常にサイレント インストールします。
- 修正[481 の発行](https://github.com/Microsoft/sqlopsstudio/issues/481):「更新プログラムを確認する」オプションを追加します。
- SQL エディターの色づけとオートコンプリートの修正:
   - 修正[発行 584](https://github.com/Microsoft/sqlopsstudio/issues/584): IntelliSense では、"FULL"強調表示されていないキーワードです。
   - 修正[発行 345](https://github.com/Microsoft/sqlopsstudio/issues/345): エディター内での色分け SQL 関数。
   - 修正[発行 300](https://github.com/Microsoft/sqlopsstudio/issues/300): [#tempData] 最新"]"緑の色が表示されます。
   - 修正[発行 225](https://github.com/Microsoft/sqlopsstudio/issues/225): キーワードの色が一致しません。
   - 修正[発行 60](https://github.com/Microsoft/sqlopsstudio/issues/60): 無効な sql 構文の色で強調表示の from 句内の一時テーブルを使用する場合。
- 接続の機能拡張 API を紹介します。
- VS コード エディター 1.19 統合します。
- ビューアーの改良がいくつかのクエリ プランを収集する JustinPealing/html-クエリ プランのコンポーネントに更新します。


## <a name="january-2018-january-public-preview"></a>年 1 月 2018 (パブリック プレビューの年 1 月)

リリース日: 2018 年 1 月 17日  
バージョン: 0.25.4

*年 1 月のパブリック プレビュー*いくつかの機能に関する意見および優先度の高いバグの修正が含まれます。 このリリースには、次の機能強化が含まれています。

- 接続ダイアログで保存されたサーバー接続を利用できます。
- ホット終了を有効にします。 ホット終了が既定では、「」を参照を有効にするに無効になって[ホット終了設定](settings.md#hot-exit)です。
- サーバー グループに基づくをタブの色指定します。 タブの色設定が既定では、「」を参照を有効にするに無効になって[色設定をタブ](settings.md#tab-color)です。
- 変更*サーバー名*に*サーバー*接続ダイアログでします。
- 修正プログラムの分類*現在のクエリの実行*コマンド。
- ドラッグ アンド ドロップの重大なバグのスクリプトを修正します。
- 不適切な修正プログラムは、[スタート] メニューのアイコンをピン留めします。
- 不足している Azure アカウントがアイコンをブランド化を修正します。


## <a name="december-2017-december-public-preview"></a>2017 年 12 月 (パブリック プレビューの年 12 月)

リリース日: 2017 年 12 月 19 日  
バージョン: 0.24.1

*年 12 月のパブリック プレビュー*次の機能強化もすべての機能領域の全体でいくつかのバグ修正が含まれています。

- 作成するファイアウォール ルール ダイアログは、Azure SQL Database と Azure SQL Data Warehouse への接続を支援するために使用できるようになりました。
- 追加の Windows セットアップと Linux DEB や RPM のインストール パッケージです。
- ダッシュ ボード ビジュアル レイアウト エディターを管理します。
- *スクリプトとして変更*と*スクリプトとして実行*コマンド。
- *実際のプランの現在のクエリを実行*コマンド。
- VS Code 1.18.1 エディター プラットフォームに統合します。
- VSIX 拡張機能のサイドローディング ファイルを有効にします。
- "N 移動"バッチ イテレーションの構文をサポートします。


## <a name="november-2017"></a>2017 年 11 月

リリース日: 2017 年 11 月 15 日  
バージョン: 0.23.6

- 初回のリリースの[!INCLUDE[name-sos](../includes/name-sos-short.md)]します。


## <a name="next-steps"></a>次の手順

作業を開始する次のクイック スタートのいずれかを参照してください。
- [接続し、クエリの SQL Server](quickstart-sql-server.md)
- [接続し、Azure SQL データベースの照会](quickstart-sql-database.md)
- [接続し、Azure データ ウェアハウスのクエリ](quickstart-sql-dw.md)

投稿[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio)
