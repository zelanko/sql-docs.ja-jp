---
title: Azure Data Studio でノートブックを実行します。
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、SQL Server 2019 のビッグ データ クラスターに Azure Data Studio conneected で Jupyter Notebook を実行する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: af1393b38b297e451903d5a39942a3e878c88ee6
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53246611"
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

## <a name="connect-to-the-hadoop-gateway-knox-end-point"></a>Hadoop ゲートウェイ Knox 終了ポイントに接続するには

クラスターの別のエンドポイントに接続することができます。 Microsoft SQL Server 接続の種類にまたは HDFS/Spark ゲートウェイ エンドポイントを接続することができます。
Azure データ Studio (プレビュー) で、F1 キーを押して、をクリックして**新しい接続** HDFS/Spark ゲートウェイ エンドポイントに接続できます。

![image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>HDFS を参照します。

接続するは、HDFS フォルダーを参照することができます。 デプロイが完了し、することができます、WebHDFS が開始**更新**、追加**新しいディレクトリ**、**アップロード**ファイル、および**を削除**.

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

  たとえば、ノートブックの名前を指定`Test.ipynb`します。 **[保存]** をクリックします。

![image6](media/notebooks-guidance/image6.png)

## <a name="supported-kernels-and-attach-to-context"></a>カーネルがサポートされているし、コンテキストにアタッチ

Notebook のインストールには、PySpark と Spark では、Spark を使用して、Python、Scala のコードを記述するため、Spark マジックのカーネルがサポートしています。 必要に応じて、ローカル開発用の Python を選択できます。

![image7](media/notebooks-guidance/image7.png)

これらのカーネルのいずれかを選択して、仮想環境でそのカーネルをインストールしますがサポートされている言語でコードを記述することができます。

|カーネル|説明
|:-----|:-----
|PySpark カーネル|クラスターからの Spark のコンピューティングを使用して Python コードを記述します。
|Spark カーネル|クラスターからの Spark のコンピューティングを使用して Scala コードを記述します。
|Python カーネル|ローカル開発用の Python コードを記述します。

`Attach to`をアタッチする、カーネルのコンテキストを提供します。 HDFS/Spark ゲートウェイ (Knox) の末尾に接続している場合は、既定値をポイント`Attach to`は、クラスターの場合は、その終了点。

![image8](media/notebooks-guidance/image8.png)

## <a name="hello-world-in-different-contexts"></a>異なるコンテキストでの hello world

### <a name="pyspark-kernel"></a>Pyspark カーネル

PySpark カーネルを選択し、次のコード セルの種類。

![image9](media/notebooks-guidance/image9.png)

開始されている Spark アプリケーションは、「」を参照して表示されます、次の出力と実行をクリックしてします。

![Image10](media/notebooks-guidance/image10.png)

出力は次の図のようになります。

![Image11](media/notebooks-guidance/image11.png)

### <a name="spark-kernel"></a>Spark カーネル
クリックして新しいコード セルを追加、 **+ コード**ツールバーにコマンド。

![Image12](media/notebooks-guidance/image12.png)

以下のオプション アイコンをクリックするとに、"セル"オプションを表示することもできます。

![Image13](media/notebooks-guidance/image13.png)

すべてのセルにするためのオプションを次に示します

![Image14](media/notebooks-guidance/image14.png)-

セルの種類/貼り付けと、カーネル用のドロップダウン リストで、Spark カーネルを選択します。

![Image15](media/notebooks-guidance/image15.png)

をクリックして**実行**Spark アプリケーションを起動することがわかり、これと Spark セッションが作成されます**spark**を定義し、 **HelloWorld**オブジェクト。

ノートブックは、次の図のようになります。

![Image16](media/notebooks-guidance/image16.png)

次のノートブック セルのオブジェクトを定義した後は、次のコードに入力します。

![Image17](media/notebooks-guidance/image17.png)

クリックして**実行**してメニューが表示する必要があります、Notebook で、「こんにちは, world!」 で出力します。

![Image18](media/notebooks-guidance/image18.png)

### <a name="local-python-kernel"></a>ローカルの python カーネル
ローカルの Python カーネルを選択して、セルの種類で

![Image19](media/notebooks-guidance/image19.png)

以下の出力が表示されます。

![Image20](media/notebooks-guidance/image20.png)

### <a name="markdown-text"></a>Markdown テキスト
クリックして新しいテキスト セルを追加、 **+ テキスト**ツールバーにコマンド。

![Image21](media/notebooks-guidance/image21.png)

Markdown を追加するプレビュー アイコンをクリックします

![Image22](media/notebooks-guidance/image22.png)

Markdown だけを表示に切り替えるためにもう一度プレビュー アイコンをクリックします

![Image23](media/notebooks-guidance/image23.png)

## <a name="manage-packages"></a>パッケージを管理します。
自分のシナリオの顧客になるパッケージをインストールする機能は、ローカルの Python 開発用に最適化モ ノの 1 つでした。 既定では、一般的なパッケージを含める pandas、numpy などが含まれていないパッケージが必要な場合、次のコードで記述 Notebook セルなど。 

```python
import <package-name>
```

このコマンドを実行すると表示されます、`Module not found`エラー。 パッケージが存在する場合エラーいない取得されます。

見つかった場合、 `Module not Found`  をクリックして、エラー**パッケージの管理**を識別、Virtualenv のパスでターミナルを起動します。 パッケージをローカルでインストールできます。 パッケージをインストールするのにには、次のコマンドを使用します。

```bash
./pip install <package-name>
```

パッケージがインストールされた後 Notebook セルに移動し、次のコマンドを入力できる必要があります。

```python
import <package-name>
```

これで、セルを実行するとが表示されなく、`Module not found`エラー。

パッケージをアンインストールするには、ターミナルから次のコマンドを使用します。

```bash
./pip uninstall <package-name>
```

## <a name="next-steps"></a>次の手順

既存のノートブックを使用する方法については、次を参照してください。 [notebook Azure Data Studio での管理方法](notebooks-how-to-manage.md)します。