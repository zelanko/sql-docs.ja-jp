---
title: Machine Learning 拡張機能 (プレビュー)
titleSuffix: Azure Data Studio
description: Azure Data Studio の Machine Learning 拡張機能を使用すると、パッケージの管理、機械学習モデルのインポート、予測の作成、および SQL データベースの実験を実行するためのノートブックの作成を行うことができます。
ms.date: 05/19/2020
ms.reviewer: sstein
ms.prod: azure-data-studio
ms.technology: machine-learning
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e6b38724e2cb8fde7fe38a544c3f87fba3cebd45
ms.sourcegitcommit: 48d60fe6b6991303a88936fb32322c005dfca2d8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2020
ms.locfileid: "85352419"
---
# <a name="machine-learning-extension-preview-for-azure-data-studio"></a>Azure Data Studio の Machine Learning 拡張機能 (プレビュー)

[Azure Data Studio](what-is.md) の Machine Learning 拡張機能を使用すると、パッケージの管理、機械学習モデルのインポート、予測の作成、および SQL データベースの実験を実行するためのノートブックの作成を行うことができます。 この拡張機能は、現在プレビューの段階にあります。

## <a name="prerequisites"></a>前提条件

Azure Data Studio を実行するコンピューターには、次の前提条件をインストールする必要があります。

- [Python 3](https://www.python.org/downloads/)。 Python をインストールしたら、[[拡張機能の設定]](#settings) で、Python インストールへのローカル パスを指定する必要があります。 Azure Data Studio で [Python カーネル ノートブック](notebooks-tutorial-python-kernel.md)を使用したことがある場合は、拡張機能ではノートブックからのパスが既定で使用されます。

- Windows、macOS、または Linux 用の [Microsoft ODBC driver 17 for SQL Server](../connect/odbc/download-odbc-driver-for-sql-server.md)。

- [R 3.5](https://www.r-project.org/) (省略可能)。 3\.5 以外のバージョンは現在サポートされていません。 R 3.5 をインストールしたら、R を有効にし、[[拡張機能の設定]](#settings) で、R インストールへのローカル パスを指定する必要があります。 これは、データベースで R パッケージを管理する場合にのみ必要です。

## <a name="install-the-extension"></a>拡張機能をインストールする

Azure Data Studio に Machine Learning 拡張機能をインストールするには、次の手順に従います。

1. Azure Data Studio で拡張機能マネージャーを開きます。 拡張機能アイコンを選択するか、[表示] メニューの [拡張機能] を選択できます。

1. **Machine Learning** 拡張機能を選択し、その詳細を表示します。

1. **[インストール]** をクリックします。

1. **[再度読み込む]** をクリックして拡張機能を有効にします。 これは、拡張機能を初めてインストールするときにのみ必要です。

<a name="settings"></a>

## <a name="extension-settings"></a>拡張機能の設定

Machine Learning 拡張機能の設定を変更するには、次の手順に従います。

1. Azure Data Studio で拡張機能マネージャーを開きます。 拡張機能アイコンを選択するか、[表示] メニューの [拡張機能] を選択できます。

1. **有効化された**拡張機能の下で、**Machine Learning** 拡張機能を見つけます。

1. **[管理]** アイコンをクリックします。

1. **[拡張機能の設定]** アイコンをクリックします。

拡張機能の設定は次のようになります。

:::image type="content" source="media/machine-learning-extension/ml-extension-settings.png" alt-text="Machine Learning 拡張機能の設定":::

### <a name="enable-python"></a>Python の有効化

データベースで Machine Learning 拡張機能と Python パッケージ管理を使用するには、次の手順に従います。

> [!IMPORTANT]
> Machine Learning 拡張機能では、データベース機能で Python パッケージ管理を使用しない場合でも、Python を有効にし、ほとんどの機能が動作するように構成する必要があります。

1. **[Machine Learning: Python の有効化]** が有効になっていることを確認します。 既定では、この設定は有効になっています。

1. 既存の Python インストールへのパスを **[Machine Learning: Python パス]** で指定します。 これには Python の実行可能ファイルまたは実行可能ファイルが格納されているフォルダーへの完全なパスを指定できます。 Azure Data Studio で [Python カーネル ノートブック](notebooks-tutorial-python-kernel.md)を使用したことがある場合は、拡張機能ではノートブックからのパスが既定で使用されます。

### <a name="enable-r"></a>R の有効化

データベースの R パッケージ管理に Machine Learning 拡張機能を使用するには、次の手順に従います。

1. **[Machine Learning: R の有効化]** が有効になっていることを確認します。 既定では、この設定は無効になっています。

1. 既存の R インストールへのパスを **[Machine Learning: R パス]** で指定します。 これは、R 実行可能ファイルへの完全なパスである必要があります。 

## <a name="use-the-machine-learning-extension"></a>Machine Learning 拡張機能を使用する

Azure Data Studio で Machine Learning 拡張機能を使用するには、次の手順に従います。

1. Azure Data Studio で接続を開きます。

1. ご使用のサーバーを右クリックし、 **[管理]** を選択します。

1. 左側のメニューの **[全般]** の下で **[Machine Learning]** をクリックします。

Machine Learning 拡張機能を使用して、パッケージを管理し、予測を行い、データベースにモデルをインポートする方法については、**次のステップ**の下のリンクを参照してください。

## <a name="next-steps"></a>次のステップ

- [データベースでのパッケージの管理](machine-learning-extension-manage-packages.md)
- [予測を行う](machine-learning-extension-predictions.md)
- [モデルのインポートまたは表示](machine-learning-extension-import-view-models.md)
- [Azure Data Studio のノートブック](notebooks-guidance.md)
- [SQL の機械学習のドキュメント](../machine-learning/index.yml)
- [SQL Edge (プレビュー) での ONNX を使用した機械学習と AI](/azure/azure-sql-edge/onnx-overview)
