---
title: リリース ノート
titleSuffix: Azure Data Studio
description: Azure Data Studio リリース ノート
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 05/08/2019
ms.openlocfilehash: d3451fcc6ca506e038ab614183007aad81880231
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454725"
---
# <a name="release-notes-for-azure-data-studio"></a>Azure Data Studio のリリース ノート

**[最新のリリースをインストールをダウンロードしてください。](download.md)**

## <a name="may-2019"></a>2019 年 5 月

2019 年 5 月 8日&nbsp;  /  &nbsp;バージョン。1.7.0 

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| スキーマ比較の拡張機能のリリース | スキーマ比較は SQL Server Data Tools (SSDT) でよく知られている機能であり、基本的なユース ケースを比較して、データベースや .dacpac ファイルの違いを視覚化して、同じことにアクションを実行するは。 |
| タスクの表示を出力ウィンドウに移動 | ユーザーは、タスク ビュー [出力] ウィンドウで、バックアップ、復元、およびスキーマ比較などの実行時間の長いタスクの状態を表示できますようになりました
| [ようこそ] ページの追加 | &bull; &nbsp; 一般的な操作へのリンクなどの新しい Notebook の新しいファイルは、新しいクエリ <br/>&bull; &nbsp; ドキュメントおよび Github へのリンク |
| SQL のノートブック機能強化 | &bull; &nbsp; メモとテーブルに対する優れたサポートをなど、マークダウン レンダリング機能強化 <br/>&bull; &nbsp; ツールバーにユーザビリティの強化 <br/>&bull; &nbsp; 信頼されている notebook を不要になったマークダウン リンク Cmd/ctrl キー + をクリックし、直接クリックすることができます。 <br/>&bull; &nbsp; Notebook を終了し、同時に複数のノートブックを開始するときにエラーを削減後のクリーンアップを Jupyter プロセスの強化 <br/>&bull; &nbsp; 同じデータベースに対して 2 つのノートブックを実行している場合にエラーを確認します。 SQL notebook 接続の機能強化は発生しません <br/>&bull; &nbsp; 自動スクロールを現在実行中のセルに、ツールバーから [セルの実行] ボタンをクリックすると notebook の機能強化 <br/>&bull; &nbsp; 全般的な安定性とパフォーマンスの向上 |
| 解決済みバグと問題。 | 参照してください[バグと github の問題](https://github.com/microsoft/azuredatastudio/milestone/31?closed=1)します。 |
| &nbsp; | &nbsp; |

## <a name="april-2019"></a>2019 年 4 月

2019 年 4 月 18日&nbsp;  /  &nbsp;バージョン。1.6.0 

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 名前が変更**サーバー**タブ**接続** | |
| [接続] での Azure の viewlet としての Azure リソース エクスプ ローラーの移動 | ユーザーの接続ビューでの Azure viewlet を通じて、Azure SQL インスタンスの表示し、下にある各サーバーまたはデータベース オブジェクトの表示を拡張できますようになりました。|
| SQL のノートブック機能強化 | &bull; &nbsp; すべてのセルの出力をクリアするにはツールバーに追加したボタン <br/>&bull; &nbsp; すべてのセルを実行するにはツールバーに追加したボタン <br/>&bull; &nbsp; サーバー名の代わりに固定接続名 (場合に設定) で、ドロップダウン リストにアタッチ <br/>&bull; &nbsp; イメージの相対パスを使用する場合は表示されません markdown でイメージの修正 <br/>&bull; &nbsp; 改善された機能を追加して notebook グリッド内では、列のサイズを自動サイズ変更をダブルクリックし、マウス ホイールのサポートを強化 <br/>&bull; &nbsp; Notebook から python をインストールする場合、エラー処理と python の機能強化が回復性をインストールします。 <br/>&bull; &nbsp; Notebook セルを選択するときにすべてを選択 機能を強化 <br/>&bull; &nbsp; ノートブックを閉じると、オブジェクト エクスプ ローラーの接続に影響を与えるを防止するノートブック接続の機能強化 <br/>&bull; &nbsp; 強化された notebook が発生するノートブックが切断され、セルを実行する接続が必要である場合、ユーザーにメッセージを表示するには<br/>&bull; &nbsp; 広告がもう一度開始されると、広告のリハイド レートするノートブックが保存されていないサポートの強化 |
| 解決済みバグと問題。 | 参照してください[バグと github の問題](https://github.com/Microsoft/azuredatastudio/milestone/26?closed=1)します。 |
| &nbsp; | &nbsp; |

## <a name="march-2019-hotfix"></a>3 月 2019 (修正プログラム)

2019 年 3 月 22日&nbsp;  /  &nbsp;バージョン。1.5.2 &nbsp;  /  &nbsp;修正プログラムのリリース

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 1.5.1 で発見されたいくつかの問題を修正しました。 | 参照してください[GitHub の修正プログラムのリリースでは、年 3 月](https://github.com/Microsoft/azuredatastudio/milestone/28)します。<br/> <br/>&bull; &nbsp; ユーザーとダッシュ ボードに「ノートブックを開く」のタスクから開かれた notebook が終了できなかった問題を修正しました <br/>&bull; &nbsp; Notebook の JSON に余分ながある問題を修正しました} 保存後 <br/>&bull; &nbsp; Notebook のグリッドがテーマの変更に応答しない、問題を修正しました <br/>&bull; &nbsp; タブ ヘッダーで notebook の完全なパスが示すように問題を修正しました。 ファイル名のみが表示されるようになりました。 |
| &nbsp; | &nbsp; |

## <a name="march-2019"></a>3 月 2019

2019 年 3 月 18日&nbsp;  /  &nbsp;バージョン。1.5.1

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 追加[Data Studio の Azure の PostgreSQL 拡張機能](postgres-extension.md) | サポートされている機能: <br/>&bull; &nbsp; 接続ダイアログ <br/>&bull; &nbsp; オブジェクト エクスプ ローラー <br/>&bull; &nbsp; クエリ エディター <br/>&bull; &nbsp; グラフ作成 <br/>&bull; &nbsp; ダッシュ ボード <br/>&bull; &nbsp; スニペット <br/>&bull; &nbsp; データを編集します。 <br/>&bull; &nbsp; Notebook |
| 追加の SQL のノートブック | Notebook の組み込みビューアーを SQL のカーネル サポートが追加されました。 <br/>&bull; &nbsp; サポートする T-SQL <br/>&bull; &nbsp; PGSQL のサポート |
| PowerShell の拡張機能を追加しました  | 経由では、 [PowerShell 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)VS コードから発生します。  |
| SQL Server dacpac の拡張機能が追加  | 新しい拡張機能に SQL Server インポート拡張機能からのデータ層アプリケーションのウィザードを削除します。  |
| 追加されたコミュニティ拡張子 QueryPlan.show | クエリ プランを視覚化する統合サポートを追加します。  |
| 更新された SQL Server 2019 Preview の拡張機能 | &bull; &nbsp; Jupyter Notebook のサポート、具体的には Python3 および Spark カーネルでは、中核となる Azure データ Studio ツールに移動します。 <br/>&bull; &nbsp; 外部のデータ ウィザードのバグ修正  |
| 解決済みバグと問題。 | 参照してください[バグと github の問題](https://github.com/Microsoft/azuredatastudio/milestone/25?closed=1)します。 |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>既知の問題
- [#4427](https://github.com/Microsoft/azuredatastudio/issues/4427):準備完了にはセルの前にカーネルで実行 をクリックしての致命的なエラーの結果を Spark**回避策。** 任意のセルを実行するまでのカーネルが読み込まれるまでの待機
- [#4493](https://github.com/Microsoft/azuredatastudio/issues/4493):SQL 認証 - ユーザー パスワードのプロンプトを使用して SSMS から起動された広告**回避策。** ここでは、Windows 認証を使用します。 
- [#4494](https://github.com/Microsoft/azuredatastudio/issues/4494):SQL のノートブック機能をインストールすることができません。 <br/>
**回避策:** 回避策の手順に従います[ここ](https://github.com/Microsoft/azuredatastudio/issues/4494#issuecomment-473043832)します。 
- [#4503](https://github.com/Microsoft/azuredatastudio/issues/4503):Azure Data Studio をダウンロード フォルダー (Mac) から直接開かれたにすることはできません。 <br />
**回避策:** アプリを解凍した後、コンピューターを再起動します。 調査されます。 
- [#4539](https://github.com/Microsoft/azuredatastudio/issues/4539):Notebook 名を付けて接続コンテキストを失った <br />
**回避策:** 次のリリースで修正される予定です。 
- [#4458](https://github.com/Microsoft/azuredatastudio/issues/4458):無効なバージョンを使用する場合、Dacpac の抽出が SqlToolsService をクラッシュします。 <br/>
**回避策:** Azure Data Studio を再起動し、正しいバージョンを使用することを確認します。
- 新しい Notebook とノートブックを開くアイコンは失われます <br/> 
**回避策:** 従来の接続の種類が非推奨とされます。 SQL Server エンドポイントに接続することをお勧めします。 および、期待どおりに、すべてのアクション (新しい Notebook、Spark ジョブ) が表示されます。 

## <a name="february-2019"></a>2019 年 2 月

2019 年 2 月 13日&nbsp;  /  &nbsp;バージョン。1.4.5

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 追加**SQL Server 用管理パック**拡張パックします。 | これにより、SQL Server の管理に関連する拡張機能のインストールを容易にします。 この機能には、次が含まれます。<br/>&bull; &nbsp; [SQL Server エージェント](sql-server-agent-extension.md?view=sql-server-2017)<br/>&bull; &nbsp; [SQL Server Profiler](https://docs.microsoft.com/sql/azure-data-studio/sql-server-profiler-extension)<br/>&bull; &nbsp; [SQL Server のインポート](sql-server-import-extension.md?view=sql-server-2017) |
| Profiler の拡張機能でのイベントのサポートを拡張する追加のフィルター処理します。 | &nbsp; |
| Added は、XML として T-SQL の結果を保存することができる機能を XML として保存します。 | &nbsp; |
| 追加のデータ層アプリケーションのウィザードの機能強化。 | &bull; &nbsp; 生成スクリプトの追加 ボタン<br/>&bull; &nbsp; デプロイ時にデータ損失の可能性の警告を提供する追加のビュー。 |
| SQL Server 2019 プレビュー拡張機能を更新します。 | 参照してください[拡張機能の SQL Server 2019 Preview](sql-server-2019-extension.md?view=sql-server-ver15)します。 |
| 結果の時間の長い既定で有効になっているストリーミング クエリを実行します。 | &nbsp; |
| 解決済みバグと問題。 | 参照してください[バグと github の問題](https://github.com/Microsoft/azuredatastudio/milestone/23?closed=1)します。 |
| &nbsp; | &nbsp; |

## <a name="january-2019-hotfix"></a>2019 年 1 月 (修正プログラム)

2019 年 1 月 16日&nbsp;  /  &nbsp;バージョン。1.3.9 &nbsp;  /  &nbsp;修正プログラムのリリース

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 1.3.8 で発見されたいくつかの問題を修正しました。 | 参照してください[GitHub での 1 月の修正プログラム リリース](https://github.com/Microsoft/azuredatastudio/milestone/24?closed=1)します。<br/><br/>詳細についてを参照してください。<br/>&bull; &nbsp; [変更ログは、GitHub の](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)します。<br/>&bull; &nbsp; [GitHub でのリリース](https://github.com/Microsoft/azuredatastudio/releases)します。 |
| &nbsp; | &nbsp; |

## <a name="january-2019"></a>2019 年 1 月

2019 年 1 月 9日&nbsp;  /  &nbsp;バージョン。1.3.8

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| Windows のユーザーの新しいインストーラーを追加します。 | 既存のシステムのインストーラーとは異なり、新しいユーザーのインストーラーに管理者特権は必要ありません。 これは、管理者以外の場合より簡単なアップグレード エクスペリエンスもできます。 |
| Azure Active Directory 認証のサポートが追加されました。 | &nbsp; |
| Idera SQL DM パフォーマンス Insights (プレビュー) をお知らせします。 | &nbsp; |
| SQL Server インポート拡張機能のサポートにデータ層アプリケーションのウィザード。 | &nbsp; |
| SQL Server 2019 プレビュー拡張機能を更新します。 | 参照してください[拡張機能の SQL Server 2019 Preview](sql-server-2019-extension.md?view=sql-server-ver15)します。 |
| SQL Server Profiler の機能強化。 | &nbsp; |
| 大規模なクエリ (プレビュー) のストリームの結果。 | &nbsp; |
| コミュニティの拡張機能: sp_executesql to sql と新しいデータベース。 | &nbsp; |
| 解決済みバグと問題。 | 参照してください[バグと github の問題](https://github.com/Microsoft/azuredatastudio/milestone/19?closed=1)します。 |
| &nbsp; | &nbsp; |

## <a name="november-2018"></a>2018 年 11 月

2018 年 11 月 6日&nbsp;  /  &nbsp;バージョン。1.2.4

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| SQL Server 2019 プレビュー拡張機能を更新します。 | 参照してください[拡張機能の SQL Server 2019 Preview](sql-server-2019-extension.md?view=sql-server-ver15)します。 |
| 貼り付けプランの拡張機能を導入します。 | &nbsp; |
| SSMS のエディター テーマを含め、High Color クエリ拡張機能を導入します。 | &nbsp; |
| SQL Server エージェント、Profiler、およびインポートの拡張機能を修正します。 | &nbsp; |
| .Net Core を修正するソケット KeepAlive 問題の原因と macOS で非アクティブな接続を削除します。 | &nbsp; |
| .Net Core へのアップグレードの SQL ツール サービスは 2.2 Preview 3 (の最終的な AAD 対応) です。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-november-2018"></a>バグの修正、2018 年 11 月

- 修正[発行 #2933](https://github.com/Microsoft/azuredatastudio/issues/2933):接続が Azure SQL DB に失われました
- 修正[発行 #2914](https://github.com/Microsoft/azuredatastudio/issues/2914):「無効な引数」例外拡大 OE データベース ノード
- 修正[発行 #2935](https://github.com/Microsoft/azuredatastudio/pull/2935):クエリの結果に複数行のメッセージを正しく表示します。
- 修正[発行 #2906](https://github.com/Microsoft/azuredatastudio/pull/2906):テーブル名に特殊文字が含まれている場合は、データの編集ドキュメント名を修正します。
- 修正[発行 #2929](https://github.com/Microsoft/azuredatastudio/issues/2929):ビルド拡張機能で、変更ログが VSCode のリリース ノートの変更を確認するという
- 修正[発行 #2719](https://github.com/Microsoft/azuredatastudio/issues/2719):ハイ コントラスト テーマ double/3 要素のアイコン
- 修正[発行 #3047](https://github.com/Microsoft/azuredatastudio/pull/3047):SQL Server に接続するためのコマンド ライン インターフェイスの追加します。
- 修正[発行 #3031](https://github.com/Microsoft/azuredatastudio/pull/3031):クエリ プランのテーマのサポートを追加します。

## <a name="october-2018"></a>2018 の年 10 月

2018 年 10 月 29 日、 &nbsp;  /  &nbsp;バージョン。1.1.4

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| Azure SQL データベースを参照する Azure リソース エクスプ ローラーを導入します。 | &nbsp; |
| オブジェクト エクスプ ローラーおよびクエリ エディターの接続の堅牢性を向上します。 | &nbsp; |
| SQL エージェント拡張機能の向上。 | &nbsp; |
| SQL Server 2019 プレビュー拡張機能を更新します。 | 参照してください[拡張機能の SQL Server 2019 Preview](sql-server-2019-extension.md?view=sql-server-ver15)します。 |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-october-2018"></a>バグの修正、2018 の年 10 月

- 修正[発行 #2717](https://github.com/Microsoft/azuredatastudio/issues/2717):XML 列の結果は、書式設定 をクリックします。
- 修正[発行 #2993](https://github.com/Microsoft/azuredatastudio/issues/2993):結果ウィンドウの幅が完了していません
- 修正[発行 #2999](https://github.com/Microsoft/azuredatastudio/issues/2999):DB に接続するときに、Mac 上のファイル System.Diagnostics.Tracing を読み込めませんでした。
- 修正[発行 #2851](https://github.com/Microsoft/azuredatastudio/issues/2851):時系列のグラフが正しくレンダリングされません。
- 修正[発行 #2996](https://github.com/Microsoft/azuredatastudio/issues/2996):セッションが突然変更による損失を一時テーブル

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/azuredatastudio/releases)します。

## <a name="september-2018-ga-release"></a>9 月 2018 (一般公開リリース)

2018 年 9 月 24 日&nbsp;  /  &nbsp;バージョン。1.0 &nbsp;  /  &nbsp; GA リリース

Azure Data Studio (SQL Operations Studio 以前) の一般的な可用性リリースします。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| クエリ結果グリッド パフォーマンスおよび結果セットの数が多いため、UX の機能強化。 | &nbsp; |
| Visual Studio Code のソース コードは、1.23 から 1.26.1 とグリッド レイアウトと向上の設定エディター (プレビュー) を更新します。 | &nbsp; |
| スクリーン リーダー、キーボード ナビゲーションとハイ コントラストのアクセシビリティ機能改善します。 | &nbsp; |
| 追加`Connection name`サーバーのビューとで代替表示名を指定するオプション。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="announcing-the-sql-server-2019-preview-extension"></a>SQL Server 2019 プレビュー拡張機能の発表

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 含む SQL Server 2019 プレビュー機能のサポートを[ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)をサポートします。 | SQL Server 2019 プレビューに付属する HDFS/Spark ゲートウェイに接続します。<br/><br/>HDFS の参照、ファイルのアップロード、ファイルを保存し、CSV ファイルのノートブックで分析などの役に立つアクションを起動します。<br/><br/>ダッシュ ボードからの Spark ジョブを送信またはオブジェクト エクスプ ローラーでの HDFS/Spark 接続を右クリックします。 |
| Azure Data Studio ノートブック。 | 作成または、統合された Notebook のビューアーを使用して Notebook を開きます。 このリリースのノートブックでは、ビューアーは、ローカル カーネルと、SQL Server 2019 のビッグ データ クラスターに対してのみへの接続をサポートします。<br/><br/>ノートブックで PROSE コード アクセラレータ ライブラリを使用して、高速なデータ準備のためのファイル形式とデータ型を参照してください。 |
| Azure リソース エクスプ ローラー。 | Azure リソース エクスプ ローラー ビューでは、Azure アカウントのデータに関連するエンドポイントを参照し、オブジェクト エクスプ ローラーでそれらへの接続を作成できます。 このリリースでは、Azure SQL データベースとサーバーをサポートします。 |
| SQL Server PolyBase では、ウィザードの外部テーブルを作成します。 | 使いやすいウィザードでは、外部テーブルとその関連のメタデータ構造体を作成します。 このリリースでは、リモートの SQL Server、Oracle サーバーがサポートされます。 |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-september-2018"></a>バグの修正、年 2018年 9 月

- 修正[発行 #2647](https://github.com/Microsoft/azuredatastudio/issues/143):グラフでは、大きな一歩を下位かかりました。
- 修正[発行 #2648](https://github.com/Microsoft/azuredatastudio/issues/143):JSON ハイパーリンク列全体を返すことを選択します。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)、および[リリース](https://github.com/Microsoft/azuredatastudio/releases)します。

## <a name="august-2018"></a>2018 の年 8 月

2018 年 8 月 30 日&nbsp;  /  &nbsp;バージョン。0.32.8 &nbsp;  /  &nbsp;パブリック プレビュー

*年 8 月のパブリック プレビュー*バグの修正、製品の安定化、および既存のシナリオのギャップを入力します。

_0.32.8 には 0.32.7 で見つかったいくつかの回帰の修正プログラムが含まれています ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971)、 [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372))_

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| SQL Server のインポート拡張をお知らせします。 | &nbsp; |
| SQL Server Profiler のセッションの管理。 | &nbsp; |
| SQL Server Profiler セッション テンプレートのサポート。 | &nbsp; |
| SQL Server エージェントの機能強化。 | &nbsp; |
| コミュニティの新しい拡張機能:最初の応答側キットです。 | &nbsp; |
| 生活の質の改良:接続文字列 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-august-2018"></a>バグの修正、年 2018年 8 月

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

### <a name="known-issues-august-2018"></a>既知の問題、年 2018年 8 月

- [発行 #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) Excel のデータの先頭行のみを保存して保存.
- [発行 #2150](https://github.com/Microsoft/azuredatastudio/issues/2150):コンテナー内の SQL を Ubuntu 16.04 に接続できません。

## <a name="july-2018"></a>2018 年 7 月

2018 年 7 月 19 日&nbsp;  /  &nbsp;バージョン。0.31.4 &nbsp;  /  &nbsp;パブリック プレビュー

*年 7 月のパブリック プレビュー*次の項目に重点を置いています。

- SQL Server エージェントの構成シナリオの最初のリリース。
- SQL Server Profiler のセッションとビュー テンプレートの強化。
- 顧客の継続的なバグの修正は、GitHub の問題を報告します。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| [SQL Operations Studio の拡張機能の SQL Server エージェント](sql-server-agent-extension.md)の機能強化。 | 左側のウィンドウでアラート、演算子、およびプロキシおよびアイコンの追加のビュー。<br/><br/>新しいジョブを新しいジョブ ステップ、新しいアラート、および新しい演算子をダイアログ ボックスを追加します。<br/><br/>追加されたジョブの削除、通知の削除、および Delete 演算子 (右クリック)。<br/><br/>追加した以前の実行の視覚化。<br/><br/>それぞれの列名の追加のフィルター。 |
| [SQL Operations Studio の拡張機能の SQL Server Profiler](sql-server-profiler-extension.md)の機能強化。 | 拡張イベントを表示する 5 つの既定のテンプレートを追加します。<br/><br/>追加されたサーバー/データベースの接続名です。<br/><br/>Azure SQL Database インスタンスのサポートが追加されました。<br/><br/>Profiler がまだ実行されているときにタブが閉じられたときに、Profiler を終了する候補を追加します。 |
| 結合スクリプト拡張機能のリリースです。 | &nbsp; |
| 拡張機能の作成者の追加ウィザードとダイアログの機能拡張ポイント。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-july-2018"></a>バグの修正、2018 年 7 月

- 修正[発行 728](https://github.com/Microsoft/azuredatastudio/issues/728):MacOS で追加の接続に応答がありません。
- 修正[1612 を発行](https://github.com/Microsoft/azuredatastudio/issues/1612):結果グリッド テキストの表示は国際文字、にくかった
- 修正[発行 1693](https://github.com/Microsoft/azuredatastudio/issues/1693):バックアップ ダイアログ ボックス:ファイル ブラウザー UI が壊れています
- 修正[発行 1713](https://github.com/Microsoft/azuredatastudio/issues/1713):影響を受ける行の数
- 修正[発行 1718](https://github.com/Microsoft/azuredatastudio/issues/1718):任意のデータ ソースに接続できません。
- 修正[発行 1719](https://github.com/Microsoft/azuredatastudio/issues/1719):サーバーに接続するときに、TypeError
- 修正[発行 1724](https://github.com/Microsoft/azuredatastudio/issues/1724):ダイアログの拡張機能が動作を停止しました
- 修正[発行 1749](https://github.com/Microsoft/azuredatastudio/issues/1749):バグ:列内の HTML データが解釈されます。
- 修正[発行 1789](https://github.com/Microsoft/azuredatastudio/issues/1789):機能拡張: 接続プロバイダーを追加する場合アンインストールは決して一覧から削除、
- 修正[発行 1791](https://github.com/Microsoft/azuredatastudio/issues/1791):Sqlops Extensions: queryeditor.connect() connects to the target database, but UI does not show the editor is connected
- 修正[発行 1799](https://github.com/Microsoft/azuredatastudio/issues/1799):上位 10 個の DB サイズのグラフは、大文字小文字を区別するインスタンスでは動作しません
- 修正[発行 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): sqlops.d.ts 入力ミスが原因で暗黙的な 'any' 型の定義
- 修正[発行 1817](https://github.com/Microsoft/azuredatastudio/issues/1817):エラー de Ortografia
- 修正[発行 1830](https://github.com/Microsoft/azuredatastudio/issues/1830):Component() が呼び出された後、ButtonComponent で iconPath を設定してもアイコンは変更されません。
- 修正[発行 1843](https://github.com/Microsoft/azuredatastudio/issues/1843):効率的なテーブルの整理

## <a name="june-2018"></a>2018 年 6 月

2018 年 6 月 20 日&nbsp;  /  &nbsp;バージョン。0.30.6 &nbsp;  /  &nbsp;パブリック プレビュー

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| **SQL Operations Studio の SQL Server Profiler_プレビュー_** 拡張機能の初期リリースします。 | &nbsp; |
| 新しい**SQL Data Warehouse**拡張機能には、data warehouse への洞察を提示充実したカスタマイズ可能なダッシュ ボードのウィジェットが含まれています。 | これには、管理と一貫したパフォーマンスの最適化されて ことを確認するデータ ウェアハウスのチューニングに関する主なシナリオがロック解除します。 |
| **データの「フィルター処理と並べ替え」を編集**をサポートします。 | &nbsp; |
| **SQL Operations Studio の SQL Server エージェント_プレビュー_** ジョブおよびジョブ履歴の拡張機能のビュー。 | &nbsp; |
| 改善**ウィザードとダイアログの UI ビルダー Framework**拡張 Api。 | &nbsp; |
| VS プラットフォーム コードのソース コードを更新します。 | 次のリリースを統合するには。<br/>&bull; &nbsp; [2018 年 3 月 (1.22)](https://code.visualstudio.com/updates/v1_22)<br/>&bull; &nbsp; [2018 年 4 月 (1.23)](https://code.visualstudio.com/updates/v1_23) |
| &nbsp; | &nbsp; |

### <a name="github-issues-fixes-june-2018"></a>GitHub の問題を修正、2018 年 6 月

- 機能の要求 ([発行 1204](https://github.com/Microsoft/azuredatastudio/issues/1204))。結果グリッドの自動調整の列の幅、データをしてください、同じクエリを再実行している場合は、手動で変更を注意してください。
- 修正[発行 1398](https://github.com/Microsoft/azuredatastudio/issues/1398):必要がありますショーはメッセージを追加し、リンクされているアカウントが空の場合は、アカウントのアカウント ボタンを追加します。
- 修正[発行 1399](https://github.com/Microsoft/azuredatastudio/issues/1399):ビューが折りたたまれているときに、リンクされたアカウント タブは解除されます。
- 修正[発行 1374](https://github.com/Microsoft/azuredatastudio/issues/1374):ディスクから、.sql ファイルを開くときに、SQL ツール サービスがクラッシュします。
- 修正[発行 1372](https://github.com/Microsoft/azuredatastudio/issues/1372):SQL キーワード"BETWEEN"がありません。
- 修正[発行 1395](https://github.com/Microsoft/azuredatastudio/issues/1395):一致' キーワードは、SQL ツール サービスがクラッシュします。
- 修正[発行 1496](https://github.com/Microsoft/azuredatastudio/issues/1496):"新しい Profiler"コンテキスト メニュー オプションは、オブジェクト エクスプ ローラーでは、何も行われません。
- 修正[発行 1495](https://github.com/Microsoft/azuredatastudio/issues/1495):クエリ エディターの「説明」クエリ プランが壊れています。

## <a name="may-2018"></a>2018 年 5 月

2018 年 5 月 7日&nbsp;  /  &nbsp;バージョン。0.29.3 &nbsp;  /  &nbsp;パブリック プレビュー

*パブリック プレビューの可能性があります*安定化とバグの修正に重点を置いています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| Redgate SQL Search 拡張機能の使用可能な拡張機能マネージャーにお知らせします。 | &nbsp; |
| コミュニティ ローカライズの 10 言語で使用できます。 | ドイツ語、スペイン語、フランス語、イタリア語、日本語、韓国語、ポルトガル語、ロシア語、簡体字中国語、および繁体字中国語します。 |
| 製品利用統計情報コレクションが変更されます。 | &bull; &nbsp; 削減製品利用統計情報のコレクション。<br/>&bull; &nbsp; オプトアウト エクスペリエンスの向上。<br/>&bull; &nbsp; プライバシーに関する声明を製品内のリンク。 |
| 拡張機能マネージャーでは、強化された Marketplace のエクスペリエンスがあります。 | コミュニティの拡張機能をより簡単に検出します。 |
| SQL エージェントの拡張機能。 | &bull; &nbsp; ジョブです。<br/>&bull; &nbsp; ジョブ履歴の表示の機能強化。 |
| Whoisactive とサーバー レポートの拡張機能を更新します。 | &nbsp; |
| 管理ダッシュ ボードのプロパティのスクロールが向上します。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues"></a>GitHub の問題を修正します。

- 修正[703 の発行](https://github.com/Microsoft/azuredatastudio/issues/703):値が正しく更新されるまで表示されないデータ編集で HTML のようなテキストを入力すると、します。
- 修正[発行 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb パッケージの依存関係
- 修正[発行 1260](https://github.com/Microsoft/azuredatastudio/issues/1260):キーワード 'distinct' は強調表示されていません。
- 修正[発行 1332](https://github.com/Microsoft/azuredatastudio/issues/1332):データの編集を元に戻す行は機能しません
- 修正[発行 1215](https://github.com/Microsoft/azuredatastudio/issues/1215):SQL エージェントの拡張機能とステータス バー
- 修正[発行 1316](https://github.com/Microsoft/azuredatastudio/issues/1316):Windows のサイズを変更した後、SQL エージェントの今後のサイズ変更

## <a name="april-2018"></a>2018 年 4 月

2018 年 4 月 25 日&nbsp;  /  &nbsp;バージョン。0.28.6 &nbsp;  /  &nbsp;パブリック プレビュー

*年 4 月のパブリック プレビュー*バグ修正と改善が含まれています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| SQL エージェント プレビュー拡張機能の機能強化: | &nbsp; |
| &nbsp; &nbsp; &nbsp; ファイルのサポートの強化。 | &bull; &nbsp; 大きなファイル。<br/>&bull; &nbsp; 保護されている管理者を保存するためのファイルを保護します。<br/>&bull; &nbsp; 格納する\>SQL Operations Studio 内で 256 個のファイル。 |
| &nbsp; &nbsp; &nbsp; 統合ターミナルを分割します。 | 複数のオープン端末を同時に操作します。 |
| &nbsp; &nbsp; &nbsp; 高速インストールとスタートアップ時間。 | ディスク上のファイル数のフット プリントの削減のインストール。 |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues-april-2018"></a>2018 年 4 月、GitHub の問題を修正します。

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

### <a name="visual-studio-code-121-platform"></a>Visual Studio コード 1.21 プラットフォーム

4 月のパブリック プレビューのハイライトは、Visual Studio コード 1.21 プラットフォームのソース コードの更新です。 前の 1.19 同期ポイントからのコア エディターおよび workbench にいくつかの更新プログラムが表示されます。 いくつかの例を以下に示します。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| [新しい通知 UI](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui)します。 | 簡単に管理し、SQL Operations Studio の通知を確認します。 |
| [統合ターミナル分割](https://code.visualstudio.com/updates/v1_21#_split-terminals)します。 | 同時に開いている複数の端末で作業します。 |
| [大規模で保護されたファイルを保存](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges)します。 | 保護されている管理者を保存し、 \>SQL Operations Studio 内で 256 個のファイル。 |
| [大きなファイルのサポートを強化](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements)します。 | 大きなファイルのテキスト バッファーの最適化。 |
| [設定の検索機能の向上](https://code.visualstudio.com/updates/v1_20#_settings-search)します。 | 自然言語検索の適切な設定を簡単に検索します。 |
| [グローバル スニペット](https://code.visualstudio.com/updates/v1_20#_global-snippets)します。 | すべてのファイルの種類で使用することができますのスニペットを作成します。 |
| [エクスプ ローラーの複数選択](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer)します。 | 一度に複数のファイルに対してアクションを実行します。 |
| [エラーと警告エクスプ ローラーで](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer)します。 | コード ベースでのエラーをすばやく移動します。 |
| [ドラッグ & ドロップ、コピー & windows 全体に貼り付け](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support)します。 | SQL Operations Studio の開いているウィンドウ間でファイルを移動します。 |
| [Git のサブモジュール サポート](https://code.visualstudio.com/updates/v1_20#_git-submodules)します。 | 入れ子になったの Git リポジトリに対して Git 操作を実行します。 |
| [ターミナル スクリーン リーダーのサポート](https://code.visualstudio.com/updates/v1_20#_screen-reader-support)します。 | 統合ターミナルになりました**スクリーン リーダーに最適化された**モード。 |
| [エディターの中央揃えのレイアウト](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout)します。 | 実際の画面を表示するコードを最大化します。 |
| [水平方向の検索結果 (プレビュー)](https://code.visualstudio.com/updates/v1_21#_horizontal-search)します。 | できるビューの検索結果の水平方向のパネルのようになりました。 |
| &nbsp; | &nbsp; |

詳細については、チェック アウト、 [Visual Studio Code 年 2 月のリリース ノート](https://code.visualstudio.com/updates/v1_21)、および[Visual Studio Code 年 1 月のリリース ノート](https://code.visualstudio.com/updates/v1_20)します。

詳細については、次を参照してください。、[変更ログ](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md)します。

## <a name="march-2018"></a>2018 年 3 月

2018 年 3 月 28 日&nbsp;  /  &nbsp;バージョン。0.27.3 &nbsp;  /  &nbsp;パブリック プレビュー

*年 3 月のパブリック プレビュー*引き続き最上位の GitHub の問題に対処して機能拡張アジャイル チームのストーリーの向上に重点を置いています。 具体的には、ダッシュ ボードの管理を向上し、SQL エージェント、insights 拡張機能を提供する、拡張機能マネージャーを有効にします。 このリリースには、次の機能強化が含まれています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| タブ付き insights と構成ウィンドウをサポートするためにダッシュ ボードの機能拡張モデルを強化します。 | 拡張機能マネージャーでは、拡張機能の簡単な取得できるようにします。<br/><br/>Sp のダッシュ ボードの拡張機能\_から whoisactive [whoisactive.com](http://www.whoisactive.com)します。<br/><br/>詳細については、「 [SQL Operations Studio の機能拡張](extensions.md)です。 |
| さらに追加[接続およびオブジェクト エクスプ ローラーの機能拡張 Api](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API)管理します。 | &nbsp; |
| 影響を与える重要な顧客の修正を続行[GitHub の懸案事項](https://github.com/Microsoft/azuredatastudio/issues)します。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="february-2018"></a>2018 年 2 月

2018 年 2 月 15 日&nbsp;  /  &nbsp;バージョン。0.26.7 &nbsp;  /  &nbsp;パブリック プレビュー

*年 2 月のパブリック プレビュー*いくつかの機能の候補と優先度の高いバグの修正が含まれています。 このリリースには、次の機能強化が含まれています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 新しいリリースがダウンロード可能なときに通知を提供する自動更新のインストールの概要。 | &nbsp; |
| 接続ダイアログ**データベース**フィールドは、指定されたサーバーから設定されたデータベースの一覧を含むドロップダウン リストを動的に設定されています。 | &nbsp; |
| 接続の機能拡張 API を紹介します。 | &nbsp; |
| VS コード エディター 1.19 の統合。 | &nbsp; |
| いくつかのクエリ プラン ビューアーの機能強化を回収する JustinPealing html-クエリのプランのコンポーネントに更新します。 | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixed-issues-february-2018"></a>2018 年 2 月の修正された問題

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

## <a name="january-2018"></a>2018 年 1 月

2018 年 1 月 17日&nbsp;  /  &nbsp;バージョン。0.25.4 &nbsp;  /  &nbsp;パブリック プレビュー

*年 1 月のパブリック プレビュー*いくつかの機能の候補と優先度の高いバグの修正が含まれています。 このリリースには、次の機能強化が含まれています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 保存されたサーバーの接続、接続ダイアログで利用できます。 | &nbsp; |
| ホットな終了を有効にします。 ホットな終了は参照を有効にする、既定で無効[ホット終了設定](settings.md#hot-exit)します。 | &nbsp; |
| サーバー グループに基づくをタブの色指定します。 既定では、「」を参照を有効にする タブの色分けはオフです[色設定をタブ](settings.md#tab-color)します。 | &nbsp; |
| 変更*サーバー名*に*Server*接続 ダイアログ ボックス。 | &nbsp; |
| 修正プログラムの分類*現在のクエリの実行*コマンド。 | &nbsp; |
| ドラッグ アンド ドロップの重大なバグのスクリプトを修正します。 | &nbsp; |
| [スタート] メニューのアイコンをピン留めする修正プログラムが正しくありません。 | &nbsp; |
| 不足している Azure アカウントがアイコンのブランドを修正します。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="december-2017"></a>2017 年 12 月

2017 年 12 月 19 日&nbsp;  /  &nbsp;バージョン。0.24.1 &nbsp;  /  &nbsp;パブリック プレビュー

*年 12 月のパブリック プレビュー*以下の機能強化もすべての機能領域の全体でいくつかのバグ修正が含まれています。

&nbsp;

| [変更] | 詳細 |
| :----- | :------ |
| 作成するファイアウォール ルール ダイアログは、Azure SQL Database と Azure SQL Data Warehouse への接続を支援するために使用できるようになりました。 | &nbsp; |
| 追加の Windows セットアップでは、および Linux DEB と RPM のインストール パッケージです。 | &nbsp; |
| ダッシュ ボードの視覚的なレイアウト エディターを管理します。 | &nbsp; |
| *スクリプトとして変更*と*スクリプトとして実行*コマンド。 | &nbsp; |
| *実際のプランで現在のクエリを実行*コマンド。 | &nbsp; |
| VS Code 1.18.1 エディター プラットフォームを統合します。 | &nbsp; |
| ファイルの VSIX 拡張機能のサイドローディングを有効にします。 | &nbsp; |
| "移動 N"バッチのイテレーションの構文をサポートします。 | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="november-2017"></a>2017 年 11 月

2017 年 11 月 15 日&nbsp;  /  &nbsp;バージョン。0.23.6

- 初回のリリースの[!INCLUDE[name-sos](../includes/name-sos-short.md)]します。

## <a name="next-steps"></a>次の手順

開始する次のクイック スタートのいずれかを参照してください。

- [接続および SQL Server のクエリ](quickstart-sql-server.md)
- [接続および Azure SQL Database のクエリ](quickstart-sql-database.md)
- [接続し、Azure Data Warehouse に対するクエリ](quickstart-sql-dw.md)

投稿する[!INCLUDE[name-sos](../includes/name-sos-short.md)]:

- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
