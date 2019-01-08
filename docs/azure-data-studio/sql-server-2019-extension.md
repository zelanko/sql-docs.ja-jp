---
title: SQL Server 2019 拡張機能 (プレビュー)
titleSuffix: Azure Data Studio
description: Azure Data Studio 用 SQL Server 2019 Preview の拡張機能
ms.custom: seodec18
ms.date: 11/06/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6ce44d22675be344aaa1f08632e39bfdf9c190b3
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432815"
---
# <a name="sql-server-2019-extension-preview"></a>SQL Server 2019 拡張機能 (プレビュー)

SQL Server 2019 拡張機能 (プレビュー) の新機能とツールのサポートに配布のプレビュー サポートを提供します[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]します。 プレビュー サポートが含まれます[SQL Server 2019 ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)、統合[ノートブック エクスペリエンス](../big-data-cluster/notebooks-guidance.md)、PolyBase [Create External Table ウィザード](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json)、および[Azure リソース エクスプ ローラー](azure-resource-explorer.md)します。

## <a name="install-the-sql-server-2019-extension-preview"></a>SQL Server 2019 拡張機能 (プレビュー) のインストールします。

SQL Server 2019 拡張機能 (プレビュー) をインストールするには、ダウンロードして、関連付けられている .vsix ファイルをインストールします。

1. SQL Server 2019 拡張機能 (プレビュー) の .vsix ファイルをローカル ディレクトリにダウンロードするには。

   |プラットフォーム|ダウンロード|リリース日|バージョン
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?linkid=2038184)|2018 年 11 月 6 日 |0.8.0 以降
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?linkid=2038178)|2018 年 11 月 6 日 |0.8.0 以降
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?linkid=2038246)|2018 年 11 月 6 日 |0.8.0 以降

1. Azure Data Studio で次のように選択します。 **VSIX パッケージからの拡張機能のインストール**から、**ファイル**メニューとダウンロードした .vsix ファイルを選択します。

1. 選択**はい**インストールを確認し、インストールが成功したことを示す通知を待機するように求められたらします。

1. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。

1. 再読み込みした後、拡張機能の依存関係がインストールされます。 [出力] ウィンドウで進行状況を表示して、まで時間がかかる可能性があります。

1. インストールが完了したら、依存関係、Azure Data Studio を閉じて。 **SQL Server のビッグ データ クラスター**接続の種類は、Azure Data Studio を再起動するまでは使用できません。

## <a name="release-notes-v080"></a>リリース ノート (v0.8.0)
*Notebook*:
* セルを追加する前に、/後の既存のセルを「その他のアクション」セルのボタンをクリックしてなりました
* **新しい接続の追加**"Attach To"のドロップダウン リストに接続するオプションが追加されました
* A **Notebook の依存関係を再インストール**Python パッケージの更新を支援し、アプリケーションを終了してインストールを途中まで停止した場所の場合の解決にコマンドが追加されました。 これは、コマンド パレットから実行することができます (を使用して、`Ctrl/Cmd+Shift+P`と種類`Reinstall Notebook Dependencies`)
* PROSE の python パッケージは、1.1.0 が更新され、多くバグ修正にはが含まれています。 使用して、 **Notebook の依存関係を再インストール**このパッケージを更新するコマンド
* A**出力データをクリア**をクリックしてコマンドがサポートされているようになりました、**その他のアクション**セルのボタン
* 次の修正に関して報告された問題。
  * パスの問題のための Windows セッションの notebook を開始できません。
  * C:\ または D:\ など、ドライブのルート フォルダーから、notebook を開始できませんでした。
  * [#2820](https://github.com/Microsoft/azuredatastudio/issues/2820) VS Code での広告から作成されたノートブックを編集できません。
  * Spark UI リンクは Spark カーネルを実行するときに今すぐ動作します。
  * 「パッケージ管理」の名前を変更「パッケージのインストール」する

*外部データを作成する*:

* エラー メッセージはコピー可能およびの概要や詳細ビューに簡単に分割されています
* UI レイアウトの向上と大幅に向上した信頼性とエラー処理
* 次の修正に関して報告された問題。
  * 無効になっている、無効な列マッピングを持つテーブルが表示され、警告、エラーを説明します。

## <a name="release-notes-v072"></a>リリース ノート (v0.7.2)
* Azure リソース エクスプ ローラーでは、Azure Data Studio に組み込まれましたと、この拡張機能から削除されました。 これに関するフィードバックをありがとうございます。
* Markdown の数のセルと notebook のパフォーマンスを改善しました。
* ノートブックにコードの自動サイズ セルです。 セルのツールバーに基づく最小サイズはこのまだあります。
* Notebook の依存関係をインストールするときにユーザーに通知します。 Windows で具体的にはこのことができます、長い時間がかかる、タスク ビューの通知が表示されるようになりましたので。
* Notebook の依存関係を再インストールをサポートします。 これは、ユーザー以前閉じた Azure Data Studio 途中のインストールを使用する場合に便利です。
* ノートブックのセルの実行の取り消しをサポートします。
* 信頼性の向上と、外部データの作成ウィザードを使用して、具体的には接続エラーが発生した場合。
* PolyBase が有効になっているか、ターゲット サーバーで実行されている場合は、外部データの作成ウィザードの使用をブロックします。
* スペル チェックし、SQL Server 2019 と外部データの作成に関連する修正プログラムの名前を付けします。
* エラーの数が多い、Azure Data Studio デバッグ コンソールから削除されます。

##  <a name="sql-server-2019-big-data-cluster-support"></a>SQL Server 2019 ビッグ データ クラスター サポート

* クリックして**接続の追加**で*オブジェクト エクスプ ローラー*選択**ビッグ データの SQL Server クラスター**接続の種類として。

   > [!TIP]
   > 表示されない場合、 **SQL Server のビッグ データ クラスター**接続の種類、Azure データ Studio を再起動します。

* ホスト名または IP アドレスのクラスター エンドポイントとのユーザー名と接続に使用するパスワードを入力します。
* 必要に応じてでわかりやすい表示名を含める、**名前**フィールド。
* をクリックして**Connect**一般的なタスクを起動することができますし、ダッシュ ボードで、[参照] **HDFS**オブジェクト エクスプ ローラーで、そこからタスクの実行コンテキスト内で。
* サーバー ノードを右クリックし、クラスターに対して Spark ジョブを送信する*オブジェクト エクスプ ローラー*選択**Submit Spark Job**送信ダイアログ ボックスを表示します。
* Notebook を開くには、次のセクションを参照してください。

詳細については、次を参照してください。[ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)します。


## <a name="azure-data-studio-notebooks"></a>Azure Data Studio Notebook

* 次の方法のいずれかで、notebook を開きます。
  * 新しいノートブックを開く、*コマンド パレット*します。
  * いずれかの SQL Server 2019 のビッグ データ クラスターの HDFS のオブジェクト エクスプ ローラー ツリーを開きます。
    * サーバー ノードを右クリックし、選択**新しい Jupyter Notebook**します。
    * CSV ファイルを右クリックし、選択**ノートブックで分析**します。
  * 既存の .ipynb ファイルを開き、**ファイル**メニューまたはファイル エクスプ ローラー *(.ipynb ファイルは正常に読み込むには、4 以降のバージョンにアップグレードする必要があります)*
* カーネルを選択します。 ローカルの notebook の実行では、Python 3 を選択します。 リモート実行は、選択 PySpark または Spark |Scala します。
* リモートで実行している場合に接続する SQL Server のビッグ データ クラスター エンドポイントを選択 (これは必要ありません Python 3 のローカル開発用)。
* Notebook のヘッダーのボタンを使用してコードまたは markdown のセルを追加します。 各セルの左側にごみ箱のアイコンのセルを削除します。
* 再生ボタン コードのセルを持つセルを実行し、マークダウンの編集を切り替え、目のアイコンでプレビュー

## <a name="polybase-create-external-table-wizard"></a>PolyBase 外部テーブルのウィザードを作成します。

* SQL Server 2019 インスタンスから、*外部テーブルの作成ウィザード*3 つの方法で開くことができます。
  * サーバーを右クリックして選択**管理**の SQL Server 2019 (プレビュー)、タブをクリックし、選択、 **Create External Table**します。
  * 選択されている SQL Server 2019 インスタンスと*オブジェクト エクスプ ローラー*、起動*外部の作成ウィザード*を使用して、*コマンド パレット*します。
  * SQL Server 2019 のデータベースを右クリックして*オブジェクト エクスプ ローラー*選択**Create External Table**します。
* このバージョンの拡張機能では、リモートの SQL Server、Oracle のテーブルにアクセスする外部テーブルが作成されます。

  > [!NOTE]
  > 外部テーブルの機能には、SQL 2019 機能が、リモートの SQL Server が以前のバージョンの SQL Server を実行する可能性があります。

* ウィザードの最初のページで SQL Server または Oracle にアクセスして、続行するかどうかを選択します。
* 1 つ既に作成されていない場合は、データベースのマスター _ キーを作成するメッセージが表示されます (パスワードは複雑さが不足しているはブロックされます)。
* データ ソース接続を作成し、リモート サーバーの資格情報をという名前です。
* 新しい外部テーブルにマップするオブジェクトを選択します。
* 選択**スクリプトの生成**または**作成**ウィザードを終了します。
* 外部テーブルの作成後にすぐに表示されます、データベースのオブジェクトのツリーが作成されました。


## <a name="known-issues"></a>既知の問題

* 接続の作成時にパスワードが保存されていない場合は、Spark ジョブの送信など一部の操作が成功しません。
* 既存の notebook の .ipynb は、ビューアーの内容を読み込むには、4 以降のバージョンにアップグレードする必要があります。
* 実行している、 **Notebook の依存関係を再インストール**コマンドはその 1 つが失敗したタスク ビューで 2 つのタスクを表示することがあります。 インストールが失敗は発生しません
* 選択**新しい接続の追加**[キャンセル] をクリックすると、Notebook が**接続の選択**が既に接続されている場合でも、表示します。