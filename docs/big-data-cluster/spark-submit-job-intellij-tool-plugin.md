---
title: Azure toolkit for IntelliJ を SQL Server のビッグ データ クラスターで Spark ジョブを実行します。
titleSuffix: SQL Server big data clusters
description: For IntelliJ には、Azure Toolkit で SQL Server のビッグ データ クラスターで Spark ジョブを送信します。
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e48aebbb15b9bd684b2ed3f5d4d314191a55ba42
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860324"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-intellij"></a>IntelliJ での SQL Server のビッグ データ クラスターで Spark ジョブを送信します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

ビッグ データの SQL Server クラスターの主なシナリオの 1 つは、Spark ジョブを送信する機能です。 Spark ジョブの送信機能では、SQL Server のビッグ データ クラスターへの参照をローカル Jar、Py ファイルを送信できます。 HDFS ファイル システムに既にあるは、Jar または Py のファイルを実行することもできます。 

## <a name="prerequisites"></a>前提条件

- SQL Server のビッグ データ クラスター。
- Oracle Java Development Kit。 インストールすることができます、 [Oracle の web サイト](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)します。
- IntelliJ IDEA。 インストールすることができます、 [JetBrains の web サイト](https://www.jetbrains.com/idea/download/)します。
- Azure Toolkit for IntelliJ の拡張機能。 インストール手順については、[Azure Toolkit for IntelliJ のインストール](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation)を参照してください。

## <a name="link-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスターをリンク
1. IntelliJ IDEA ツールを開きます。

2. 自己署名証明書を使用している場合から SSL 証明書の検証を無効にする**ツール**メニューの  **Azure**、 **Spark クラスター SSL 証明書の検証**し、**無効にする**します。

    ![SQL Server のビッグ データ クラスター リンク - SSL を無効にします。](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Azure Explorer を開きます**ビュー**メニューの **ツール Windows**、し、 **Azure エクスプ ローラー**します。
4. 右クリックして**SQL Server のビッグ データ クラスター**を選択します**リンク SQL Server のビッグ データ クラスター**します。 入力、**サーバー**、**ユーザー名**と**パスワード**、順にクリックします**OK**します。

    ![ビッグ データ クラスターのリンク ダイアログ](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. 信頼されていないサーバーの証明書のダイアログ ボックスが表示されたら、クリックして**Accept**します。 後で、証明書を管理するを参照してください[サーバー証明書](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html)します。

6. リンクされたクラスターが一覧表示**SQL Server のビッグ データ クラスター**します。 でしたもリンクを解除する、クラスターを右クリックして、spark 履歴 UI と Yarn UI を開いて、spark ジョブを監視するできます。

    ![リンク クラスターのビッグ データ - コンテキスト メニュー](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-hdinsight-template"></a>HDInsight テンプレートからの Spark Scala アプリケーションを作成します。

1. IntelliJ IDEA を起動し、プロジェクトを作成します。 **新しいプロジェクト** ダイアログ ボックスで、次の手順に従います。 

   A. 選択**Azure Spark/HDInsight** > **Spark (Scala) のサンプル プロジェクト**します。

   B. **ビルド ツール**一覧で、ニーズに合わせて、次のいずれかを選択します。

      * **Maven**、Scala プロジェクト作成ウィザードのサポート
      * **SBT**、依存関係の管理と Scala プロジェクトの構築

    ![[新しいプロジェクト] ダイアログ ボックス](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. **[次へ]** を選択します。

3. Scala プロジェクト作成ウィザードでは、Scala プラグインをインストールしたかどうかを自動的に検出します。 **[インストール]** を選択します。

   ![Scala プラグインの確認](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Scala プラグインをダウンロードするには、次のように選択します。 **OK**します。 指示に従って、IntelliJ を再起動します。 

   ![Scala プラグインのインストール ダイアログ ボックス](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. **新しいプロジェクト**ウィンドウで、次の手順を実行します。  

    ![Spark SDK の選択](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   A. プロジェクトの名前と場所を入力します。

   B. **プロジェクト SDK**ドロップダウン リストで、 **Java 1.8** Spark 2.x クラスターの場合、または選択**Java 1.7** Spark 1.x クラスターの。

   c. **Spark バージョン**ドロップダウン リスト、Scala プロジェクト作成ウィザードでは、Spark SDK と Scala SDK の適切なバージョンが統合されます。 Spark クラスターのバージョンが 2.0 より前の場合は、選択**Spark 1.x**します。 それ以外の場合、選択**Spark2.x**します。 この例では**Spark 2.0.2 (Scala 2.11.8)** します。

6. **[完了]** を選択します。

7. Spark プロジェクトでは、アーティファクトが自動的に作成します。 成果物を表示するには、次の手順を実行します。

   A. **ファイル**メニューの **プロジェクト構造**します。

   B. **プロジェクト構造**ダイアログ ボックスで、**成果物**作成される既定の成果物を表示します。 プラス記号を選択して、独自のアーティファクトを作成することもできます (**+**)。

      ![アーティファクト情報 ダイアログ ボックス](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスターへのアプリケーションを送信します。
ビッグ データの SQL Server クラスターのリンクの後にアプリケーションを送信できます。

1. 構成を設定する**実行/デバッグ構成**ウィンドウで、[+]-> [**SQL Server での Apache Spark**を選択します] タブ**クラスターにリモートで実行**、としてパラメーターを設定[ok] をクリックし、します。

    ![対話型コンソール構成エントリを追加します。](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![ビッグ データ クラスターの構成リンクします。](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * **Spark クラスター (Linux のみ)** アプリケーションを実行するクラスターを選択します。

    * IntelliJ プロジェクトからアーティファクトを選択するか、ハード ドライブから 1 つを選択します。

    * **メイン クラス名**フィールド。既定値は、選択したファイルからメイン クラスです。 クラスを変更するには、省略記号ボタンを選択して (**.**) を別のクラスを選択します。   

    * **ジョブ構成**フィールド。既定値は、前に示した図として設定されます。 値を変更したり、ジョブの送信の新しいキー/値を追加できます。 詳細:[Apache Livy REST API](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![Spark の送信 ダイアログ ボックスのジョブ構成意味](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * **コマンドライン引数**フィールド。必要な場合は、メイン クラスのスペースで分割引数の値を入力することができます。

    * **Jar を参照**と**参照ファイル**フィールド。存在する場合は、参照される Jar とファイルのパスを入力できます。 詳細:[Apache Spark の構成](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![つまり Spark の送信 ダイアログ ボックスの jar ファイル](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > JARs 参照と参照されているファイルをアップロードするを参照してください。[クラスター化リソースをアップロードする方法](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)
                         
    * **アップロード パス**:Jar ファイルまたは Scala プロジェクトのリソース送信用のストレージの場所を指定できます。 サポートされているいくつかの記憶域種類があります。**Spark の対話型セッションを使用してアップロード**と**使用 WebHDFS をアップロードするには**
    
2. クリックして**SparkJobRun**選択したクラスターにプロジェクトを送信します。 **クラスターで Spark ジョブをリモート** タブは下部にあるジョブの実行の進行状況を表示します。 アプリケーションを停止するには、赤いボタンをクリックします。  

    ![リンクのビッグ データ クラスターの実行](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="spark-console"></a>Spark コンソール
Spark ローカル Console(Scala) を実行したり、Spark Livy 対話型セッション Console(Scala) を実行できます。

### <a name="spark-local-consolescala"></a>Spark ローカル Console(Scala)
WINUTILS が満たされていることを確認します。EXE の前提条件です。

1. メニュー バーに移動します**実行** > **構成の編集...**。

2. **実行/デバッグ構成**に移動します ウィンドウの左側のウィンドウで、**ビッグ データの SQL Server クラスターでの Apache Spark** > **[SQL での Spark] myApp**します。

3. メイン ウィンドウで、選択、**ローカルで実行**タブ。

4. 次の値を指定し、 **OK**:

    |プロパティ |値 |
    |----|----|
    |ジョブのメイン クラス|既定値は、選択したファイルからメイン クラスです。 クラスを変更するには、省略記号ボタンを選択して (**.**) を別のクラスを選択します。|
    |環境変数|HADOOP_HOME の値が正しいことを確認します。|
    |WINUTILS.exe の場所|パスが正しいことを確認します。|

    ![セットのローカルのコンソールの構成](./media/spark-submit-job-intellij-tool-plugin/console-set-configuration.png)

5. プロジェクトに移動します**myApp** > **src** > **メイン** > **scala**  > 。 **myApp**します。  

6. メニュー バーに移動します。**ツール** > **Spark コンソール** > **Spark のローカル Console(Scala) 実行**します。

7. 依存関係を修正する自動かどうかを確認する 2 つのダイアログ ボックスが表示されます。 その場合は、選択**自動修正**します。

    ![Spark 自動 Fix1](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix1.png)

    ![Spark 自動 Fix2](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix2.png)

8. コンソールは、次の図のようになります。 コンソール ウィンドウの種類で`sc.appName`、し、ctrl キーを押しながら Enter キーを押します。  結果が表示されます。 ローカルのコンソールを終了するには、赤いボタンをクリックします。

    ![ローカルのコンソールの結果](./media/spark-submit-job-intellij-tool-plugin/local-console-result.png)


### <a name="spark-livy-interactive-session-consolescala"></a>Livy 対話型セッション Console(Scala) を spark します。
Spark Livy 対話型セッション Console(Scala) は IntelliJ 2018.2 と 2018.3 でのみサポートされます。

1. メニュー バーに移動します**実行** > **構成の編集...**。

2. **実行/デバッグ構成**に移動します ウィンドウの左側のウィンドウで、**ビッグ データの SQL Server クラスターでの Apache Spark** > **[SQL での Spark] myApp**します。

3. メイン ウィンドウで、選択、**クラスターにリモートで実行**タブ。

4. 次の値を指定し、 **OK**:

    |プロパティ |値 |
    |----|----|
    |Spark クラスター (Linux のみ)|アプリケーションを実行する SQL Server のビッグ データ クラスターを選択します。|
    |メイン クラス名|既定値は、選択したファイルからメイン クラスです。 クラスを変更するには、省略記号ボタンを選択して (**.**) を別のクラスを選択します。|

    ![対話型コンソール セットの構成](./media/spark-submit-job-intellij-tool-plugin/interactive-console-configuration.png)

5. プロジェクトに移動します**myApp** > **src** > **メイン** > **scala**  > 。 **myApp**します。  

6. メニュー バーに移動します。**ツール** > **Spark コンソール** > **実行 Spark Livy 対話型セッション Console(Scala)** します。

7. コンソールは、次の図のようになります。 コンソール ウィンドウの種類で`sc.appName`、し、ctrl キーを押しながら Enter キーを押します。  結果が表示されます。 ローカルのコンソールを終了するには、赤いボタンをクリックします。

    ![対話型コンソールの結果](./media/spark-submit-job-intellij-tool-plugin/interactive-console-result.png)

### <a name="send-selection-to-spark-console"></a>選択範囲を Spark コンソールに送信します。

便宜上、Livy 対話型セッション Console(Scala)、ローカル コンソールにいくつかのコードを送信することによって、スクリプトの結果を確認できます。 Scala ファイルでいくつかのコードを強調表示は、右クリックし、**選択する Spark コンソールに送信**します。 選択したコードは、コンソールに送信され、実行します。 コンソールでのコードの後に、結果が表示されます。 既存の場合、コンソールは、エラーを確認します。  

   ![選択範囲を Spark コンソールに送信します。](./media/spark-submit-job-intellij-tool-plugin/send-selection-to-console.png)

## <a name="next-steps"></a>次のステップ
SQL Server のビッグ データ クラスターと関連するシナリオの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターは](big-data-cluster-overview.md)でしょうか。
