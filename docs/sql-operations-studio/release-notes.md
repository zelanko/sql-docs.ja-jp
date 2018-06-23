---
title: Microsoft SQL Operations Studio (プレビュー) のリリース ノート |Microsoft ドキュメント
description: Microsoft SQL Operations Studio (プレビュー) のリリース ノート
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 29ae09022c18e5c96ffe4db25f59e6bfd619f432
ms.sourcegitcommit: d3432a37b23b61c37092daf7519b30fc42fc0538
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271013"
---
# <a name="sql-operations-studio-preview-release-notes"></a>SQL Operations Studio (プレビュー) のリリース ノート

**[年 6 月のパブリック プレビューをダウンロードします。](download.md)**


## <a name="june-2018-june-public-preview"></a>年 6 月 2018 (年 6 月のパブリック プレビュー)

リリース日: 2018 年 6 月 20日  
バージョン: 0.30.6

*年 6 月のパブリック プレビュー*次の点が含まれています。  

- **SQL Server Profiler for SQL 操作 Studio*プレビュー*** 拡張機能の初期リリースします。
- 新しい**SQL Data Warehouse**拡張機能には、豊富なダッシュ ボード ウィジェット提示、データ ウェアハウスへの洞察にはが含まれています。 これには、主要なシナリオを管理すると、一貫したパフォーマンス用に最適化を確実にデータ ウェアハウスのチューニングがロック解除します。
- **「フィルターと並べ替え」のデータを編集**をサポートします。
- **SQL 操作 Studio の SQL Server エージェント*プレビュー*** ジョブとジョブ履歴の拡張機能の拡張機能のビューです。
- 向上**ウィザードとダイアログ UI ビルダー フレームワーク**機能拡張 Api です。
- VS プラットフォーム コードのソース コードの統合を更新[年 2018年 3 月 (1.22)](https://code.visualstudio.com/updates/v1_22)と[年 2018年 4 月 (1.23)](https://code.visualstudio.com/updates/v1_23)を解放します。
- GitHub の問題を修正します。
  - 機能の要求 ([発行 1204](https://github.com/Microsoft/sqlopsstudio/issues/1204)): くださいする結果グリッド [自動調整] 列の幅、データや、同じクエリが再実行の場合、手動で変更を注意してください。
  - 修正[発行 1398](https://github.com/Microsoft/sqlopsstudio/issues/1398): 表示メッセージおよび追加リンクされているアカウントが空の場合は、アカウントのアカウント ボタンを追加します。
  - 修正[発行 1399](https://github.com/Microsoft/sqlopsstudio/issues/1399): ビューが折りたたまれているときに、リンクされているアカウント タブが壊れています。
  - 修正[発行 1374](https://github.com/Microsoft/sqlopsstudio/issues/1374): ディスクから .sql ファイルを開くときに、SQL ツール サービスがクラッシュします。
  - 修正[発行 1372](https://github.com/Microsoft/sqlopsstudio/issues/1372): 見つからない SQL キーワード"BETWEEN"です。
  - 修正[発行 1395](https://github.com/Microsoft/sqlopsstudio/issues/1395): 'MATCH' キーワードが SQL ツール サービスがクラッシュします。
  - 修正[発行 1496](https://github.com/Microsoft/sqlopsstudio/issues/1496): オブジェクト エクスプ ローラーで、「新しいプロファイラー」コンテキスト メニュー オプションは、何も行われません。
  - 修正[発行 1495](https://github.com/Microsoft/sqlopsstudio/issues/1495): クエリ エディターの「説明」クエリ プランが壊れています。


詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/sqlopsstudio/releases)です。


## <a name="may-2018-may-public-preview"></a>月 2018年 (パブリック プレビューの場合があります)

リリース日: 2018 月 7日  
バージョン: 0.29.3

*パブリック プレビューの場合があります*安定化とバグの修正にフォーカスが移動します。 このビルドには、次の点が含まれています。  

- Announcing Redgate SQL Search の拡張機能の拡張機能マネージャーで使用できます。
- 10 言語の使用可能なコミュニティ ローカリゼーション: ドイツ語、スペイン語、フランス語、イタリア語、日本語、韓国語、ポルトガル語、ロシア語、簡体字中国語、繁体字中国語です。
- 削減製品利用統計情報コレクション、オプトアウト エクスペリエンスの向上と製品内へのリンクのプライバシーに関する声明。
- 拡張機能マネージャーは、コミュニティの拡張機能を簡単に検出するエクスペリエンスが向上 Marketplace を持っています。
- 拡張機能の SQL エージェント ジョブとジョブ履歴は、改善を表示します。
- Whoisactive およびサーバーのレポートの拡張機能を更新します。
- 管理ダッシュ ボードのプロパティのスクロールが向上します。
- GitHub の問題を修正します。
   - 修正[発行 703](https://github.com/Microsoft/sqlopsstudio/issues/703): 値が正しく更新されるまで表示されないデータ編集の HTML のようなテキストを入力すると、
   - 修正[発行 821](https://github.com/Microsoft/sqlopsstudio/issues/821): sqlopsstudio.deb パッケージの依存関係
   - 修正[発行 1260](https://github.com/Microsoft/sqlopsstudio/issues/1260): 'distinct' 強調表示されていないキーワード
   - 修正[発行 1332](https://github.com/Microsoft/sqlopsstudio/issues/1332): データ編集を元に戻す行は機能しません
   - 修正[発行 1215](https://github.com/Microsoft/sqlopsstudio/issues/1215): SQL エージェントの拡張機能とステータス バー
   - 修正[発行 1316](https://github.com/Microsoft/sqlopsstudio/issues/1316): ウィンドウ サイズの変更後に SQL エージェントの今後のサイズを変更




## <a name="april-2018-april-public-preview"></a>年 4 月 2018 (年 4 月のパブリック プレビュー)

リリース日: 2018 年 4 月 25日  
バージョン: 0.28.6

*年 4 月のパブリック プレビュー*バグの修正プログラムと機能強化が含まれています。 

- SQL エージェント プレビュー拡張機能が改善されました。
- 保護されている管理者を保存するための大規模で保護されたファイルのサポートの向上と > SQL Operations Studio 内で 256 個のファイルです。
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
   - 修正[1068 を発行](https://github.com/Microsoft/sqlopsstudio/issues/1068): ダッシュ ボード出力 windows pop アップ for Azure SQL Database のエラー メッセージを使用します。
   - 修正[発行 1069](https://github.com/Microsoft/sqlopsstudio/issues/1069): 接続ダイアログが最初に表示されるときに必要なサーバー エラーを示しています。
   - 修正[発行 1070](https://github.com/Microsoft/sqlopsstudio/issues/1070): サーバー グループは今すぐ、ダブルクリックして展開を必要とします。
   - 修正[発行 1072](https://github.com/Microsoft/sqlopsstudio/issues/1072): 選択コントロールの背景が透明度の低い。
   - 修正[発行 1115](https://github.com/Microsoft/sqlopsstudio/issues/1115): SQL Operations Studio ですべてのハイ コントラスト ユーザー補助の問題を修正します。
   - 修正[発行 1101](https://github.com/Microsoft/sqlopsstudio/issues/1101): アップグレード「ダウンロード手動で」リンクに失敗する拡張機能が誤った場所に移動します。
   - 修正[発行 1103](https://github.com/Microsoft/sqlopsstudio/issues/1103): [ホーム] タブで作業していない V スクロールします。
   - 修正[発行 1104](https://github.com/Microsoft/sqlopsstudio/issues/1104): SQL 拡張機能のタブが動作を停止しました。


年 4 月のパブリック プレビューの重要な点では、Visual Studio コード 1.21 プラットフォームのソース コードの更新です。 以前の 1.19 同期ポイントからコア エディターとワークベンチに更新プログラムのいくつかで表示されます。 次に例をいくつか示します。

- [新しい通知 UI](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) - 簡単に管理および SQL Operations Studio の通知を確認します。
- [ターミナル分割を統合](https://code.visualstudio.com/updates/v1_21#_split-terminals)-複数開いている端末と同時に作業します。
- [大規模で保護されたファイルを保存](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) - 保護されている管理者を保存および > SQL Operations Studio 内で 256 個のファイルです。
- [大きなファイルのサポートが向上](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements)-サイズの大きなファイルのテキスト バッファーに最適化します。
- [設定の検索機能の向上](https://code.visualstudio.com/updates/v1_20#_settings-search)- 簡単に自然言語検索を使用して正しい設定を検索します。
- [グローバル スニペット](https://code.visualstudio.com/updates/v1_20#_global-snippets)-すべてのファイルの種類を使用することができますのスニペットを作成します。
- [エクスプ ローラーの複数選択](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer)-一度に複数のファイルに対してアクションを実行します。
- [エラーと警告エクスプ ローラーで](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer)すばやくコード ベースでのエラーに移動します。
- [ドラッグ ドロップ、コピー & windows 全体に貼り付け](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support)-SQL Operations Studio の開いているウィンドウ間でファイルを移動します。
- [Git のサブモジュール サポート](https://code.visualstudio.com/updates/v1_20#_git-submodules)-入れ子になったの Git リポジトリでの Git の実行操作。
- [ターミナル スクリーン リーダーのサポート](https://code.visualstudio.com/updates/v1_20#_screen-reader-support)-統合ターミナルよう「スクリーン リーダーの最適化」モードになりました。
- [中央揃えエディター レイアウト](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout)-実際の画面を表示するコードを最大化します。
- [水平方向の検索結果 (プレビュー)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) -今すぐ横方向パネルの 検索結果を表示することができます。

詳細については、チェック アウト、 [Visual Studio コード年 2 月のリリース ノート](https://code.visualstudio.com/updates/v1_21)、および[Visual Studio コード年 1 月リリース ノート](https://code.visualstudio.com/updates/v1_20)です。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/sqlopsstudio/blob/master/CHANGELOG.md)です。

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
