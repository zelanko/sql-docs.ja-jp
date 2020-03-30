---
title: Python のチュートリアル:スキー レンタル
description: この 4 部構成のチュートリアル シリーズのパート 3 では、SQL Server Machine Learning Services でスキー レンタルを予測する線形回帰モデルを Python で構築します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/02/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe8a0c9af06d39ce183677adb86f30d9fc197d67
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75681750"
---
# <a name="python-tutorial-predict-ski-rental-with-linear-regression-in-sql-server-machine-learning-services"></a>Python のチュートリアル:SQL Server Machine Learning Services での線形回帰を使用したスキー レンタルの予測
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この 4 部構成のチュートリアル シリーズでは、[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) で Python と線形回帰を使用して、スキーのレンタル数を予測します。 このチュートリアルでは [Azure Data Studio で Python notebook](../../azure-data-studio/sql-notebooks.md) を使用しますが、独自の Python 統合開発環境 (IDE) を使用することもできます。

たとえば、スキー レンタル事業を所有していて、将来の日付に対するレンタル数を予測したい場合を考えてみましょう。 この情報は、在庫、スタッフおよび設備の準備に役立ちます。

このシリーズのパート 1 では、前提条件を設定します。 パート 2 と 3 では、Jupyter notebook でいくつかの Python スクリプトを開発して、データを準備し、機械学習モデルをトレーニングします。 次にパート 3 では、T-SQL ストアド プロシージャを使用して、SQL Server 内でこれらの Python スクリプトを実行します。

この記事では、次の方法について学習します。

> [!div class="checklist"]
> * サンプル データベースを SQL Server にインポートする 

[パート 2](python-ski-rental-linear-regression-prepare-data.md) では、SQL Server から Python データ フレームにデータを読み込み、Python でデータを準備する方法を学習します。

[パート 3](python-ski-rental-linear-regression-train-model.md) では、Python で線形回帰モデルをトレーニングする方法について学習します。

[第 4 部](python-ski-rental-linear-regression-deploy-model.md)では、モデルを SQL Server に格納し、そして第 2 部と第 3 部で開発した Python スクリプトからストアド プロシージャを作成する方法について学習します。 ストアド プロシージャは、新しいデータに基づいて予測を行うために SQL Server で実行されます。

## <a name="prerequisites"></a>前提条件

* SQL Server Machine Learning Services - Machine Learning Services をインストールする方法については、「[Windows インストール ガイド](../install/sql-machine-learning-services-windows-install.md)」または「[Linux インストール ガイド](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fadvanced-analytics%2Ftoc.json)」に関するページを参照してください。

* Python IDE - このチュートリアルは、[Azure Data Studio](../../azure-data-studio/what-is.md) で Python のノートブックを使用します。 詳細については、「[Azure Data Studio でノートブックを使用する方法](../../azure-data-studio/sql-notebooks.md)」を参照してください。 

    Jupyter notebook や [Visual Studio Code](https://code.visualstudio.com/docs) などの独自の Python IDE を使用することもできます。これには [Python 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-python.python) と [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)を使用します。 

* SQL クエリ ツール - このチュートリアルでは、[Azure Data Studio](../../azure-data-studio/what-is.md) を使用していることを前提としています。 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md) (SSMS) を使用することもできます。

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

1. ファイル [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak) をダウンロードします。

1. Azure Data Studio で、以下の詳細情報を使用して、「[バックアップ ファイルからデータベースを復元する](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file)」に記載されている手順に従います。

   * ダウンロードした **TutorialDB.bak** ファイルからインポートします
   * ターゲット データベースに "TutorialDB" という名前を指定します

1. **dbo.rental_data** テーブルに対してクエリを実行して、復元されたデータベースが存在することを確認できます。

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```

次の SQL コマンドを実行して、外部スクリプトを有効にします。

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