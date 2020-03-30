---
title: 'ノートブックを実行する: Azure Data Studio'
titleSuffix: SQL Server Big Data Clusters
description: この記事では、SQL Server 2019 ビッグ データ クラスターに接続されている Azure Data Studio で Jupyter ノートブックを実行する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ff3f569761b7ba95a64f693f1726df589ce7e579
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75244102"
---
# <a name="how-to-use-notebooks-in-sql-server"></a>SQL Server でノートブックを使用する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、[**Azure Data Studio**](../azure-data-studio/download.md) の最新リリースでノートブック エクスペリエンスを起動する方法と、独自のノートブックの作成を開始する方法について説明します。 さらに、さまざまなカーネルを使用してノートブックを作成する方法についても説明します。

Azure Data Studio のノートブックの概要については、次の 5 分間の短いビデオをご覧ください。

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introduction-to-Azure-Data-Studio-Notebooks/player?WT.mc_id=dataexposed-c9-niner]


## <a name="connect-to-sql-server"></a>SQL Server への接続

Azure Data Studio で Microsoft SQL Server 接続の種類に接続できます。
Azure Data Studio では、F1 キーを押して、 **[新しい接続]**  をクリックし、SQL Server に接続することもできます。

![接続情報](media/notebooks-guidance/connection-info.png)

## <a name="launch-notebooks"></a>ノートブックを起動する

新しいノートブックを起動するには、複数の方法があります。

- Azure Data Studio の **[ファイル] メニュー**に移動し、 **[新しいノートブック]** をクリックします。

    ![新しいノートブック](media/notebooks-guidance/file-new-notebook.png)

- **[SQL Server]** 接続を右クリックして、 **[新しいノートブック]** を開始します。

    ![新しいノートブック](media/notebooks-guidance/server-new-notebook.png)

- コマンド パレット (**Ctrl + Shift + P**) を開き、 **[新しいノートブック]** に入力します。 `Notebook-1.ipynb` という名前の新しいファイルが開きます。

## <a name="supported-kernels-and-attach-to-context"></a>サポートされているカーネルとコンテキストへのアタッチ

Azure Data Studio でノートブックをインストールすると、SQL カーネルがネイティブにサポートされます。 SQL 開発者がノートブックを使用する場合は、これが選択されたカーネルになります。 

また、SQL カーネルを使用して、PostgreSQL サーバー インスタンスに接続することもできます。 PostgreSQL 開発者であり、ノートブックを PostgreSQL サーバーに接続する場合は、Azure Data Studio 拡張機能 Marketplace で [**PostgreSQL 拡張機能**](../azure-data-studio/postgres-extension.md)をダウンロードしてから、**新しいノートブック**を起動して、ノートブック インスタンスを開き、PostgreSQL サーバーに接続します。

![PostgreSQL 接続](media/notebooks-guidance/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL カーネル

このノートブック内のコード セルでは、クエリ エディターと同様に、最新の SQL コーディング エクスペリエンスがサポートされており、豊富な SQL エディター、IntelliSense、組み込みのコード スニペットなどの組み込みの機能を使用して、日常的なタスクを簡単に行うことができます。 コード スニペットを使用すると、データベース、テーブル、ビュー、ストアド プロシージャなどを作成するための適切な SQL 構文を生成したり、既存のデータベース オブジェクトを更新したりすることができます。 開発またはテストを目的としたデータベースのコピーをすばやく作成したり、スクリプトを生成および実行したりするには、コード スニペットを使用します。

**[実行]** をクリックして、各セルを実行します。

SQL Server インスタンスに接続する SQL カーネル

![SQL カーネル](media/notebooks-guidance/intellisense-code-cell.png)

クエリ結果

![Query results](media/notebooks-guidance/sql-cell-results.png)

PostgreSQL サーバー インスタンスに接続する SQL カーネル 

![PostgreSQL 接続](media/notebooks-guidance/pgsql-code-cell.png)

クエリ結果

![Query results](media/notebooks-guidance/pgsql-cell-results.png)

SQL カーネルにアタッチされている既存のノートブックにテキスト セルを追加する場合は、ツールバーの **[+Text]** コマンドをクリックします。

![ノートブック ツール バー](media/notebooks-guidance/notebook-toolbar.png)

セルは編集モードに変わり、「markdown」と入力すると、プレビューが同時に表示されます。

![Markdown セル](media/notebooks-guidance/notebook-markdown-cell.png)

テキスト セルの外側をクリックすると、markdown テキストが表示されます。

![Markdown テキスト](media/notebooks-guidance/notebook-markdown-preview.png)


### <a name="configure-python-for-notebooks"></a>ノートブック用の Python の構成

[カーネル] ドロップダウンから、SQL 以外の他のカーネルを選択すると、**ノートブック用に Python を構成**するよう求められます。 ノートブックの依存関係は、指定した場所にインストールされますが、インストールの場所を設定するかどうかを決めることができます。 このインストールには時間がかかる場合があるため、インストールが完了するまでアプリケーションを終了しないことをお勧めします。 インストールが完了すると、サポートされている言語でコードの記述を開始できます。

![Python の構成](media/notebooks-guidance/configure-python.png)

インストールが成功すると、出力ターミナルで実行されている Jupyter バックエンド サーバーの場所と共に、タスク履歴に通知が表示されます。

![Jupyter バックエンド](media/notebooks-guidance/jupyter-backend.png)

|カーネル|説明
|:-----|:-----
| SQL カーネル | リレーショナル データベースを対象とした SQL コードを記述します。
|PySpark3 と PySpark カーネル| クラスターから Spark コンピューティングを使用して Python コードを作成します。
|Spark カーネル|クラスターから Spark コンピューティングを使用して Scala および R コードを作成します。
|Python カーネル|ローカル開発用の Python コードを作成します。

`Attach to` によって、アタッチするカーネルのコンテキストが提供されます。 SQL カーネルを使用している場合は、任意の SQL Server インスタンスに `Attach to` することができます。

Python3 カーネルを使用している場合、`Attach to` は `localhost` です。 このカーネルは、ローカルの Python 開発に使用できます。

SQL Server 2019 ビッグ データ クラスターに接続している場合、既定の `Attach to` がクラスターのエンド ポイントになり、クラスターの Spark コンピューティングを使用して Python、Scala、R コードを送信できるようになります。

### <a name="code-cells-and-markdown-cells"></a>コードセルと Markdown セル

ツールバーの **[+Code]** コマンドをクリックして、新しいコード セルを追加します。

ツールバーの **[+Text]** コマンドをクリックして、新しいテキスト セルを追加します。

![ノートブック ツール バー](media/notebooks-guidance/notebook-toolbar.png)

セルは編集モードに変わり、「markdown」と入力すると、プレビューが同時に表示されます。

![Markdown セル](media/notebooks-guidance/notebook-markdown-cell.png)

テキスト セルの外側をクリックすると、markdown テキストが表示されます。

![Markdown テキスト](media/notebooks-guidance/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>"信頼されている" と "信頼されていない"

Azure Data Studio で開いているノートブックは、既定で**信頼されている**状態です。

他のソースからノートブックを開くと、**信頼されていない**モードで開かれます。その後、**信頼されている**状態にすることができます。

### <a name="run-cells"></a>セルの実行
ノートブックですべてのセルを実行する場合は、ツールバーの **[Run Cells]\(セルの実行\)** ボタンをクリックします。

![Markdown テキスト](media/notebooks-guidance/run-cell.png)


### <a name="clear-results"></a>[結果をクリア]

ノートブックで実行されたすべてのセルの結果を消去する場合は、ツールバーの **[結果をクリア]** ボタンをクリックします。

![Markdown テキスト](media/notebooks-guidance/clear-results.png)

### <a name="save"></a>保存

ノートブックを保存するには、次のいずれかの操作を実行します。

- Ctrl + S を選択します
- **[ファイル]**  > 、 **[保存]** の順にクリックします
- **[ファイル]**  > 、 **[名前を付けて保存]** の順にクリックします
- **[ファイル]**  > 、 **[すべて保存]** の順にクリックします 
- コマンドパレットで、「**ファイル:保存**」と入力します。 

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark カーネル

`PySpark Kernel` を選択して、セルに次のコードを入力します。

**[実行]** をクリックします。

Spark アプリケーションが起動し、次の出力が返されます。

![Spark アプリケーション](media/notebooks-guidance/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark カーネル | Scala 言語

`Spark|Scala Kernel` を選択して、セルに次のコードを入力します。

![Spark Scala](media/notebooks-guidance/spark-scala.png)

下のオプションアイコンをクリックすると、"セル オプション" を表示することもできます。

![セル オプション](media/notebooks-guidance/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark カーネル | R 言語

カーネルのドロップダウンで Spark | R を選択します。 セルにコードを入力するか、貼り付けます。 **[実行]** をクリックすると、次の出力が表示されます。

![Spark R](media/notebooks-guidance/spark-r.png)

### <a name="local-python-kernel"></a>ローカル Python カーネル

ローカルの Python カーネルを選択し、セルに次のように入力します。

![Local python](media/notebooks-guidance/local-python.png)

## <a name="manage-packages"></a>パッケージの管理

ローカルの Python 開発向けに最適化されたものの 1 つは、顧客がシナリオに必要とするパッケージをインストールする機能を含めることでした。 既定では、`pandas` や `numpy` などの共通パッケージが含まれていますが、含まれていないパッケージを想定している場合は、ノートブック セルに次のコードを記述します。 

```python
import <package-name>
```

このコマンドを実行すると、`Module not found` が返されます。 パッケージが存在する場合、このエラーは表示されません。

`Module not Found` エラーが返された場合は、 **[パッケージの管理]** をクリックしてターミナルを起動します。 パッケージをローカルにインストールできるようになりました。 次のコマンドを使用して、パッケージをインストールします。

```bash
./pip install <package-name>
```

   > [!Tip]
   > Mac では、ターミナル ウィンドウの指示に従ってパッケージをインストールします。 

パッケージがインストールされたら、ノートブック セルに移動して、次のコマンドを入力することができます。

```python
import <package-name>
```

パッケージをアンインストールするには、ターミナルから次のコマンドを使用します。

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>次のステップ

既存のノートブックを操作する方法については、「[Azure Data Studio でノートブックを管理する方法](notebooks-how-to-manage.md)」を参照してください。