---
title: SQL Server 2019 ビッグ データ クラスター上のサンプルの notebook の実行 |Microsoft Docs
description: このチュートリアルを読み込む方法、実行、SQL Server 2019 ビッグ データ クラスター (プレビュー) のサンプルの Spark notebook を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/17/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 811c94615f0d69886f0f538357529ad3125e2925
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644236"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-2019-big-data-cluster"></a>チュートリアル: SQL Server 2019 ビッグ データ クラスター上のサンプルの notebook を実行します。

このチュートリアルでは、読み込みを SQL Server 2019 ビッグ データ クラスター (プレビュー) で Azure Data Studio で、notebook を実行する方法について説明します。 これにより、データ サイエンティストやデータ エンジニアは、Python、R、または Scala コードをクラスターに対して実行できます。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[サンプルを Spark](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) GitHub でします。

## <a id="prereqs"></a> 前提条件

* [Kubernetes でのビッグ データ クラスター デプロイ](deployment-guidance.md)します。
* [Azure Data Studio と SQL Server 2019 拡張機能をインストール](deploy-big-data-tools.md)します。
* [クラスターにサンプル データを読み込む](#sampledata)します。

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="download-the-sample-notebook-file"></a>サンプルのノートブック ファイルをダウンロードします。

次の手順を使用して、サンプルのノートブック ファイルを読み込む**spark sql.ipynb** Azure Data Studio にします。

1. Bash コマンド プロンプト (Linux) または Windows PowerShell を開きます。

1. サンプルのノートブック ファイルをダウンロードするディレクトリに移動します。

1. 次の実行**curl**ノートブック ファイルを GitHub からダウンロードするコマンド。

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/spark-sql.ipynb' -o spark-sql.ipynb
   ```

## <a name="open-the-notebook"></a>ノートブックを開きます

次の手順では、Azure Data Studio で、ノートブック ファイルを開く方法を示しています。

1. Azure Data Studio、ビッグ データ クラスターの HDFS/Spark ゲートウェイに接続します。 詳細については、次を参照してください。 [HDFS/Spark ゲートウェイへの接続](deploy-big-data-tools.md#hdfs)します。

1. HDFS/Spark ゲートウェイ接続をダブルクリックして、**サーバー**ウィンドウ。 選び**Notebook を開いて**します。

   ![ノートブックを開く](media/tutorial-notebook-spark/azure-data-studio-open-notebook.png)

1. 待つ、**カーネル**および対象のコンテキスト (**にアタッチ**) が設定されます。 設定、**カーネル**に**PySpark3**、設定と**にアタッチ**ビッグ データ クラスター エンドポイントの IP アドレスにします。

   ![カーネルの設定にアタッチ](media/tutorial-notebook-spark/set-kernel-and-attach-to.png)

## <a name="run-the-notebook-cells"></a>Notebook セルを実行します。

各 notebook セルを実行するには、セルの左側の [再生] ボタンを押します。 セルの実行が完了した後、ノートブックの結果が表示されます。

![ノートブック セルを実行します。](media/tutorial-notebook-spark/run-notebook-cell.png)

連続サンプルの notebook 内の各セルを実行します。 ビッグ データの SQL Server クラスターで notebook の使用に関する詳細については、次のリソースを参照してください。

- [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)
- [Azure Data Studio でノートブックを管理する方法](notebooks-how-to-manage.md)

## <a name="next-steps"></a>次の手順

ノートブックについて説明します。
> [!div class="nextstepaction"]
> [ノートブックについて説明します](notebooks-guidance.md)