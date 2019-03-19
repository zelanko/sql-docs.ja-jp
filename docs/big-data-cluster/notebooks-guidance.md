---
title: Azure Data Studio でノートブックを実行します。
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスターに Azure Data Studio conneected で Jupyter Notebook を実行する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/12/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 44ba203fcd7445add8fce00dd64913f85bcf4cc1
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161659"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>SQL Server 2019 プレビューで notebook を使用する方法

この記事では、ビッグ データ クラスターで Jupyter Notebook を起動する方法と、独自のノートブックの作成を開始する方法について説明します。 また、クラスターに対してジョブを送信する方法を示します。

## <a name="prerequisites"></a>前提条件

Notebook を使用するには、次の前提条件をインストールする必要があります。

- [SQL Server 2019 のビッグ データ クラスター](deployment-guidance.md)
- [SQL Server 2019 ビッグ データ ツール](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **kubectl**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>SQL Server のビッグ データ クラスター エンドポイントに接続します。

クラスターの別のエンドポイントに接続することができます。 Microsoft SQL Server 接続の種類に、または SQL Server のビッグ データ クラスター エンドポイントに接続できます。
Azure データ studio で、F1 キーを押すし、 をクリックして**新しい接続** SQL Server のビッグ データ クラスター終了ポイントに接続できます。

![image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>HDFS を参照します。

接続するは、HDFS フォルダーを参照することができます。 デプロイが完了したら、SQL Server 開始 WebHDFS が開始されます。 WebHDFS を使用することができます**更新**、追加**新しいディレクトリ**、**アップロード**ファイル、および**削除**します。

![イメージ 2](media/notebooks-guidance/image2.png)

これらの単純な操作では、HDFS に独自のデータを表示できます。

## <a name="launch-new-notebooks"></a>新しい Notebook を起動します。

>[!NOTE]
>環境内で実行されている複数の Python プロセスがあれば、最初に削除、`.scaleoutdata`インストールされているディレクトリの下のフォルダー。 これをトリガーする必要があります、 `Reinstall Notebook dependencies` Azure Data Studio でのタスク。 すべての依存関係をインストールするまで数分をかかります。

Notebook の依存関係のインストールで問題がある場合は、Ctrl + Shift + P または Macintosh Cmd + Shift + P、および種類をクリックします`Reinstall Notebook dependencies`コマンド パレットでします。

![image3](media/notebooks-guidance/image3.png)

新しい notebook を起動する複数の方法はあります。

1. **管理ダッシュ ボード**します。 新しい接続を終了したら、ダッシュ ボードが表示されます。 クリックして**新しい Notebook**ダッシュ ボードからタスク。
  
    ![image4](media/notebooks-guidance/image4.png)

1. HDFS/Spark 接続を右クリックし、をクリックして**新しい Notebook**のコンテキスト メニュー。

    ![image5](media/notebooks-guidance/image5.png)

    という名前の新しいファイル`Notebook-0.ipynb`が開きます。

    ![image6](media/notebooks-guidance/image6.png)

コマンド パレットからノートブックを開くと、として、notebook が表示されます。`Untitled-0.ipynb`します。

## <a name="supported-kernels-and-attach-to-context"></a>カーネルがサポートされているし、コンテキストにアタッチ

Notebook のインストールには、PySpark と Spark では、Spark を使用して、Python、Scala のコードを記述するため、Spark マジックのカーネルがサポートしています。 必要に応じて、ローカル開発用の Python を選択できます。

![image7](media/notebooks-guidance/image7.png)

これらのカーネルのいずれかを選択して、インストールでは、そのカーネルを構成、仮想環境でサポートされている言語でコードを記述することができます。

|カーネル|説明
|:-----|:-----
|PySpark3、および PySpark カーネル| クラスターからの Spark のコンピューティングを使用して Python コードを記述します。
|Spark カーネル|クラスターからの Spark のコンピューティングを使用して Scala と R コードを記述します。
|Python カーネル|ローカル開発用の Python コードを記述します。

`Attach to` アタッチする、カーネルのコンテキストを提供します。 SQL Server ビッグ データ クラスターの終了ポイント、既定値に接続しているときに`Attach to`は、クラスターの場合は、その終了点。

SQL Server のビッグ データ クラスター エンドポイントに接続されていない場合は、Python が既定のカーネルは、`Attach to`は`localhost`します。

## <a name="hello-world-in-different-contexts"></a>異なるコンテキストでの hello world

### <a name="pyspark3pyspark-kernel"></a>Pyspark3/PySpark カーネル

PySpark カーネルを選択し、次のコード セルの種類。

**[実行]** をクリックします。

Spark アプリケーションが開始され、次の出力を返します。

![image8](media/notebooks-guidance/image8.png)

### <a name="spark-kernel--scala-language"></a>Spark カーネル |Scala 言語

Spark の選択 |Scala カーネルと、次のコード セルの種類。

![image9](media/notebooks-guidance/image9.png)

クリックして新しいコード セルを追加、 **+ コード**ツールバーにコマンド。

ここで、Spark を選択 |– でセルの種類/貼り付けと、カーネル用のドロップダウン リストでの Scala

![Image10](media/notebooks-guidance/image10.png)

– 以下のオプション アイコンをクリックするとに、"セル"オプションを表示することもできます。

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel--r-language"></a>Spark カーネル |R 言語

Spark の選択 |R カーネルでは、ドロップダウン リストにします。 セルに入力するか、コードを貼り付けます。 クリックして**実行**に、次の出力を参照してください。

![Image13](media/notebooks-guidance/image13.png)

### <a name="local-python-kernel"></a>ローカルの Python カーネル

ローカルの Python カーネルを選択して、セルの種類で

![Image14](media/notebooks-guidance/image14.png)

### <a name="markdown-text"></a>Markdown テキスト

クリックして新しいテキスト セルを追加、 **+ テキスト**ツールバーにコマンド。

![Image15](media/notebooks-guidance/image15.png)

編集ビューに変更するテキスト セル内をダブルクリックします 

![Image16](media/notebooks-guidance/image16.png)

編集モードのセルの変更

![Image17](media/notebooks-guidance/image17.png)

今すぐ型 markdown とすると同時にプレビューが表示されます。

![Image18](media/notebooks-guidance/image18.png)

**[実行]** をクリックします。 Spark アプリケーションが起動するには、として Spark セッションが作成されます。 **spark**を定義し、 **HelloWorld**オブジェクト。

ノートブックは、次の図のようになります。

テキスト セルの外側をクリックすると、プレビュー モードに変更され、マークダウンを非表示にします。

![Image19](media/notebooks-guidance/image19.png)


## <a name="manage-packages"></a>パッケージを管理します。
自分のシナリオの顧客になるパッケージをインストールする機能は、ローカルの Python 開発用に最適化モ ノの 1 つでした。 既定では、ような一般的なパッケージを含める`pandas`、`numpy`などが含まれていないパッケージは、ノートブックのセルに次のコードを記述する、想定する場合は。 

```python
import <package-name>
```

このコマンドを実行するときに`Module not found`が返されます。 パッケージが存在する場合エラーいない取得されます。

返された場合、 `Module not Found`  をクリックして、エラー**パッケージの管理**を識別、Virtualenv のパスでターミナルを起動します。 パッケージをローカルでインストールできます。 パッケージをインストールするのにには、次のコマンドを使用します。

```bash
./pip install <package-name>
```

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