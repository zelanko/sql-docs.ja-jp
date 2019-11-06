---
title: K-Means クラスタリングを使用して顧客を分類する方法
description: この 4 部構成のチュートリアルシリーズでは、SQL Server Machine Learning Services で Python を使用した SQL database で K-Means アルゴリズムを使用して、顧客のクラスタリングを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 78a5999bc0c00a72edcc631877fdfed647024bc5
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294367"
---
# <a name="tutorial-categorizing-customers-using-k-means-clustering-with-sql-server-machine-learning-services"></a>チュートリアル:K-Means クラスタリングを使用した顧客の分類 - SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この 4 部構成のチュートリアルシリーズでは、お客様のデータをクラスター化するために、Python を使用して、 [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) で K-Means クラスターモデルを開発およびデプロイします。

このシリーズの第1部では、チュートリアルの前提条件を設定してから、サンプルデータセットを SQL database に復元します。 このシリーズの後半で、このデータを使用して、SQL Server Machine Learning Services を使用した Python でのクラスターモデルのトレーニングとデプロイを行います。

このシリーズのパート2と3では、データを分析および準備し、機械学習モデルをトレーニングするために、Azure Data Studio notebook でいくつかの Python スクリプトを開発します。 次に、第4部では、ストアドプロシージャを使用して、これらの Python スクリプトを SQL database 内で実行します。

*クラスタリング* は、グループのメンバーが何らかの方法で類似しているグループにデータの編成することとして説明できます。 このチュートリアルシリーズでは、小売事業を所有しているとします。 **K-Means** アルゴリズムを使用して、製品の購入と返品のデータセットで顧客のクラスタリングを実行します。 顧客をクラスタリングすることで、特定のグループをターゲットにし、マーケティングの取り組みをより効果的に進めることができます。
K-Means クラスタリングは、類似性に基づいてデータのパターンを検索する *教師なし学習* アルゴリズムです。

この記事では、次の方法について説明します。

> [!div class="checklist"]
> * サンプルデータベースを SQL Server インスタンスに復元する

[パート 2](python-clustering-model-prepare-data.md) では、クラスタリングを実行するために SQL データベースからデータを準備する方法について説明します。

[パート 3](python-clustering-model-build.md) では、Python で K-Means クラスターモデルを作成してトレーニングする方法について説明します。

[パート 4](python-clustering-model-deploy.md)では、新しいデータに基づいて Python でクラスタリングを実行できる SQL データベースにストアドプロシージャを作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

* Python 言語オプションを使用して[Machine Learning Services を SQL Server](../what-is-sql-server-machine-learning.md)には、 [Windows インストールガイド](../install/sql-machine-learning-services-windows-install.md)または[Linux インストールガイド](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-machine-learning?toc=%2fsql%2fadvanced-analytics%2ftoc.json&view=sql-server-linux-ver15)に記載されているインストール手順に従ってください。

* Python IDE-このチュートリアルでは、 [Azure Data Studio](../../azure-data-studio/what-is.md)の python notebook を使用します。 詳細については、「 [Azure Data Studio で notebook を使用する方法](../../azure-data-studio/sql-notebooks.md)」を参照してください。 Jupyter notebook や、 [python 拡張](https://marketplace.visualstudio.com/items?itemName=ms-python.python)機能と[mssql extension](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)を使用した[Visual Studio Code](https://code.visualstudio.com/docs)など、独自の python IDE を使用することもできます。

* [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) package- **revoscalepy**パッケージは SQL Server Machine Learning Services に含まれています。 クライアントコンピューターでパッケージを使用するには、「 [Python 開発用のデータサイエンスクライアントを設定](../python/setup-python-client-tools-sql.md)する」を参照して、このパッケージをローカルにインストールするオプションを選択してください。

  Azure Data Studio で Python notebook を使用している場合は、次の追加の手順に従って**revoscalepy**を使用します。

  1. Azure Data Studio を開く
  1. **[ファイル]** メニューの **[基本設定]** を選択し、 **[設定]** をクリックします。
  1. **拡張機能**を展開し、 **Notebook 構成**を選択します
  1. **[Python パス]** で、ライブラリをインストールしたパスを入力します`C:\path-to-python-for-mls`(たとえば、)。
  1. 既存の**Python を使用する**ことを確認する
  1. 再起動 Azure Data Studio

  別の Python IDE を使用している場合は、IDE の同様の手順に従います。

* SQL クエリツール-このチュートリアルでは、 [Azure Data Studio](../../azure-data-studio/what-is.md)を使用していることを前提としています。 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) を使用することもできます。

* 追加の Python パッケージ-このチュートリアルシリーズの例では、インストールされている可能性のある Python パッケージを使用します。 必要に応じて、次の**pip**コマンドを使用してこれらのパッケージをインストールします。

  ```console
  pip install matplotlib
  pip install scipy
  pip install sklearn
  ```

## <a name="restore-the-sample-database"></a>サンプルデータベースを復元する

このチュートリアルで使用されているサンプルデータセットは、ダウンロードして使用するための **.bak**データベースバックアップファイルに保存されています。 このデータセットは、[トランザクション処理パフォーマンス協議会 (TPC)](http://www.tpc.org/default.asp)によって提供される[tpcx-bb](http://www.tpc.org/tpcx-bb/default.asp)データセットから派生します。

1. [Tpcxbb_1gb](https://sqlchoice.blob.core.windows.net/sqlchoice/static/tpcxbb_1gb.bak)ファイルをダウンロードします。

1. 次の詳細を使用して、「Azure Data Studio で[バックアップファイルからデータベースを復元](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file)する」の手順に従います。

   * ダウンロードした tpcxbb_1gb ファイルからインポートし**ます。**
   * ターゲットデータベースに "tpcxbb_1gb" という名前を指定します。

1. データベースを復元した後、 **dbo. customer**テーブルに対してクエリを実行することで、データセットが存在することを確認できます。

    ```sql
    USE tpcxbb_1gb;
    SELECT * FROM [dbo].[customer];
    ```

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを続行しない場合は、SQL Server から tpcxbb_1gb データベースを削除してください。

## <a name="next-steps"></a>次の手順

このチュートリアルシリーズの第1部では、次の手順を完了しました。

* サンプルデータベースを SQL Server インスタンスに復元する

機械学習モデルのデータを準備するには、このチュートリアルシリーズのパート 2 に従います。

> [!div class="nextstepaction"]
> [チュートリアル: SQL Server Machine Learning Services を使用した Python でのクラスタリングを実行するためのデータを準備する](python-clustering-model-prepare-data.md)
