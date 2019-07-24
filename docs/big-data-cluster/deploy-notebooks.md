---
title: Azure Data Studio notebook を使用して SQL Server ビッグデータクラスターをデプロイする
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Azure Data Studio の notebook を使用して、ビッグデータクラスターをデプロイします。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f12a4f06ceb1c3a48b2b2fc661c59594e6d6cce3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426422"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Azure Data Studio notebook を使用して SQL Server ビッグデータクラスターをデプロイする

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]配置ノートブックを含む Azure Data Studio の拡張機能を提供します。 デプロイノートブックには、SQL Server ビッグデータクラスターを作成するために Azure Data Studio で使用できるドキュメントとコードが含まれています。 

もともと、オープンソースプロジェクトとして実装されており、[ノートブック](notebooks-guidance.md)は[Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)に実装されています。 テキストセル内のテキストに markdown を使用し、使用可能なカーネルの1つを使用してコードセルにコードを記述することができます。

Notebook を使用して、の[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]ビッグデータクラスターを展開できます。

## <a name="prerequisites"></a>必須コンポーネント
Notebook を起動するには、次の前提条件が必要です。

* [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)インストールされている最新バージョン
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]Azure Data Studio にインストールされた拡張機能

上記に加えて、SQL Server 2019 ビッグデータクラスターを展開するには、次のものも必要です。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Notebook を起動する

1. [Azure Data Studio insider ビルド](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)をインストールして起動します。
1.  **[接続]** タブで **[...]** をクリックし、 **[SQL Server ビッグデータクラスターのデプロイ]** を選択します。

   ![AI と ML](media/deploy-notebooks/deploy-notebooks-1.png)

1. **デプロイターゲット**の **[オプション]** で、 **[新しい azure Kubernetes クラスター]** または **[既存の azure Kubernetes Service クラスター]** を選択します。
1. **[Notebook を開く]** を選択します。

この操作により、適切な notebook が起動します。 デプロイを完了するには、notebook の指示に従って、既存または新規[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]の Azure Kubernetes サービスクラスターに用のビッグデータクラスターをデプロイします。
