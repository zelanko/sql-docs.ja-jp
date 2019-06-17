---
title: Azure Data Studio でノートブックを実行します。
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスターに接続されている Azure Data Studio で Jupyter Notebook を実行する方法について説明します。
author: achatter
ms.author: jroth
manager: jroth
ms.date: 05/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e4b24b70a427e7ac3e3f058b1db332b899729034
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66802819"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>SQL Server 2019 プレビューで notebook を使用する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事の最新のリリースで Notebook エクスペリエンスを起動する方法を説明します[ **Azure Data Studio** ](../azure-data-studio/download.md)と独自のノートブックの作成を開始する方法。 また、さまざまなカーネルを使用して Notebook を作成する方法も示します。

## <a name="connect-to-sql-server"></a>SQL Server への接続

Azure Data Studio では、Microsoft SQL Server 接続の種類に接続することができます。
Azure データ Studio では、また、F1 キーを押して をクリックすることができます**新しい接続** し、SQL Server に接続します。

![接続情報](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>Notebook を起動します。

新しい notebook を起動する複数の方法はあります。

- 移動して、**ファイル メニュー**でクリックして Azure Data Studio**新しい Notebook**します。

    ![新しい notebook](media/notebooks-guidance/file-new-notebook.png)

- 右クリックして、 **SQL Server**接続と起動**新しい Notebook**します。

    ![新しい notebook](media/notebooks-guidance/server-new-notebook.png)

- コマンド パレットを開いて (**Ctrl + Shift + P**)) に入力し、**新しい Notebook**します。 という名前の新しいファイル`Notebook-1.ipynb`が開きます。

## <a name="supported-kernels-and-attach-to-context"></a>カーネルがサポートされているし、コンテキストにアタッチ

Azure Data Studio で Notebook のインストールは、SQL のカーネルをネイティブでサポートします。 となり、選択したかどうかは、SQL 開発者し、Notebook を使用するにはカーネルです。 

SQL カーネルが PostgreSQL のサーバー インスタンスに接続することもできます。 PostgreSQL 開発者あり、notebook を PostgreSQL サーバーに接続する場合は、ダウンロード、 [ **PostgreSQL 拡張機能**](../azure-data-studio/postgres-extension.md) Data Studio の Azure 拡張機能マーケットプ レースにし、起動**新しい Notebook** PostgreSQL サーバーに接続するための notebook インスタンスを開きます。

![PostgreSQL の接続](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL のカーネル

クエリ エディターのようなノートブックのコード セルは、コーディング エクスペリエンスを日常的なタスクの豊富な SQL エディター、IntelliSense、および組み込みのコード スニペットなどの組み込みの機能を簡単に最新の SQL をサポートします。 コード スニペットを使用すると、データベース、テーブル、ビュー、ストアド プロシージャなどを作成し、既存のデータベース オブジェクトを更新する適切な SQL 構文を生成できます。 開発やテストの目的でデータベースのコピーをすばやく作成し、生成し、スクリプトを実行するには、コード スニペットを使用します。

クリックして**実行**各セルを実行します。

SQL Server インスタンスに接続する SQL カーネル

![SQL のカーネル](media/notebooks-guidance/intellisense-code-cell.png)

クエリ結果

![クエリ結果](media/notebooks-guidance/sql-cell-results.png)

PostgreSQL のサーバー インスタンスに接続する SQL カーネル 

![PostgreSQL の接続](media/notebooks-guidance/pgsql-code-cell.png)

クエリ結果

![クエリ結果](media/notebooks-guidance/pgsql-cell-results.png)

Notebook が SQL カーネルに接続されている場合は、既存のテキストのセルを追加するには、をクリックして、 **+ テキスト**ツールバーにコマンド。

![Notebook のツールバー](media/notebooks-guidance/notebook-toolbar.png)

セルの変更が編集モードおよび markdown とする入力と同時にプレビューが表示されます。

![Markdown のセル](media/notebooks-guidance/notebook-markdown-cell.png)

テキスト セルの外側をクリックすると、マークダウン テキストが表示されます。

![Markdown テキスト](media/notebooks-guidance/notebook-markdown-preview.png)


### <a name="configure-python-for-notebooks"></a>Notebook の Python を構成します。

カーネルのドロップダウン リストから SQL とは別に、その他のカーネルのいずれかを選択するとこのするように求められます**構成の Python notebook**します。 Notebook の依存関係の指定した場所にインストールが、インストール場所を設定するかどうかを決定できます。 このインストールは時間がかかることができ、インストールが完了するまで、アプリケーションを閉じないことをお勧めします。 インストールが完了すると、サポートされている言語でコードを記述を開始できます。

![Python を構成します。](media/notebooks-guidance/configure-python.png)

インストールが完了すると、出力ターミナルで実行されている Jupyter バックエンド サーバーの場所と共にタスクの履歴に通知が表示されます。

![Jupyter のバックエンド](media/notebooks-guidance/jupyter-backend.png)

|カーネル|説明
|:-----|:-----
| SQL のカーネル | リレーショナル データベースを対象とする SQL コードを記述します。
|PySpark3、および PySpark カーネル| クラスターからの Spark のコンピューティングを使用して Python コードを記述します。
|Spark カーネル|クラスターからの Spark のコンピューティングを使用して Scala と R コードを記述します。
|Python カーネル|ローカル開発用の Python コードを記述します。

`Attach to` アタッチする、カーネルのコンテキストを提供します。 SQL のカーネルを使用しているかどうかはその後、 `Attach to` SQL Server インスタンスのいずれか。

Python3 カーネルを使用している場合、`Attach to`は`localhost`します。 このカーネルを使用するには、ローカルの Python 開発。

既定の SQL Server 2019 ビッグ データ クラスターに接続しているときに`Attach to`クラスターの場合は、その終了点は、クラスターの Spark のコンピューティングを使用して、Python、Scala、R のコードを送信できます。

### <a name="code-cells-and-markdown-cells"></a>コード セルと Markdown のセル

クリックして新しいコード セルを追加、 **+ コード**ツールバーにコマンド。

クリックして新しいテキスト セルを追加、 **+ テキスト**ツールバーにコマンド。

![Notebook のツールバー](media/notebooks-guidance/notebook-toolbar.png)

セルの変更が編集モードおよび markdown とする入力と同時にプレビューが表示されます。

![Markdown のセル](media/notebooks-guidance/notebook-markdown-cell.png)

テキスト セルの外側をクリックすると、マークダウン テキストが表示されます。

![Markdown テキスト](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>信頼できる、非信頼

Notebook を Azure Data Studio で開くには、既定**信頼済み**します。

開くが他のソースからノートブックを開く場合**信頼されていない**モードとしやすく**信頼済み**します。

### <a name="run-cells"></a>セルを実行します。
ノートブックのすべてのセルを実行し、をクリックする場合、**セルの実行**ツールバーのボタンをクリックします。

![Markdown テキスト](media/notebooks-guidance/run-cell.png)


### <a name="clear-results"></a>[結果をクリア]

Notebook で実行されたすべてのセルの結果をクリアするかどうかをクリックして、 **Clear Results**ツールバーのボタン。

![Markdown テキスト](media/notebooks-guidance/clear-results.png)

### <a name="save"></a>保存

Notebook は、次のいずれかを保存します。

- Ctrl キーを押しながら S キーを選択します。
- クリックして**ファイル** > **保存**
- クリックして**ファイル** > **として保存しています.**
- クリックして**ファイル** > **すべてを保存** 
- コマンド パレットで、次のように入力します。**ファイル。保存** 

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark カーネル

選択、`PySpark Kernel`と、次のコード セルの種類。

**[実行]** をクリックします。

Spark アプリケーションが開始され、次の出力を返します。

![Spark アプリケーション](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark カーネル |Scala 言語

選択、`Spark|Scala Kernel`と、次のコード セルの種類。

![Spark Scala](media/notebooks-guidance/spark-scala.png)

– 以下のオプション アイコンをクリックするとに、"セル"オプションを表示することもできます。

![セルのオプション](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark カーネル |R 言語

Spark の選択 |R カーネルでは、ドロップダウン リストにします。 セルに入力するか、コードを貼り付けます。 クリックして**実行**に、次の出力を参照してください。

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>ローカルの Python カーネル

ローカルの Python カーネルを選択して、セルの種類で

![ローカルの python](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>パッケージを管理します。

自分のシナリオの顧客になるパッケージをインストールする機能は、ローカルの Python 開発用に最適化モ ノの 1 つでした。 既定では、ような一般的なパッケージを含める`pandas`、`numpy`などが含まれていないパッケージは、ノートブックのセルに次のコードを記述する、想定する場合は。 

```python
import <package-name>
```

このコマンドを実行するときに`Module not found`が返されます。 パッケージが存在する場合エラーいない取得されます。

返された場合、 `Module not Found`  をクリックして、エラー**パッケージの管理**ターミナルを起動します。 パッケージをローカルでインストールできます。 パッケージをインストールするのにには、次のコマンドを使用します。

```bash
./pip install <package-name>
```

   > [!Tip]
   > Mac では、パッケージをインストールするためのターミナル ウィンドウの指示に従ってください。 

パッケージがインストールされた後 Notebook セルに移動し、次のコマンドを入力できる必要があります。

```python
import <package-name>
```

パッケージをアンインストールするには、ターミナルから次のコマンドを使用します。

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>次のステップ

既存のノートブックを使用する方法については、次を参照してください。 [notebook Azure Data Studio での管理方法](notebooks-how-to-manage.md)します。