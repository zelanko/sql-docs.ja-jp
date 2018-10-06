---
title: SQL Server 2019 プレビューで notebook を使用する方法 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 989ee419406d0f69cd7bda26485d3d44cbf56550
ms.sourcegitcommit: c7d3a903eb7f410db3a0230101d24de0af17621a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2018
ms.locfileid: "48827333"
---
# <a name="how-to-use-notebooks-in-sql-server-2019-preview"></a>SQL Server 2019 プレビューで notebook を使用する方法

この記事では、SQL Server 2019 のビッグ データ クラスター上の notebook を起動する方法を示します。 また、独自のノートブックの作成を開始する方法と、クラスターに対してジョブを送信する方法も説明します。

## <a name="prerequisites"></a>前提条件

Notebook を使用するには、次の前提条件をインストールする必要があります。

- [SQL Server 2019 のビッグ データ クラスター](deployment-guidance.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [SQL Server 2019 拡張機能 (プレビュー)](../azure-data-studio/sql-server-2019-extension.md)します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="connect-to-the-sql-server-big-data-cluster-end-point"></a>SQL Server のビッグ データ クラスター エンドポイントに接続します。

クラスター内の別のエンドポイントに接続することができます。 Microsoft SQL Server 接続の種類または SQL Server のビッグ データ クラスター エンドポイントを接続することができます。

Azure Data Studio (プレビュー)、入力**F1** > **新しい接続**、し、SQL Server のビッグ データ クラスター エンドポイントに接続します。

![image1](media/notebooks-guidance/image1.png)

## <a name="browse-hdfs"></a>HDFS を参照します。
接続するは、HDFS フォルダーを参照することができます。 デプロイが完了し、することができます、WebHDFS が開始**更新**、追加**新しいディレクトリ**、**アップロード**ファイル、および**を削除**.

![イメージ 2](media/notebooks-guidance/image2.png)

これらの単純な操作では、HDFS に独自のデータを表示できます。

## <a name="launch-new-notebooks"></a>新しい Notebook を起動します。

新しい notebook を起動する複数の方法はあります。

1. ダッシュ ボードを管理します。 新しい接続を作成するのには、ダッシュ ボードが表示されます。 ダッシュ ボードからタスクを新しい Notebook をクリックします。

  ![image3](media/notebooks-guidance/image3.png)

1. HDFS/Spark 接続を右クリックし、コンテキスト メニューに新しい Notebook があります。

![image4](media/notebooks-guidance/image4.png)

ノートブックの名前を入力 (例: *Test.ipynb*) をクリック**保存**します。

![image5](media/notebooks-guidance/image5.png)

## <a name="supported-kernels-and-attach-to-context"></a>カーネルがサポートされているし、コンテキストにアタッチ

インストールでは、ノートブック、PySpark と Spark では、Spark マジック カーネル、Spark を使用して、Python、Scala のコードを記述するようにすることをサポートします。 ここには、ローカルの開発のそれぞれの目的の Python を選択するユーザーもできます。

![image6](media/notebooks-guidance/image6.png)

これらのカーネルのいずれかを選択して、仮想環境でそのカーネルをインストールしますがサポートされている言語でコードを記述することができます。

| カーネル | 説明
|---- |----
|PySpark カーネル| Spark を使用して Python コードを記述するためには、クラスターからコンピューティングします。
|Spark カーネル|Spark を使用して Scala コードを記述するためには、クラスターからコンピューティングします。
|Python カーネル|ローカル開発用の Python コードを記述します。

アタッチ先の選択では、アタッチする、カーネルのコンテキストを提供します。 SQL Server のビッグ データ クラスター エンドポイントに接続すると、既定のアタッチ先の選択は、クラスターのエンドポイントになります。

![image7](media/notebooks-guidance/image7.png)

## <a name="hello-world-in-the-different-contexts"></a>異なるコンテキストでの hello world

### <a name="pyspark-kernel"></a>Pyspark カーネル

PySpark カーネルを選択し、次のコード セルの種類。

![image8](media/notebooks-guidance/image8.png)

開始されている Spark アプリケーションは、「」を参照して表示されます、次の出力と実行をクリックしてします。

![image9](media/notebooks-guidance/image9.png)

出力は次の図のようになります。

![Image10](media/notebooks-guidance/image10.png)

### <a name="spark-kernel"></a>Spark カーネル
新しいコード セルをクリックして追加のツールバーにコマンドをコード + です。

![Image11](media/notebooks-guidance/image11.png)

セルの種類/貼り付けと、カーネルのドロップダウン リストで、Spark カーネルを選択します。 

![Image12](media/notebooks-guidance/image12.png)

クリックして**実行**開始されている Spark アプリケーションが表示され、これは、Spark セッションを作成**spark**を定義し、 **HelloWorld**オブジェクト。

ノートブックは、次の図のようになります。

![Image13](media/notebooks-guidance/image13.png)

1 回、オブジェクトの定義し、次のコードに次の Notebook セルの種類で。

![Image14](media/notebooks-guidance/image14.png)

クリックして**実行**してメニューが表示する必要があります、Notebook で、「こんにちは, world!」 で出力します。

![Image15](media/notebooks-guidance/image15.png)

### <a name="local-python-kernel"></a>ローカルの python カーネル
ローカルの Python カーネルを選択し、セルの種類で * *

![Image16](media/notebooks-guidance/image16.png)

以下の出力が表示されます。

![Image17](media/notebooks-guidance/image17.png)

### <a name="markdown-text"></a>Markdown テキスト
クリックして新しいテキスト セルを追加、+、ツールバーの [テキスト]。

![Image18](media/notebooks-guidance/image18.png)

Markdown を追加するプレビュー アイコンをクリックします

![Image19](media/notebooks-guidance/image19.png)

Markdown だけを表示に切り替えるためにもう一度プレビュー アイコンをクリックします

![Image20](media/notebooks-guidance/image20.png)

## <a name="manage-packages"></a>パッケージを管理します。
自分のシナリオの顧客になるパッケージをインストールする機能は、ローカルの Python 開発用に最適化モ ノの 1 つでした。 既定では、一般的なパッケージを含める pandas、numpy などが含まれていないパッケージが必要な場合、次のコードで記述 Notebook セルなど

```python
import <package-name>
```

このコマンドを実行すると表示されます、`Module not found`エラー。 パッケージが存在する場合エラーいない取得されます。

見つかった場合、 `Module not Found`  をクリックして、エラー、**パッケージの管理**を識別、Virtualenv のパスでターミナルを起動します。 パッケージをローカルでインストールできます。 パッケージをインストールするのにには、次のコマンドを使用します。

```
./pip install <package-name>
```

パッケージがインストールされた後 Notebook セルに移動し、次のコマンドを入力できる必要があります。

```python
import <package-name>
```

これで、セルを実行するとが表示されなく、`Module not found`エラー。

パッケージをアンインストールする場合は、ターミナルから次のコマンドを使用します。

```
./pip uninstall <package-name>
```

## <a name="next-steps"></a>次の手順

既存のノートブックを使用する方法については、次を参照してください。 [notebook Azure Data Studio での管理方法](notebooks-how-to-manage.md)します。