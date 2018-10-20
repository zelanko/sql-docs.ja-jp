---
title: Azure のデータ Studio の SQL Server 2019 拡張機能 (プレビュー) |Microsoft Docs
description: Azure Data Studio 用 SQL Server 2019 Preview の拡張機能
ms.custom: tools|sos
ms.date: 10/11/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6624f2efb14f5d056ee0ac052fa9396535ebb239
ms.sourcegitcommit: ef115025e57ec342c14ed3151ce006f484d1fadc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2018
ms.locfileid: "49411169"
---
# <a name="sql-server-2019-extension-preview"></a>SQL Server 2019 拡張機能 (プレビュー)

SQL Server 2019 拡張機能 (プレビュー) の新機能とツールのサポートに配布のプレビュー サポートを提供します[!INCLUDE[sql-server-2019](..\includes\sssqlv15-md.md)]します。 プレビュー サポートが含まれます[SQL Server 2019 ビッグ データ クラスター](../big-data-cluster/big-data-cluster-overview.md)、統合[ノートブック エクスペリエンス](../big-data-cluster/notebooks-guidance.md)、PolyBase [Create External Table ウィザード](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json)、および[Azure リソース エクスプ ローラー](azure-resource-explorer.md)します。

## <a name="install-the-sql-server-2019-extension-preview"></a>SQL Server 2019 拡張機能 (プレビュー) のインストールします。

SQL Server 2019 拡張機能 (プレビュー) をインストールするには、ダウンロードして、関連付けられている .vsix ファイルをインストールします。

1. SQL Server 2019 拡張機能 (プレビュー) の .vsix ファイルをローカル ディレクトリにダウンロードするには。

   |プラットフォーム|ダウンロード|リリース日|バージョン
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?LinkId=2031539)|2018 年 10 月 18 日|0.7.2 です。
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?LinkId=2031717)|2018 年 10 月 18 日 |0.7.2 です。
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?LinkId=2031538)|2018 年 10 月 18 日 |0.7.2 です。

1. Azure Data Studio で次のように選択します。 **VSIX パッケージからの拡張機能のインストール**から、**ファイル**メニューとダウンロードした .vsix ファイルを選択します。

1. 選択**はい**インストールを確認し、インストールが成功したことを示す通知を待機するように求められたらします。

1. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。

1. 再読み込みした後、拡張機能の依存関係がインストールされます。 [出力] ウィンドウで進行状況を表示して、まで時間がかかる可能性があります。

## <a name="release-notes-v072"></a>リリース ノート (v0.7.2)
* Azure リソース エクスプ ローラーでは、Azure Data Studio に組み込まれましたと、この拡張機能から削除されました。 これに関するフィードバックをありがとうございます。
* Markdown の数のセルと notebook のパフォーマンスを改善しました。
* ノートブックにコードの自動サイズ セルです。 セルのツールバーに基づく最小サイズはこのまだあります。
* Notebook の依存関係をインストールするときにユーザーに通知します。 Windows で具体的にはこのことができます、長い時間がかかる、タスク ビューの通知が表示されるようになりましたので。
* Notebook の依存関係を再インストールをサポートします。 これは、ユーザー以前閉じた Azure Data Studio 途中のインストールを使用する場合に便利です。
* ノートブックのセルの実行の取り消しをサポートします。
* 信頼性の向上と、外部データの作成ウィザードを使用して、具体的には接続エラーが発生した場合。
* Polybase が有効になっているか、ターゲット サーバーで実行されている場合は、外部データの作成ウィザードの使用をブロックします。
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

## <a name="polybase-create-external-table-wizard"></a>Polybase 外部テーブルのウィザードを作成します。

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
