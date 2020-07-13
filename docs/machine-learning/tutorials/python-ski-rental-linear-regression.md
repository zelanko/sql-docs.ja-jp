---
title: Python のチュートリアル:スキー レンタル
titleSuffix: SQL machine learning
description: この 4 部構成のチュートリアル シリーズでは、SQL 機械学習でスキー レンタルを予測する線形回帰モデルを Python で構築します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b34687440763f2c514016989542ae3f2d7c0e6ed
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606917"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-with-sql-machine-learning"></a>Python のチュートリアル:SQL 機械学習での線形回帰を使用したスキー レンタルの予測
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
この 4 部構成のチュートリアル シリーズでは、[SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) または[ビッグ データ クラスター](../../big-data-cluster/machine-learning-services.md)で Python と線形回帰を使用して、スキーのレンタル数を予測します。 このチュートリアルは、[Azure Data Studio で Python のノートブック](../../azure-data-studio/sql-notebooks.md)を使用します。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
この 4 部構成のチュートリアル シリーズでは、[SQL Server Machine Learning Services](../sql-server-machine-learning-services.md) で Python と線形回帰を使用して、スキーのレンタル数を予測します。 このチュートリアルは、[Azure Data Studio で Python のノートブック](../../azure-data-studio/sql-notebooks.md)を使用します。
::: moniker-end

たとえば、スキー レンタル事業を所有していて、将来の日付に対するレンタル数を予測したい場合を考えてみましょう。 この情報は、在庫、スタッフおよび設備の準備に役立ちます。

このシリーズのパート 1 では、前提条件を設定します。 パート 2 と 3 では、ノートブックでいくつかの Python スクリプトを開発して、データを準備し、機械学習モデルをトレーニングします。 次にパート 3 では、T-SQL ストアド プロシージャを使用して、SQL Server 内でこれらの Python スクリプトを実行します。

この記事では、次の方法について学習します。

> [!div class="checklist"]
> * サンプル データベースを SQL Server にインポートする 

[パート 2](python-ski-rental-linear-regression-prepare-data.md) では、データベースから Python データ フレームにデータを読み込み、Python でデータを準備する方法を学習します。

[パート 3](python-ski-rental-linear-regression-train-model.md) では、Python で線形回帰モデルをトレーニングする方法について学習します。

[パート 4](python-ski-rental-linear-regression-deploy-model.md) では、モデルをデータベースに格納した後、パート 2 と 3 で開発した Python スクリプトからストアド プロシージャを作成する方法について学習します。 ストアド プロシージャは、新しいデータに基づいて予測を行うためにサーバーで実行されます。

## <a name="prerequisites"></a>前提条件

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* SQL Server Machine Learning Services - Machine Learning Services をインストールする方法については、「[Windows インストール ガイド](../install/sql-machine-learning-services-windows-install.md)」または「[Linux インストール ガイド](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json)」に関するページを参照してください。 [SQL Server ビッグ データ クラスターで Machine Learning Services を有効にする](../../big-data-cluster/machine-learning-services.md)こともできます。
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* SQL Server Machine Learning Services - Machine Learning Services をインストールする方法については、[Windows インストール ガイド](../install/sql-machine-learning-services-windows-install.md)に関するページを参照してください。 
::: moniker-end

* Python IDE - このチュートリアルは、[Azure Data Studio](../../azure-data-studio/what-is.md) で Python のノートブックを使用します。 詳細については、「[Azure Data Studio でノートブックを使用する方法](../../azure-data-studio/sql-notebooks.md)」を参照してください。

* SQL クエリ ツール - このチュートリアルでは、[Azure Data Studio](../../azure-data-studio/what-is.md) を使用していることを前提としています。

* 追加の Python パッケージ - このチュートリアル シリーズの例では、既定ではインストールされない可能性がある次の Python パッケージを使用します。

  * pandas
  * pyodbc
  * sklearn

  これらのパッケージをインストールするには:
  1. Azure Data Studio で、 **[パッケージの管理]** を選択します。
  2. **[パッケージの管理]** ペインで **[新規追加]** タブを選択します。
  3. 次の各パッケージについてパッケージ名を入力し、 **[検索]** をクリックし、 **[インストール]** をクリックします。

  また、 **[コマンド プロンプト]** を開き、Azure Data Studio で使用する Python のバージョンのインストール パス (たとえば `cd %LocalAppData%\Programs\Python\Python37-32`) に変更し、パッケージごとに `pip install` を実行する方法もあります。

## <a name="restore-the-sample-database"></a>サンプル データベースを復元する

このチュートリアルで使用するサンプル データベースは、ダウンロードして使用できるように **.bak** データベース バックアップ ファイルに保存されています。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> ビッグ データ クラスターで Machine Learning Services を使用している場合は、[SQL Server ビッグ データ クラスターのマスター インスタンスにデータベースを復元する](../../big-data-cluster/data-ingestion-restore-database.md)方法に関する記事を参照してください。
::: moniker-end

1. ファイル [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak) をダウンロードします。

1. Azure Data Studio で、以下の詳細情報を使用して、「[バックアップ ファイルからデータベースを復元する](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file)」に記載されている手順に従います。

   * ダウンロードした **TutorialDB.bak** ファイルからインポートします
   * ターゲット データベースに "TutorialDB" という名前を指定します

1. **dbo.rental_data** テーブルに対してクエリを実行して、復元されたデータベースが存在することを確認できます。

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

1. 次の SQL コマンドを実行して、外部スクリプトを有効にします。

    ```sql
    sp_configure 'external scripts enabled', 1;
    RECONFIGURE WITH override;
    ```

## <a name="next-steps"></a>次のステップ

このチュートリアル シリーズの第 1 部では、これらの手順を完了しました。

* 必須コンポーネントのインストール
* サンプル データベースを SQL Server にインポートする

TutorialDB データベースからデータを準備するには、このチュートリアル シリーズのパート 2 の手順を実行します。

> [!div class="nextstepaction"]
> [Python のチュートリアル:線形回帰モデルをトレーニングするためのデータを準備する](python-ski-rental-linear-regression-prepare-data.md)