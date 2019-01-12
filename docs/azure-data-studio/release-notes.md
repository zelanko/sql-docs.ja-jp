---
title: リリース ノートと変更ログ
titleSuffix: Azure Data Studio
description: Azure Data Studio リリース ノート
ms.custom: seodec18
ms.date: 01/10/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 63cf17e26ce554b901a3c9cc6db1fcb18162140d
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143662"
---
# <a name="azure-data-studio-latest-release-notes-and-changelog"></a>Azure Data Studio の最新のリリース ノートと、変更ログ

**[1 月のリリースをダウンロードしてください。](download.md)**


## <a name="january-2019-january-release"></a>2019 年 1 月 (1 月リリース)

リリース日:2019 年 1 月 9日  
バージョン：1.3.8

- Windows のユーザーの新しいインストーラーを追加します。 既存のシステムのインストーラーとは異なり、新しいユーザーのインストーラーに管理者特権は必要ありません。 これにより、管理者以外のユーザーより簡単なアップグレード エクスペリエンスができます。
- Azure Active Directory 認証のサポート。
- Idera SQL DM パフォーマンス Insights (プレビュー) をお知らせします。
- SQL Server インポート拡張機能のサポートにデータ層アプリケーションのウィザード。
- 更新する、 [SQL Server 2019 プレビュー拡張機能](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- SQL Server Profiler の機能強化。
- 大規模なクエリ (プレビュー) のストリームの結果。
- コミュニティの拡張機能: sp_executesql to sql と新しいデータベース。
- 解決[バグし、問題](https://github.com/Microsoft/azuredatastudio/milestone/19?closed=1)します。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/azuredatastudio/releases)します。

## <a name="november-2018-november-release"></a>2018 年 11 月 (11 月のリリース)

リリース日:2018 年 11 月 6 日  
バージョン：1.2.4

- 更新する、 [SQL Server 2019 プレビュー拡張機能](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- 貼り付けプランの拡張機能の概要
- SSMS のエディター テーマを含め、High Color クエリ拡張機能の概要
- SQL Server エージェント、Profiler、およびインポートの拡張機能での修正します。
- .Net Core を修正する macOS で非アクティブな接続を削除するソケット KeepAlive 問題の原因
- .Net Core へのアップグレードの SQL ツール サービス 2.2 Preview 3 (の最終的な AAD サポート)

### <a name="bug-fixes"></a>バグの修正

- 修正[発行 #2933](https://github.com/Microsoft/azuredatastudio/issues/2933):接続が Azure SQL DB に失われました
- 修正[発行 #2914](https://github.com/Microsoft/azuredatastudio/issues/2914):「無効な引数」例外拡大 OE データベース ノード
- 修正[発行 #2935](https://github.com/Microsoft/azuredatastudio/pull/2935):クエリの結果に複数行のメッセージを正しく表示します。
- 修正[発行 #2906](https://github.com/Microsoft/azuredatastudio/pull/2906):テーブル名に特殊文字が含まれている場合は、データの編集ドキュメント名を修正します。
- 修正[発行 #2929](https://github.com/Microsoft/azuredatastudio/issues/2929):ビルド拡張機能で、変更ログが VSCode のリリース ノートの変更を確認するという
- 修正[発行 #2719](https://github.com/Microsoft/azuredatastudio/issues/2719):ハイ コントラスト テーマ double/3 要素のアイコン
- 修正[発行 #3047](https://github.com/Microsoft/azuredatastudio/pull/3047):SQL Server に接続するためのコマンド ライン インターフェイスの追加します。
- 修正[発行 #3031](https://github.com/Microsoft/azuredatastudio/pull/3031):クエリ プランのテーマのサポートを追加します。
- [...]

## <a name="october-2018-october-release"></a>10 月 2018 (年 10 月リリース)

リリース日:2018 年 10 月 29 日  
バージョン：1.1.4

- Azure SQL データベースを参照する Azure リソース エクスプ ローラーの概要
- オブジェクト エクスプ ローラーおよびクエリ エディターの接続の堅牢性を向上します。
- SQL エージェント拡張機能の機能強化
- 更新する、 [SQL Server 2019 プレビュー拡張機能](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)

### <a name="bug-fixes"></a>バグの修正
- 修正[発行 #2717](https://github.com/Microsoft/azuredatastudio/issues/2717):XML 列の結果は、書式設定 をクリックします。
- 修正[発行 #2993](https://github.com/Microsoft/azuredatastudio/issues/2993):結果ウィンドウの幅が完了していません
- 修正[発行 #2999](https://github.com/Microsoft/azuredatastudio/issues/2999):DB に接続するときに、Mac 上のファイル System.Diagnostics.Tracing を読み込めませんでした。
- 修正[発行 #2851](https://github.com/Microsoft/azuredatastudio/issues/2851):時系列のグラフが正しくレンダリングされません。
- 修正[発行 #2996](https://github.com/Microsoft/azuredatastudio/issues/2996):セッションが突然変更による損失を一時テーブル
- [...]

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/azuredatastudio/releases)します。

## <a name="september-2018-september-ga-release"></a>9 月 2018 (9 月 GA リリース)

リリース日:2018 年 9 月 24 日  
バージョン：1.0

Azure Data Studio (SQL Operations Studio 以前) の一般的な可用性リリースします。

- SQL Server 2019 プレビュー拡張機能をお知らせします。
  - 含む SQL Server 2019 プレビュー機能のサポートを[ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)をサポートします。
    - SQL Server 2019 プレビューに付属する HDFS/Spark ゲートウェイに接続します。
    - HDFS の参照、ファイルのアップロード、ファイルを保存し、CSV ファイルのノートブックで分析などの役に立つアクションを起動します。
    - ダッシュ ボードからの Spark ジョブを送信またはオブジェクト エクスプ ローラーでの HDFS/Spark 接続を右クリックします。
  - Azure Data Studio Notebook
    - 作成または、統合された Notebook のビューアーを使用して Notebook を開きます。 このリリースのノートブックでは、ビューアーは、ローカル カーネルと、SQL Server 2019 のビッグ データ クラスターに対してのみへの接続をサポートします。
    - ノートブックで PROSE コード アクセラレータ ライブラリを使用して、高速なデータ準備のためのファイル形式とデータ型を参照してください。
  - Azure リソース エクスプ ローラー
    - Azure リソース エクスプ ローラー ビューでは、Azure アカウントのデータに関連するエンドポイントを参照し、オブジェクト エクスプ ローラーでそれらへの接続を作成できます。 このリリースでは、Azure SQL データベースとサーバーをサポートします。
  - SQL Server PolyBase 外部テーブルのウィザードを作成します。
    - 使いやすいウィザードでは、外部テーブルとその関連のメタデータ構造体を作成します。 このリリースでは、リモートの SQL Server、Oracle サーバーがサポートされます。
- クエリ結果グリッド パフォーマンスおよび結果セットの数が多いため、UX の機能強化。
- Visual Studio Code のソース コードは、1.23 から 1.26.1 とグリッド レイアウトと向上の設定エディター (プレビュー) を更新します。
- スクリーン リーダー、キーボード ナビゲーションとハイ コントラストのアクセシビリティ機能改善します。
- 追加`Connection name`サーバーのビューとで代替表示名を指定するオプション。

### <a name="bug-fixes"></a>バグの修正

- 修正[発行 #2647](https://github.com/Microsoft/azuredatastudio/issues/143):グラフでは、大きな一歩を下位かかりました。
- 修正[発行 #2648](https://github.com/Microsoft/azuredatastudio/issues/143):JSON ハイパーリンク列全体を返すことを選択します。
- [...]

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/azuredatastudio/releases)します。


## <a name="august-2018-august-public-preview"></a>8 月 2018 (パブリック プレビューの年 8 月)

リリース日:2018 年 8 月 30 日  
バージョン：0.32.8

*0.32.8 には 0.32.7 で見つかったいくつかの回帰の修正プログラムが含まれています ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971)、 [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372)*)

*年 8 月のパブリック プレビュー*バグの修正、製品の安定化、および既存のシナリオのギャップを入力します。  

- SQL Server インポート拡張機能の発表
- SQL Server Profiler のセッションの管理
- SQL Server Profiler セッション テンプレートのサポート
- SQL Server エージェントの機能強化
- コミュニティの新しい拡張機能:最初の応答側キット
- 生活の質の改良:接続文字列

### <a name="bug-fixes"></a>バグの修正

- 使用して SQL クエリ エディター ウィンドウ内の解析、`Parse Syntax`コマンド。
- 修正[発行 #143](https://github.com/Microsoft/azuredatastudio/issues/143):変数名で選択しない をダブルクリックします。
- 修正[発行 #387](https://github.com/Microsoft/azuredatastudio/issues/387):SQL タブ DB アイコンが赤です。
- 修正[#825 を発行](https://github.com/Microsoft/azuredatastudio/issues/825):要求:現在のサーバーとしてのスクリプトの後に自動接続しています. 
- 修正[発行 #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [デスクトップ エントリ] - 名前とコメントの冗長の値。
- 修正[発行 #1285](https://github.com/Microsoft/azuredatastudio/issues/1285):Windows での削除/置換のある原因がアプリケーション アイコンを更新しています。
- 修正[発行 #1317](https://github.com/Microsoft/azuredatastudio/issues/1317):10 進数の区切り記号を修正します。
- 修正[発行 #1474](https://github.com/Microsoft/azuredatastudio/issues/1474):接続の変更をキャンセルでは、現在の接続を切断します。
- 修正[発行 #1497](https://github.com/Microsoft/azuredatastudio/issues/1497):下部にあるオプションは切り捨てられますグラフとして表示されます。
- 修正[発行 #1524](https://github.com/Microsoft/azuredatastudio/issues/1524):シェル/ダッシュ ボード:メイン viewlet アイコンは、ドラッグ可能なアプリがクラッシュすることができます。
- 修正[発行 #1578](https://github.com/Microsoft/azuredatastudio/issues/1578):名前をクリックしてリモート ファイル ブラウザー フォルダーの展開/折りたたみことができません。
- 修正[発行 #1620](https://github.com/Microsoft/azuredatastudio/issues/1620):機能の修正候補:既存の接続には、接続文字列を取得します。
- 修正[発行 #1624](https://github.com/Microsoft/azuredatastudio/issues/1624):ください ボックスには、無効にした場合の色を変更しません。
- 修正[発行 #1728](https://github.com/Microsoft/azuredatastudio/issues/1728):JSON/EXCEL/CSV 作業していないとして保存します。
- 修正[発行 #1744](https://github.com/Microsoft/azuredatastudio/issues/1744):結果ウィンドウでは、タブを切り替えるときに、スクロールの位置が失われます。
- 修正[発行 #1748](https://github.com/Microsoft/azuredatastudio/issues/1748):Excel ファイルを 2 回目 (以降) の時間を保存するときのエラー メッセージ。
- 修正[発行 # ~ 1782](https://github.com/Microsoft/azuredatastudio/issues/1782):データの編集: エスケープ キーを押すことで元の値にセルが元に戻します。
- 修正[発行 #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): .sql ファイルが SQL Operations Studio と関連付けられていません。
- 修正[発行 #1850](https://github.com/Microsoft/azuredatastudio/issues/1850):入力 N 'オートコンプリートを N' '。
- 修正[発行 #1985](https://github.com/Microsoft/azuredatastudio/issues/1985):クエリ結果のグリッドが 1 つの列で無効になってからコピーします。
- 修正[発行 #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998):VS Code のバージョンをバージョン情報ダイアログを追加します。
- 修正[発行 #2042](https://github.com/Microsoft/azuredatastudio/pull/2042):エージェント:Sql ファイルからクエリをインポートする ボタンを有効になります。
- 修正[発行 #2091](https://github.com/Microsoft/azuredatastudio/issues/2091):結果ウィンドウからコピーするショートカットの CTRL + C を使用できません。
- 修正[発行 #2099](https://github.com/Microsoft/azuredatastudio/pull/2099):その他の saveAsCsv オプションが追加されます。
- 修正[発行 #2107](https://github.com/Microsoft/azuredatastudio/issues/2107):ダッシュ ボードと Profiler のドキュメントのドキュメント アイコンを更新します。
- 修正[発行 #2129](https://github.com/Microsoft/azuredatastudio/pull/2129):タブの切り替えは、データのスクロール位置の編集を保存します。
- 修正[発行 #2152](https://github.com/Microsoft/azuredatastudio/issues/2152):結果のグリッド行インジケーター 0 から始まります。

### <a name="known-issues"></a>既知の問題

- [発行 #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) Excel のデータの先頭行のみを保存して保存.
- [発行 #2150](https://github.com/Microsoft/azuredatastudio/issues/2150):コンテナー内の SQL を Ubuntu 16.04 に接続できません。


## <a name="july-2018-july-public-preview"></a>2018 年 7 月 (7 月のパブリック プレビュー)

リリース日:2018 年 7 月 19 日  
バージョン：0.31.4

*年 7 月のパブリック プレビュー*顧客に GitHub の問題が報告される構成シナリオの SQL Server エージェント、SQL Server Profiler のセッションとビュー テンプレートの強化、および継続的なバグの修正の初期リリースに重点を置いています。 このリリースには、次の主なトピックが含まれています。  

- [SQL Operations Studio の拡張機能の SQL Server エージェント](sql-server-agent-extension.md)の機能強化
 - アラート、演算子、およびプロキシおよびアイコンの左側のウィンドウで追加のビュー
 - 新しいジョブを新しいジョブ ステップ、新しいアラート、および新しい演算子のダイアログの追加
 - 追加されたジョブの削除、通知の削除、および Delete 演算子 (右クリック)
 - 追加した以前の実行の視覚化
 - それぞれの列名の追加のフィルター
- [SQL Operations Studio の拡張機能の SQL Server Profiler](sql-server-profiler-extension.md)の機能強化
 - 起動と Profiler の起動/停止を迅速に追加されたホット キー
 - 拡張イベントを表示する 5 つの既定のテンプレートの追加
 - 追加のサーバー/データベース接続名
 - Azure SQL Database インスタンスのサポートが追加されました
 - Profiler がまだ実行されているときにタブが閉じられたときに、Profiler を終了する候補を追加しました
- 結合スクリプト拡張機能のリリース
- 拡張機能の作成者の追加ウィザードとダイアログの機能拡張ポイント
- GitHub の問題を修正するには。
 - 修正[発行 728](https://github.com/Microsoft/azuredatastudio/issues/728):MacOS で追加の接続に応答がありません。
 - 修正[1612 を発行](https://github.com/Microsoft/azuredatastudio/issues/1612):結果グリッド テキストの表示は国際文字、にくかった
 - 修正[発行 1693](https://github.com/Microsoft/azuredatastudio/issues/1693):バックアップ ダイアログ ボックス:ファイル ブラウザー UI が壊れています
 - 修正[発行 1713](https://github.com/Microsoft/azuredatastudio/issues/1713):影響を受ける行の数
 - 修正[発行 1718](https://github.com/Microsoft/azuredatastudio/issues/1718):任意のデータ ソースに接続できません。
 - 修正[発行 1719](https://github.com/Microsoft/azuredatastudio/issues/1719):サーバーに接続するときに、TypeError
 - 修正[発行 1724](https://github.com/Microsoft/azuredatastudio/issues/1724):ダイアログの拡張機能が動作を停止しました
 - 修正[発行 1749](https://github.com/Microsoft/azuredatastudio/issues/1749):バグ:列内の HTML データが解釈されます。
 - 修正[発行 1789](https://github.com/Microsoft/azuredatastudio/issues/1789):機能拡張: 接続プロバイダーを追加する場合アンインストールは決して一覧から削除、
 - 修正[発行 1791](https://github.com/Microsoft/azuredatastudio/issues/1791):Sqlops 拡張機能: が queryeditor.connect() が、ターゲット データベースに接続しますが、UI は、エディターの接続を表示しません。
 - 修正[発行 1799](https://github.com/Microsoft/azuredatastudio/issues/1799):上位 10 個の DB サイズのグラフは、大文字小文字を区別するインスタンスでは動作しません
 - 修正[発行 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): sqlops.d.ts 入力ミスが原因で暗黙的な 'any' 型の定義
 - 修正[発行 1817](https://github.com/Microsoft/azuredatastudio/issues/1817):エラー de Ortografia
 - 修正[発行 1830](https://github.com/Microsoft/azuredatastudio/issues/1830):Component() が呼び出された後、ButtonComponent で iconPath を設定してもアイコンは変更されません。
 - 修正[発行 1843](https://github.com/Microsoft/azuredatastudio/issues/1843):効率的なテーブルの整理


## <a name="june-2018-june-public-preview"></a>2018 年 6 月 (6 月のパブリック プレビュー)

リリース日:2018 年 6 月 20 日  
バージョン：0.30.6

*年 6 月のパブリック プレビュー*次の主なトピックが含まれています。  

- **SQL Operations Studio の SQL Server Profiler*プレビュー*** 拡張機能の初期リリースします。
- 新しい**SQL Data Warehouse**拡張機能には、data warehouse への洞察を提示充実したカスタマイズ可能なダッシュ ボードのウィジェットが含まれています。 これには、管理と一貫したパフォーマンスの最適化されて ことを確認するデータ ウェアハウスのチューニングに関する主なシナリオがロック解除します。
- **データの「フィルター処理と並べ替え」を編集**をサポートします。
- **SQL Operations Studio の SQL Server エージェント*プレビュー*** ジョブおよびジョブ履歴の拡張機能のビュー。
- 改善**ウィザードとダイアログの UI ビルダー Framework**拡張 Api。
- VS プラットフォーム コードのソース コードの統合を更新[2018 年 3 月 (1.22)](https://code.visualstudio.com/updates/v1_22)と[2018 年 4 月 (1.23)](https://code.visualstudio.com/updates/v1_23)を解放します。
- GitHub の問題を修正するには。
  - 機能の要求 ([発行 1204](https://github.com/Microsoft/azuredatastudio/issues/1204))。同じクエリを再実行している場合は、手動で変更を注意してくださいまたはこのデータを結果グリッドの自動調整の列の幅を行うことが。
  - 修正[発行 1398](https://github.com/Microsoft/azuredatastudio/issues/1398):必要がありますショーはメッセージを追加し、リンクされているアカウントが空の場合は、アカウントのアカウント ボタンを追加します。
  - 修正[発行 1399](https://github.com/Microsoft/azuredatastudio/issues/1399):ビューが折りたたまれているときに、リンクされたアカウント タブは解除されます。
  - 修正[発行 1374](https://github.com/Microsoft/azuredatastudio/issues/1374):ディスクから、.sql ファイルを開くときに、SQL ツール サービスがクラッシュします。
  - 修正[発行 1372](https://github.com/Microsoft/azuredatastudio/issues/1372):SQL キーワード"BETWEEN"がありません。
  - 修正[発行 1395](https://github.com/Microsoft/azuredatastudio/issues/1395):一致' キーワードは、SQL ツール サービスがクラッシュします。
  - 修正[発行 1496](https://github.com/Microsoft/azuredatastudio/issues/1496):"新しい Profiler"コンテキスト メニュー オプションは、オブジェクト エクスプ ローラーでは、何も行われません。
  - 修正[発行 1495](https://github.com/Microsoft/azuredatastudio/issues/1495):クエリ エディターの「説明」クエリ プランが壊れています。


## <a name="may-2018-may-public-preview"></a>2018 年 5 月 (パブリック プレビュー 5 月)

リリース日:2018 年 5 月 7 日  
バージョン：0.29.3

*パブリック プレビューの可能性があります*安定化とバグの修正に重点を置いています。 このビルドには、次の主なトピックが含まれています。  

- Redgate SQL Search 拡張機能の使用可能な拡張機能マネージャーにお知らせします。
- コミュニティのローカリゼーションの 10 言語使用できます。ドイツ語、スペイン語、フランス語、イタリア語、日本語、韓国語、ポルトガル語、ロシア語、簡体字の中国語と繁体字中国語します。
- 削減テレメトリの収集、オプトアウトのエクスペリエンスの向上、およびプライバシーに関する声明への製品内リンク。
- 拡張機能マネージャーでは、強化された Marketplace のコミュニティの拡張機能を簡単に検出するエクスペリエンスがあります。
- 拡張機能の SQL エージェント ジョブとジョブ履歴は、改善を表示します。
- Whoisactive とサーバー レポートの拡張機能を更新します。
- 管理ダッシュ ボードのプロパティのスクロールが向上します。
- GitHub の問題を修正するには。
   - 修正[703 の発行](https://github.com/Microsoft/azuredatastudio/issues/703):値が正しく更新されるまで表示されないデータ編集で HTML のようなテキストを入力すると、します。
   - 修正[発行 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb パッケージの依存関係
   - 修正[発行 1260](https://github.com/Microsoft/azuredatastudio/issues/1260):キーワード 'distinct' は強調表示されていません。
   - 修正[発行 1332](https://github.com/Microsoft/azuredatastudio/issues/1332):データの編集を元に戻す行は機能しません
   - 修正[発行 1215](https://github.com/Microsoft/azuredatastudio/issues/1215):SQL エージェントの拡張機能とステータス バー
   - 修正[発行 1316](https://github.com/Microsoft/azuredatastudio/issues/1316):Windows のサイズを変更した後、SQL エージェントの今後のサイズ変更




## <a name="april-2018-april-public-preview"></a>2018 年 4 月 (年 4 月のパブリック プレビュー)

リリース日:2018 年 4 月 25 日  
バージョン：0.28.6

*年 4 月のパブリック プレビュー*バグ修正と改善が含まれています。 

- SQL エージェント プレビュー拡張機能の改善。
- 保護されている管理者を保存するための大規模で保護されたファイルのサポートの向上と > SQL Operations Studio 内で 256 個のファイルです。
- 統合ターミナルを一度に複数のオープン端末で作業を分割します。
- 高速インストールおよびスタートアップに時間の削減インストール ディスク上のファイル数フィートを印刷します。
- 続行すると、GitHub の問題を修正します。
   - 修正[発行 37](https://github.com/Microsoft/azuredatastudio/issues/37):グラフ ビューアーは、エラーをスローするときに予期しない動作が発生します。
   - 修正[発行 462](https://github.com/Microsoft/azuredatastudio/issues/462):機能要求:既定で展開するサーバー グループのオプションです。
   - 修正[発行 606](https://github.com/Microsoft/azuredatastudio/issues/606): intellisense、'update' コマンドの不適切な修正候補。
   - 修正[発行 967](https://github.com/Microsoft/azuredatastudio/issues/967):クエリ プランを予想される結果のグリッドで XML プラン表示を選択するとします。
   - 修正[発行 1023](https://github.com/Microsoft/azuredatastudio/issues/1023):Flyfishingdba から ms_foreachdb 呼び出しに角かっこを追加します。
   - 修正[発行 1048](https://github.com/Microsoft/azuredatastudio/issues/1048):SSL や TLS ハンドシェイクの前のログイン エラー。
   - 修正[発行 1050](https://github.com/Microsoft/azuredatastudio/issues/1050):クリア insights は、エラーを表示する前に表示します。
   - 修正[発行 1057](https://github.com/Microsoft/azuredatastudio/issues/1057):復元とエクスプ ローラー ウィジェットで新しいクエリのアクションが壊れています。
   - 修正[発行 1068](https://github.com/Microsoft/azuredatastudio/issues/1068):ダッシュ ボード出力 windows pop アップし、Azure SQL Database のエラー メッセージ。
   - 修正[発行 1069](https://github.com/Microsoft/azuredatastudio/issues/1069):接続ダイアログには、最初に表示されるときに必要なサーバー エラーが表示されます。
   - 修正[発行 1070](https://github.com/Microsoft/azuredatastudio/issues/1070):サーバー グループには、ダブルクリックを展開するようになりましたが必要です。
   - 修正[発行 1072](https://github.com/Microsoft/azuredatastudio/issues/1072):選択コントロールの背景が半透明にします。
   - 修正[発行 1115](https://github.com/Microsoft/azuredatastudio/issues/1115):SQL Operations Studio のすべてのハイ コントラストのアクセシビリティの問題を修正します。
   - 修正[発行 1101](https://github.com/Microsoft/azuredatastudio/issues/1101):アップグレード「ダウンロード手動で」リンクに失敗する拡張機能は、間違った場所に移動します。
   - 修正[発行 1103](https://github.com/Microsoft/azuredatastudio/issues/1103):[ホーム] タブで作業していない V スクロールします。
   - 修正[発行 1104](https://github.com/Microsoft/azuredatastudio/issues/1104):SQL 拡張機能のタブは、動作を停止しました。


4 月のパブリック プレビューの重要な強調表示は、Visual Studio コード 1.21 プラットフォームのソース コードの更新です。 以前 1.19 同期ポイントからのコア エディターおよび workbench にいくつかの更新プログラムが表示されます。 いくつかの例を以下に示します。

- [新しい通知 UI](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) - 簡単に管理および SQL Operations Studio の通知を確認します。
- [統合ターミナル分割](https://code.visualstudio.com/updates/v1_21#_split-terminals)-オープン端子を複数同時に作業します。
- [大規模で保護されたファイルを保存](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) - 保護されている管理者を保存および > SQL Operations Studio 内で 256 個のファイルです。
- [大きなファイルのサポートを強化](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements)-大きなファイルのテキスト バッファーの最適化。
- [設定の検索機能の向上](https://code.visualstudio.com/updates/v1_20#_settings-search)- 簡単に自然言語検索を適切な設定を見つけます。
- [グローバル スニペット](https://code.visualstudio.com/updates/v1_20#_global-snippets)-すべてのファイルの種類で使用することができますのスニペットを作成します。
- [エクスプ ローラーの複数選択](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer)一度に複数のファイルで操作を実行します。
- [エラーと警告エクスプ ローラーで](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer)すばやくコード ベースでのエラーに移動します。
- [ドラッグ ドロップ、コピー & windows 全体に貼り付け](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support)-SQL Operations Studio の開いているウィンドウ間でファイルを移動します。
- [Git のサブモジュール サポート](https://code.visualstudio.com/updates/v1_20#_git-submodules)-入れ子になったの Git リポジトリで Git の実行操作。
- [ターミナル スクリーン リーダーのサポート](https://code.visualstudio.com/updates/v1_20#_screen-reader-support)-統合ターミナルが「スクリーン リーダーの最適化」モードになりました。
- [エディターの中央揃えのレイアウト](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout)-実際の画面を表示するコードを最大化します。
- [水平方向の検索結果 (プレビュー)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) -今すぐ横方向パネルの 検索結果が表示することができます。

詳細については、チェック アウト、 [Visual Studio Code 年 2 月のリリース ノート](https://code.visualstudio.com/updates/v1_21)、および[Visual Studio Code 年 1 月のリリース ノート](https://code.visualstudio.com/updates/v1_20)します。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)します。

## <a name="march-2018-march-public-preview"></a>2018 年 3 月 (パブリック プレビューの年 3 月)

リリース日:2018 年 3 月 28 日  
バージョン：0.27.3

*年 3 月のパブリック プレビュー*最上位の GitHub の問題に対処する続行し、機能拡張アジャイル チームのストーリーの向上に重点を置いています。 具体的には、ダッシュ ボードの管理を向上し、SQL エージェント、insights 拡張機能を提供する、拡張機能マネージャーを有効にします。 このリリースには、次の機能強化が含まれています。

- タブ付き insights と構成ウィンドウをサポートするためにダッシュ ボードの機能拡張モデルを強化します。
   - 拡張機能マネージャーでは、拡張機能の簡単な取得できるようにします。
   - ダッシュ ボード拡張機能から sp_whoisactive [whoisactive.com](http://www.whoisactive.com)します。
   - 詳細については、「 [SQL Operations Studio の機能拡張](extensions.md)です。
- さらに追加[接続およびオブジェクト エクスプ ローラーの機能拡張 Api](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API)管理します。
- 影響を与える重要な顧客の修正を続行[GitHub の懸案事項](https://github.com/Microsoft/azuredatastudio/issues)します。


## <a name="february-2018-february-public-preview"></a>2018 年 2 月 (パブリック プレビューの年 2 月)

リリース日:2018 年 2 月 15 日  
バージョン：0.26.7

*年 2 月のパブリック プレビュー*いくつかの機能の候補と優先度の高いバグの修正が含まれています。 このリリースには、次の機能強化が含まれています。

- 自動更新のインストールの概要を提供する通知を新しいリリースができるように、ダウンロード 
- 接続ダイアログの 'Database' フィールドは、指定されたサーバーから設定されたデータベースの一覧を含む動的に設定されているドロップダウン リストではようになりました。
- 修正[発行 6](https://github.com/Microsoft/azuredatastudio/issues/6):新しいクエリ タブを開くときに、接続および選択したデータベースを保持します。
- 修正[発行 22](https://github.com/Microsoft/azuredatastudio/issues/22):'Server Name' と 'Database_name' はこれらのドロップダウン テキスト ボックスではなくでしょうか。
- 修正[発行 549](https://github.com/Microsoft/azuredatastudio/issues/549):サイレント/非常にサイレント インストールは、インストール後に元のアプリケーションで発生します。
- 修正[発行 481](https://github.com/Microsoft/azuredatastudio/issues/481):「更新プログラムの確認」オプションを追加します。
- SQL エディターの色づけとオート コンプリートの修正:
   - 修正[発行 584](https://github.com/Microsoft/azuredatastudio/issues/584):キーワードが IntelliSense によって強調表示「完全」されません。
   - 修正[発行 345](https://github.com/Microsoft/azuredatastudio/issues/345):エディター内での SQL 関数を色分けして表示します。
   - 修正[発行 300](https://github.com/Microsoft/azuredatastudio/issues/300): [#tempData] 最新"]"緑の色が表示されます。
   - 修正[発行 225](https://github.com/Microsoft/azuredatastudio/issues/225):キーワードの色が一致しません。
   - 修正[発行 60](https://github.com/Microsoft/azuredatastudio/issues/60):無効な sql 構文の色の強調表示の from 句内の一時テーブルを使用する場合。
- 接続の機能拡張 API を紹介します。
- VS コード エディター 1.19 の統合。
- いくつかのクエリ プラン ビューアーの機能強化を回収する JustinPealing html-クエリのプランのコンポーネントに更新します。


## <a name="january-2018-january-public-preview"></a>2018 年 1 月 (1 月のパブリック プレビュー)

リリース日:2018 年 1 月 17 日  
バージョン：0.25.4

*年 1 月のパブリック プレビュー*いくつかの機能の候補と優先度の高いバグの修正が含まれています。 このリリースには、次の機能強化が含まれています。

- 保存されたサーバーの接続、接続ダイアログで利用できます。
- ホットな終了を有効にします。 ホットな終了は参照を有効にする、既定で無効[ホット終了設定](settings.md#hot-exit)します。
- サーバー グループに基づくをタブの色指定します。 既定では、「」を参照を有効にする タブの色分けはオフです[色設定をタブ](settings.md#tab-color)します。
- 変更*サーバー名*に*Server*接続 ダイアログ ボックス。
- 修正プログラムの分類*現在のクエリの実行*コマンド。
- ドラッグ アンド ドロップの重大なバグのスクリプトを修正します。
- [スタート] メニューのアイコンをピン留めする修正プログラムが正しくありません。
- 不足している Azure アカウントがアイコンのブランドを修正します。


## <a name="december-2017-december-public-preview"></a>2017 年 12 月 (12 月のパブリック プレビュー)

リリース日:2017 年 12 月 19 日  
バージョン：0.24.1

*年 12 月のパブリック プレビュー*以下の機能強化もすべての機能領域の全体でいくつかのバグ修正が含まれています。

- 作成するファイアウォール ルール ダイアログは、Azure SQL Database と Azure SQL Data Warehouse への接続を支援するために使用できるようになりました。
- 追加の Windows セットアップでは、および Linux DEB と RPM のインストール パッケージです。
- ダッシュ ボードの視覚的なレイアウト エディターを管理します。
- *スクリプトとして変更*と*スクリプトとして実行*コマンド。
- *実際のプランで現在のクエリを実行*コマンド。
- VS Code 1.18.1 エディター プラットフォームを統合します。
- ファイルの VSIX 拡張機能のサイドローディングを有効にします。
- "移動 N"バッチのイテレーションの構文をサポートします。


## <a name="november-2017"></a>2017 年 11 月

リリース日:2017 年 11 月 15 日  
バージョン：0.23.6

- 初回のリリースの[!INCLUDE[name-sos](../includes/name-sos-short.md)]します。


## <a name="next-steps"></a>次の手順

開始する次のクイック スタートのいずれかを参照してください。
- [接続および SQL Server のクエリ](quickstart-sql-server.md)
- [接続および Azure SQL Database のクエリ](quickstart-sql-database.md)
- [接続し、Azure Data Warehouse に対するクエリ](quickstart-sql-dw.md)

投稿する[!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
