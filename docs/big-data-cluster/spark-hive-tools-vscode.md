---
title: Spark & Hive ツールを使用して Spark ジョブを実行し SQL Server ビッグデータクラスターで VS Code します
titleSuffix: SQL Server big data clusters
description: Spark & Hive Tools for Visual Studio Code を使用して spark ジョブを SQL Server ビッグデータクラスターに送信します。
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4458666792d7f4629b4e1820e98e2dbb9901c2b6
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425982"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-cluster-in-visual-studio-code"></a>Visual Studio Code の SQL Server ビッグデータクラスターで Spark ジョブを送信する

Spark & Hive Tools for Visual Studio Code を使用して Apache Spark 用の PySpark スクリプトを作成して送信する方法について説明します。まず、Spark & Hive ツールを Visual Studio Code にインストールする方法について説明します。次に、Spark にジョブを送信する方法について説明します。  

Spark & Hive ツールは、Windows、Linux、macOS など、Visual Studio Code でサポートされているプラットフォームにインストールできます。 以下では、さまざまなプラットフォームの前提条件について説明します。


## <a name="prerequisites"></a>必須コンポーネント

この記事の手順を完了するには、次の項目が必要です。

- SQL Server ビッグデータクラスター。 「[ビッグデータクラスターの SQL Server](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions)」を参照してください。
- [Visual Studio Code](https://code.visualstudio.com/)。
- [Mono](https://www.mono-project.com/docs/getting-started/install/)。 Mono は、Linux と macOS でのみ必要です。
- [Visual Studio Code 用に PySpark interactive 環境を設定](https://docs.microsoft.com/azure/hdinsight/set-up-pyspark-interactive-environment)します。
- **Hdexample**という名前のローカルディレクトリ。  この記事では、 **c/hdexを**使用します。

## <a name="install-spark--hive-tools"></a>Spark & Hive ツールをインストールする

前提条件を完了したら、Visual Studio Code 用の Spark & Hive ツールをインストールできます。  Spark & Hive ツールをインストールするには、次の手順を実行します。

1. Visual Studio Code を開きます。

2. メニューバーから [**表示** > ] **[拡張機能]** に移動します。

3. 検索ボックスに、「 **Spark & Hive**」と入力します。

4. 検索結果から **[Spark & Hive ツール]** を選択し、 **[インストール]** を選択します。  

   ![拡張機能のインストール](./media/spark-hive-tools-vscode/extension.png)

5. 必要に応じて再読み込みします。

## <a name="open-work-folder"></a>作業フォルダーを開く

次の手順を実行して、作業フォルダーを開き、Visual Studio Code でファイルを作成します。

1. メニューバーで、[**ファイル** > ] **[フォルダーを開く...** ] の順に移動します。次に、 **[フォルダーの選択]** ボタンを選択します。   >  左側の **[エクスプローラー]** ビューにフォルダーが表示されます。

2. **エクスプローラー** ビューで、 フォルダー、 **hdexample**の順に選択し、作業フォルダーの横にある **新しいファイル** アイコンを選択します。

   ![新しいファイル](./media/spark-hive-tools-vscode/new-file.png)

3. 新しいファイルに`.py` (Spark スクリプト) ファイル拡張子を付けます。  この例では、 **HelloWorld.py**を使用します。
4. 次のコードをコピーしてスクリプトファイルに貼り付けます。
   ```python
    import sys
    from operator import add
    from pyspark.sql import SparkSession, Row
    
    spark = SparkSession\
        .builder\
        .appName("PythonWordCount")\
        .getOrCreate()
    
    data = [Row(col1='pyspark and spark', col2=1), Row(col1='pyspark', col2=2), Row(col1='spark vs hadoop', col2=2), Row(col1='spark', col2=2), Row(col1='hadoop', col2=2)]
    df = spark.createDataFrame(data)
    lines = df.rdd.map(lambda r: r[0])

    counters = lines.flatMap(lambda x: x.split(' ')) \
        .map(lambda x: (x, 1)) \
        .reduceByKey(add)
    
    output = counters.collect()
    sortedCollection = sorted(output, key = lambda r: r[1], reverse = True)
    
    for (word, count) in sortedCollection:
        print("%s: %i" % (word, count))
   ```

## <a name="link-a-sql-server-big-data-cluster"></a>SQL Server ビッグデータクラスターのリンク

Visual Studio Code からクラスターにスクリプトを送信するには、SQL Server ビッグデータクラスターをリンクする必要があります。

1. メニューバーから [**コマンドパレット**の**表示** > ...] に移動し **、「Spark/Hive」と入力します。クラスター**をリンクします。

   ![クラスターのリンクコマンド](./media/spark-hive-tools-vscode/link-cluster-command.png)

2. [リンクされたクラスターの種類] を選択して**ビッグデータ SQL Server**します。

3. ビッグデータエンドポイント SQL Server 入力します。

4. ビッグデータクラスターのユーザー名 SQL Server 入力します。

5. ユーザー管理者のパスワードを入力してください。

6. クラスターの表示名を設定します (省略可能)。

7. クラスターを一覧表示し、確認のために**出力**ビューを確認します。

## <a name="list-clusters"></a>クラスターの一覧表示

1. メニューバーから [**コマンドパレット**の**表示** > ...] に移動し **、「Spark/Hive」と入力します。クラスター**を一覧表示します。

2. **出力**ビューを確認します。  このビューには、リンクされたクラスターが表示されます。

    ![既定のクラスター構成を設定する](./media/spark-hive-tools-vscode/list-cluster-result.png)

## <a name="set-default-cluster"></a>既定のクラスターの設定

1. [前](#open-work-folder)に作成したフォルダー **Hdexample**開きます (閉じている場合)。  

2. [前](#open-work-folder)の手順で作成した**HelloWorld.py**ファイルを選択すると、スクリプトエディターに表示されます。

3. クラスターをまだリンクしていない場合は、リンクします。

4. スクリプトエディターを右クリックし、[Spark **/Hive] を選択します。既定のクラスター**を設定します。   

5. 現在のスクリプトファイルの既定のクラスターとしてクラスターを選択します。 ツールによって構成ファイルが自動的に更新され**ます。Vscode\\ json**。 

   ![既定のクラスター構成の設定](./media/spark-hive-tools-vscode/set-default-cluster-configuration.png)

## <a name="submit-interactive-pyspark-queries"></a>対話型の PySpark クエリを送信する

次の手順に従って、対話型の PySpark クエリを送信できます。

1. [前](#open-work-folder)に作成したフォルダー **hdexample**開きます (閉じている場合)。  

2. [前](#open-work-folder)の手順で作成した**HelloWorld.py**ファイルを選択すると、スクリプトエディターに表示されます。

3. クラスターをまだリンクしていない場合は、リンクします。

4. すべてのコードを選択し、スクリプトエディターを右クリックし**て、[Spark] を選択します。PySpark Interactive**を使用してクエリを送信するか、 **Ctrl + Alt + I キー**を使用します。

   ![pyspark interactive コンテキストメニュー](./media/spark-hive-tools-vscode/pyspark-interactive-right-click.png)

5. 既定のクラスターを指定していない場合は、クラスターを選択します。 しばらくすると、Python の**対話型**結果が新しいタブに表示されます。また、このツールでは、コンテキストメニューを使用して、スクリプトファイル全体ではなくコードブロックを送信することもできます。 

   ![pyspark 対話型 python 対話型ウィンドウ](./media/spark-hive-tools-vscode/pyspark-interactive-python-interactive-window.png) 

6. **「%% Info」** と入力し、 **Shift + enter**キーを押してジョブ情報を表示します。 (オプション)

   ![ジョブ情報の表示](./media/spark-hive-tools-vscode/pyspark-interactive-view-job-information.png)

   > [!NOTE] 
   >
   > [設定] で **[Python 拡張有効]** がオフになっている場合 (既定の設定がオンになっている場合)、送信された pyspark の相互作用の結果は古いウィンドウを使用します。
   >
   > ![pyspark interactive python 拡張機能が無効になっています](./media/spark-hive-tools-vscode/pyspark-interactive-python-extension-disabled.png)


## <a name="submit-pyspark-batch-job"></a>PySpark batch ジョブの送信

1. [前](#open-work-folder)に作成したフォルダー **hdexample**開きます (閉じている場合)。  

2. [前](#open-work-folder)の手順で作成した**HelloWorld.py**ファイルを選択すると、スクリプトエディターに表示されます。

3. クラスターをまだリンクしていない場合は、リンクします。

4. スクリプトエディターを右クリックし、[Spark] **を選択します。PySpark Batch**、またはショートカット**キー Ctrl + Alt + H**を使用します。 

5. 既定のクラスターを指定していない場合は、クラスターを選択します。 Python ジョブを送信すると、Visual Studio Code の**出力**ウィンドウに送信ログが表示されます。 **SPARK UI url**と**Yarn ui url**も表示されます。 Web ブラウザーで URL を開いて、ジョブの状態を追跡することができます。

   ![Python ジョブの結果の送信](./media/spark-hive-tools-vscode/submit-pythonjob-result.png) 

## <a name="apache-livy-configuration"></a>Apache Livy の構成

[Apache Livy](https://livy.incubator.apache.org/)の構成はサポートされており、で設定でき**ます。** ワークスペースフォルダー内の Vscode\ json。 現時点では、Livy 構成では Python スクリプトのみがサポートされています。 詳細については、「 [LIVY README](https://github.com/cloudera/livy/blob/master/README.rst )」を参照してください。

### <a id="triggerlivyconf"></a>**Livy 構成をトリガーする方法**

#### <a name="method-1"></a>方法 1

1. メニューバーで、[**ファイル** >  > ] [設定] の順に移動**します。**  
2. **[検索の設定]** テキストボックス**に「HDInsight ジョブ sumission:Livy Conf**。  
3. 関連する検索結果に対して **[Edit in settings. json]** を選択します。

#### <a name="method-2"></a>方法 2

ファイルを送信すると、 `.vscode`フォルダーが自動的に作業フォルダーに追加されることがわかります。 Livy の構成を確認するには`.vscode\settings.json`、をクリックします。

+ プロジェクトの設定:

    ![Livy の構成](./media/spark-hive-tools-vscode/hdi-livyconfig.png)

>[!NOTE]
>設定**Drivermomory**と**executormomry**場合は、値を単位で設定します (たとえば、1g または)。 

### <a name="supported-livy-configurations"></a>サポートされている Livy 構成

#### <a name="post-batches"></a>POST/バッチ

**要求本文**

| NAME | description | type |
| :- | :- | :- |
| file | 実行するアプリケーションを含むファイル | パス (必須) |
| proxyUser | ジョブの実行時に権限を借用するユーザー | string |
| className | アプリケーション Java/Spark main クラス | string |
| value | アプリケーションのコマンドライン引数 | 文字列の一覧 |
| jar | このセッションで使用される jar | 文字列の一覧 |
| pyFiles | このセッションで使用される Python ファイル | 文字列の一覧 |
| files | このセッションで使用されるファイル | 文字列の一覧 |
| driverMemory | ドライバープロセスに使用するメモリの量 | string |
| driverCores | ドライバープロセスに使用するコアの数 | ssNoversion |
| executorMemory | 実行プログラムごとに使用するメモリの量 | string |
| executorCores | 実行プログラムごとに使用するコアの数 | ssNoversion |
| numExecutors | このセッションで起動する実行プログラムの数 | ssNoversion |
| アーカイブ | このセッションで使用するアーカイブ | 文字列の一覧 |
| queue | 送信先の YARN キューの名前 | string |
| NAME | このセッションの名前 | string |
| sd.conf | Spark の構成プロパティ | キーのマップ = val |

#### <a name="response-body"></a>応答本文

作成されたバッチオブジェクト。

| NAME | description | type |
| :- | :- | :- |
| id | セッション id | ssNoversion |
| appId | このセッションのアプリケーション id | String |
| appInfo | アプリケーションの詳細情報 | キーのマップ = val |
| ログ | ログ行 | 文字列の一覧 |
| state | バッチの状態 | string |

>[!NOTE]
>割り当てられた Livy config は、スクリプトの送信時に出力ペインに表示されます。

## <a name="additional-features"></a>その他の機能

Spark & Hive for Visual Studio Code は次の機能をサポートしています。

- **IntelliSense のオートコンプリート**。 キーワード、メソッド、変数などの候補がポップアップ表示されます。 異なるアイコンは、さまざまな種類のオブジェクトを表します。

    ![Visual Studio Code IntelliSense オブジェクトの種類用の Spark & Hive ツール](./media/spark-hive-tools-vscode/hdinsight-for-vscode-auto-complete-objects.png)
- **IntelliSense エラーマーカー**。 言語サービスでは、Hive スクリプトの編集エラーに下線が引かれます。     
- **構文の強調**表示。 言語サービスでは、変数、キーワード、データ型、関数などを区別するためにさまざまな色が使用されます。 

    ![Visual Studio Code 構文の強調表示用の Spark & Hive ツール](./media/spark-hive-tools-vscode/hdinsight-for-vscode-syntax-highlights.png)

## <a name="unlink-cluster"></a>クラスターのリンク解除

1. メニューバーから [**コマンドパレット**の**表示** > ...] に移動し、 **「Spark/Hive」と入力します。クラスター**のリンクを解除します。  

2. リンクを解除するクラスターを選択します。  

3. 確認のために**出力**ビューを確認します。  

## <a name="next-steps"></a>次の手順
ビッグデータクラスターとそれに関連するシナリオの SQL Server の詳細については、「[ビッグデータ](https://docs.microsoft.com/sql/big-data-cluster/big-data-cluster-overview?view=sqlallproducts-allversions)クラスターの SQL Server」を参照してください。
