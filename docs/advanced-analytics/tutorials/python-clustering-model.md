---
title: Python のチュートリアル:ユーザーのカテゴリー化
description: この 4 部構成のチュートリアル シリーズでは、SQL Server Machine Learning Services で Python を使用した SQL データベースで K-Means を使用して、顧客のクラスタリングを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 12/17/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f5d1254c6b5c478c7bcad63da0902f21f4db70a9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306581"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>チュートリアル:SQL Server Machine Learning Services と K-Means クラスタリングを使用して顧客を分類する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この 4 部構成のチュートリアル シリーズでは、Python を使用して、[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) で K-Means クラスタリング モデルを開発および展開して、顧客データをクラスター化します。

このシリーズの第 1 部では、チュートリアルの前提条件を設定してから、サンプル データセットを SQL データベースに復元します。 このシリーズの後半では、このデータを使用して、SQL Server Machine Learning Services を使用する Python でクラスタリング モデルをトレーニングし展開します。

このシリーズの第 2 部と第 3 部では、Azure Data Studio ノートブックでいくつかの Python スクリプトを開発して、データを準備し、機械学習モデルをトレーニングします。 次に第 4 部では、ストアド プロシージャを使用して、SQL データベース内でこれらの Python スクリプトを実行します。

*クラスター化*は、グループのメンバーにある意味で類似点があるグループにデータを編成すること、として説明できます。 このチュートリアル シリーズでは、小売事業を営んでいる場合を想定しています。 **K-Means** アルゴリズムを使用して、製品の購入と返品のデータセット内で、顧客のクラスタリングを実行します。 顧客をクラスタリングすることで、特定のグループをターゲットして、マーケティングの取り組みをより効果的に進めることができます。
K-Means クラスタリングは、類似性に基づいてデータのパターンを探す*教師なし学習*アルゴリズムです。

この記事では、次の方法について学習します。

> [!div class="checklist"]
> * サンプル データベースを SQL Server インスタンスに復元する

[第 2 部](python-clustering-model-prepare-data.md)では、SQL データベースからデータを準備してクラスタリングを実行する方法を学びます。

[第 3 部](python-clustering-model-build.md)では、Python で K-Means クラスタリング モデルを作成し、トレーニングする方法を学びました。

[パート 4 ](python-clustering-model-deploy.md)では、新しいデータに基づいて Python でクラスタリングを実行できるストアド プロシージャを SQL データベースに作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

* [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) に Python 言語オプションがあること。[Windows インストール ガイド](../install/sql-machine-learning-services-windows-install.md)または [Linux インストール ガイド](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15)に記載されているインストール手順に従ってください。

* [Azure Data Studio](../../azure-data-studio/what-is.md) Azure Data Studio では、Python と SQL の両方にノートブックを使用します。 ノードブックの詳細については、「[Azure Data Studio でノートブックを使用する方法](../../azure-data-studio/sql-notebooks.md)」を参照してください。

  * Python - Jupyter Notebook や [Visual Studio Code](https://code.visualstudio.com/docs) などの独自の Python IDE を使用することもできます。これには [Python 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-python.python) と [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)を使用します。
  * SQL - [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) を使用することもできます。

* 追加の Python パッケージ - このチュートリアル シリーズの例では、インストールされていない Python パッケージを使用する可能性があります。

  **コマンド プロンプト**を開き、Azure Data Studio で使用する Python のバージョンのインストール パスに変更します。 たとえば、「 `cd %LocalAppData%\Programs\Python\Python37-32` 」のように入力します。 さらに次のコマンドを実行して、まだインストールされていないすべてのパッケージをインストールします。

  ```console
  pip install matplotlib
  pip install pandas
  pip install pyodbc
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>サンプル データベースを復元する

このチュートリアルで使用するサンプル データセットは、ダウンロードして使用できるように **.bak** データベース バックアップ ファイルに保存されています。 このデータセットは、[トランザクション処理性能評議会 (TPC)](http://www.tpc.org/default.asp) によって提供される [tpcx-bb](http://www.tpc.org/tpcx-bb/default.asp) データセットから派生しています。

1. [tpcxbb_1gb.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak) ファイルをダウンロードします。

1. Azure Data Studio で、以下の詳細情報を使用して、「[バックアップ ファイルからデータベースを復元する](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file)」に記載されている手順に従います。

   * ダウンロードした **tpcxbb_1gb.bak** ファイルからインポートします
   * ターゲット データベースに "tpcxbb_1gb" という名前を指定します

1. **dbo.customer** テーブルに対してクエリを実行することで、データベースを復元した後にデータセットが存在することを確認できます。

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを続行しない場合は、SQL Server から tpcxbb_1gb データベースを削除してください。

## <a name="next-steps"></a>次のステップ

このチュートリアル シリーズの第 1 部では、これらの手順を完了しました。

* サンプル データベースを SQL Server インスタンスに復元する

機械学習モデル用にデータを準備するには、このチュートリアル シリーズの第 2 部の手順を実行します。

> [!div class="nextstepaction"]
> [チュートリアル:SQL Server Machine Learning Services を使用して Python でクラスター化を実行するためのデータを準備する](python-clustering-model-prepare-data.md)
