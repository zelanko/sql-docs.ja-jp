---
title: Azure Data Studio で SQL のノートブックを使用する方法
titleSuffix: Azure Data Studio
description: Azure Data Studio で SQL のノートブックを使用する方法について説明します
ms.custom: seodec18
ms.date: 03/17/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: achatter; alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 9aad778475649280e5472f80ad96973d09803375
ms.sourcegitcommit: a9a03f9a7ec4dad507d2dfd5ca33571580114826
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "58566381"
---
# <a name="how-to-use-notebooks-in-azure-data-studio"></a>Azure Data Studio で notebook を使用する方法

この記事では、ノートブック エクスペリエンスは、Azure Data Studio を起動する方法と、独自のノートブックの作成を開始する方法について説明します。 また、さまざまなカーネルを使用して Notebook を作成する方法も示します。


## <a name="connect-to-sql-server"></a>SQL Server への接続

Azure Data Studio では、Microsoft SQL Server 接続の種類に接続することができます。
Azure データ Studio では、また、F1 キーを押して をクリックすることができます**新しい接続** し、SQL Server に接続します。

![image1](media/sql-notebooks/connection-info.png)

## <a name="launch-notebooks"></a>Notebook を起動します。

新しい notebook を起動する複数の方法はあります。

1. 移動して、**ファイル メニュー**でクリックして Azure Data Studio**新しい Notebook**します。

    ![image3](media/sql-notebooks/file-new-notebook.png)

3. 右クリックして、 **SQL Server**接続と起動**新しい Notebook**します。 
    ![image3](media/sql-notebooks/server-new-notebook.png)

4. コマンド パレットを開いて (**Ctrl + Shift + P**)) に入力し、**新しい Notebook**します。 という名前の新しいファイル`Notebook-1.ipynb`が開きます。

## <a name="supported-kernels-and-attach-to-context"></a>カーネルがサポートされているし、コンテキストにアタッチ

Azure Data Studio で Notebook のインストールは、SQL のカーネルをネイティブでサポートします。 となり、選択したかどうかは、SQL 開発者し、Notebook を使用するにはカーネルです。 

SQL カーネルが PostgreSQL のサーバー インスタンスに接続することもできます。 PostgreSQL 開発者あり、PostgreSQL サーバーに接続する場合は、ダウンロード、 [ **PostgreSQL 拡張機能**](postgres-extension.md)で Azure Data Studio の拡張機能マーケットプ レースです。

![image7](media/sql-notebooks/sql-kernel-dropdown.png)

### <a name="sql-kernel"></a>SQL のカーネル

クエリ エディターのようなノートブックのコード セルは、コーディング エクスペリエンスを日常的なタスクの豊富な SQL エディター、IntelliSense、および組み込みのコード スニペットなどの組み込みの機能を簡単に最新の SQL をサポートします。 コード スニペットを使用すると、データベース、テーブル、ビュー、ストアド プロシージャなどを作成し、既存のデータベース オブジェクトを更新する適切な SQL 構文を生成できます。 開発やテストの目的でデータベースのコピーをすばやく作成し、生成し、スクリプトを実行するには、コード スニペットを使用します。

クリックして**実行**各セルを実行します。

SQL Server インスタンスに接続する SQL カーネル

![image7](media/sql-notebooks/intellisense-code-cell.png)

クエリ結果

![Image19](media/sql-notebooks/sql-cell-results.png)

PostgreSQL のサーバー インスタンスに接続する SQL カーネル 

![Image18](media/sql-notebooks/pgsql-code-cell.png)

クエリ結果

![Image20](media/sql-notebooks/pgsql-cell-results.png)

### <a name="configure-python-for-notebooks"></a>Notebook の Python を構成します。

カーネルのドロップダウン リストから SQL とは別に、その他のカーネルのいずれかを選択するとこのするように求められます**構成の Python notebook**します。 Notebook の依存関係の指定した場所にインストールが、インストール場所を設定するかどうかを決定できます。 このインストールは時間がかかることができ、インストールが完了するまで、アプリケーションを閉じないことをお勧めします。 インストールが完了すると、サポートされている言語でコードを記述を開始できます。

![Image21](media/sql-notebooks/configure-python.png)

インストールが完了すると、出力ターミナルで実行されている Jupyter バックエンド サーバーの場所と共にタスクの履歴に通知が表示されます。

![Image22](media/sql-notebooks/jupyter-backend.png)

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

![image8](media/sql-notebooks/notebook-toolbar.png)

セルの変更が編集モードおよび markdown とする入力と同時にプレビューが表示されます。

![image9](media/sql-notebooks/notebook-markdown-cell.png)

テキスト セルの外側をクリックすると、マークダウン テキストが表示されます。

![Image10](media/sql-notebooks/notebook-markdown-preview.png)

### <a name="trusted-and-non-trusted"></a>信頼できる、非信頼

Notebook を Azure Data Studio で開くには、既定**信頼済み**します。

開くが他のソースからノートブックを開く場合**信頼されていない**モードとしやすく**信頼済み**します。

### <a name="save"></a>保存 

ノートブックを保存する**Ctrl + S**  をクリックしてまたは、**ファイルの保存の**、**ファイルとして保存しています.** と**ファイルすべて保存**ファイル メニューからコマンドと**ファイル。保存**コマンド パレットで入力したコマンド。

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark カーネル

選択、`PySpark Kernel`と、次のコード セルの種類。

**[実行]** をクリックします。

Spark アプリケーションが開始され、次の出力を返します。

![Image12](media/sql-notebooks/pyspark.png)

### <a name="spark-kernel--scala-language"></a>Spark カーネル |Scala 言語

選択、`Spark|Scala Kernel`と、次のコード セルの種類。

![Image13](media/sql-notebooks/spark-scala.png)

– 以下のオプション アイコンをクリックするとに、"セル"オプションを表示することもできます。

![Image14](media/sql-notebooks/scala-cell-options.png)

### <a name="spark-kernel--r-language"></a>Spark カーネル |R 言語

Spark の選択 |R カーネルでは、ドロップダウン リストにします。 セルに入力するか、コードを貼り付けます。 クリックして**実行**に、次の出力を参照してください。

![Image15](media/sql-notebooks/spark-r.png)

### <a name="local-python-kernel"></a>ローカルの Python カーネル

ローカルの Python カーネルを選択して、セルの種類で

![Image16](media/sql-notebooks/local-python.png)

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

既存のノートブックを使用する方法については、[notebook Azure Data Studio での管理方法](https://docs.microsoft.com/sql/big-data-cluster/notebooks-how-to-manage?view=sqlallproducts-allversions)を参照してください。