---
title: サンプルの notebook の実行 |Microsoft Docs
titleSuffix: SQL Server big data clusters
description: このチュートリアルを読み込む方法、実行、SQL Server 2019 ビッグ データ クラスター (プレビュー) のサンプルの Spark notebook を示します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 12/06/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b07f552259aad61c03822ab5c9efd859f3244307
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728346"
---
# <a name="tutorial-run-a-sample-notebook-on-a-sql-server-big-data-cluster"></a>チュートリアル:ビッグ データの SQL Server クラスターでのサンプルの notebook を実行します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、読み込みを SQL Server 2019 ビッグ データ クラスター (プレビュー) で Azure Data Studio で、notebook を実行する方法について説明します。 これにより、データ サイエンティストやデータ エンジニアは、Python、R、または Scala コードをクラスターに対して実行できます。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[サンプルを Spark](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark) GitHub でします。

## <a id="prereqs"></a> 前提条件

- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
- [ビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)

## <a name="download-the-sample-notebook-file"></a>サンプルのノートブック ファイルをダウンロードします。

次の手順を使用して、サンプルのノートブック ファイルを読み込む**spark sql.ipynb** Azure Data Studio にします。

1. Bash コマンド プロンプト (Linux) または Windows PowerShell を開きます。

1. サンプルのノートブック ファイルをダウンロードするディレクトリに移動します。

1. 次の実行**curl**ノートブック ファイルを GitHub からダウンロードするコマンド。

   ```bash
   curl 'https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-loading/transform-csv-files.ipynb' -o transform-csv-files.ipynb
   ```

## <a name="open-the-notebook"></a>ノートブックを開きます

次の手順では、Azure Data Studio で、ノートブック ファイルを開く方法を示しています。

1. Azure データ studio では、ビッグ データ クラスターのマスター インスタンスに接続します。 詳細については、次を参照してください。[ビッグ データ クラスターに接続する](connect-to-big-data-cluster.md)します。

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
