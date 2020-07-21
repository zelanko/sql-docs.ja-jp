---
title: Machine Learning 拡張機能を使用してモデルをインポートまたは表示する
titleSuffix: Azure Data Studio
description: Azure Data Studio の Machine Learning 拡張機能を使用して、ONNX モデルをインポートしたり、データベースに既にインポートされているモデルを表示したりする方法について説明します。
ms.date: 06/09/2020
ms.reviewer: sstein
ms.prod: azure-data-studio
ms.technology: machine-learning
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 62eb0a2c4eb4db7c86f4c5ff486a0088a20e8244
ms.sourcegitcommit: 48d60fe6b6991303a88936fb32322c005dfca2d8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2020
ms.locfileid: "85352409"
---
# <a name="import-or-view-models-with-machine-learning-extension-preview-for-azure-data-studio"></a>Azure Data Studio の Machine Learning 拡張機能 (プレビュー) を使用してモデルをインポートまたは表示する

[Azure Data Studio の Machine Learning 拡張機能](machine-learning-extension.md)を使用して、ONNX モデルをインポートしたり、データベースに既にインポートされているモデルを表示したりする方法について説明します。

> [!IMPORTANT]
> Machine Learning 拡張機能を使用したデータベースでのインポートと表示では、現在、[Azure SQL Managed Instance での Machine Learning Services](/azure/azure-sql/managed-instance/machine-learning-services-overview) と、[ONNX を使用した Azure SQL Edge](/azure/azure-sql-edge/onnx-overview) のみがサポートされています。

## <a name="prerequisites"></a>前提条件

- [Azure Data Studio の Machine Learning 拡張機能](machine-learning-extension.md)のインストールと構成。 [[拡張機能の設定] で Python インストール パス](machine-learning-extension.md#settings)を指定する必要があります。

- **onnxruntime**、**mlflow**、および **mlflow-dbstore** の各 Python パッケージ。 パッケージがまだインストールされていない場合は、Machine Learning 拡張機能によってインストールするように求められます。

## <a name="view-models"></a>モデルの表示

次の手順に従って、データベースに格納されている ONNX モデルを表示します。

1. **[モデルのインポートまたは表示]** をクリックします。

1. **onnxruntime**、**mlflow**、**mlflow-dbstore** をインストールするように求められた場合は、 **[はい]** をクリックします。

1. モデルが格納されている**モデル データベース**と**モデル テーブル**を選択します。

これにより、モデルのリストが表示されます。 モデルの名前と説明を編集することも、リストからモデルを削除することもできます。

## <a name="import-a-new-model"></a>新しいモデルのインポート

次の手順に従って、データベースに ONNX モデルをインポートします。

1. **[モデルのインポートまたは表示]** をクリックします。

1. **onnxruntime**、**mlflow**、**mlflow-dbstore** をインストールするように求められた場合は、 **[はい]** をクリックします。

1. **[モデルのインポート]** をクリックします。

1. インポートされたモデルを格納する**モデル データベース**を選択します。

1. インポートされたモデルを格納する**モデル テーブル**を選択します。 **既存のテーブル**を選択するか、**新しいテーブル**を作成することができます。 **[次へ]** をクリックします。

1. モデルが配置されている場所を選択し、 **[次へ]** をクリックします。 使用できるもの:
    - **ファイルのアップロード**。 ファイルからモデルを使用する場合は、これを選択します。 **[ソース ファイル]** でモデル ファイルを選択し、 **[次へ]** をクリックします。
    - **Azure Machine Learning**。 Azure Machine Learning のモデルを使用するには、これを選択します。 最初に、**Azure にサインイン**します。 次に、ご自分の **Azure アカウント**、**Azure サブスクリプション**、**Azure リソース グループ**、**Azure ML ワークスペース**を選択します。 使用するモデルを選択し、 **[次へ]** をクリックします。

1. モデルの **[名前]** と **[説明]** を入力し、 **[デプロイ]** をクリックして、モデルをデータベースに格納します。

> [!NOTE]
> Machine Learning 拡張機能は現在プレビューの段階です。 そのため、モデルが格納されているテーブル スキーマは将来変更される可能性があります。

## <a name="next-steps"></a>次のステップ

- [Azure Data Studio の Machine Learning 拡張機能](machine-learning-extension.md)
- [データベースでのパッケージの管理](machine-learning-extension-manage-packages.md)
- [予測を行う](machine-learning-extension-predictions.md)
- [モデルのインポートと表示](machine-learning-extension-import-view-models.md)
- [SQL の機械学習のドキュメント](../machine-learning/index.yml)
- [Azure SQL Managed Instance の Machine Learning Services](/azure/azure-sql/managed-instance/machine-learning-services-overview)
- [SQL Edge (プレビュー) での ONNX を使用した機械学習と AI](/azure/azure-sql-edge/onnx-overview)
