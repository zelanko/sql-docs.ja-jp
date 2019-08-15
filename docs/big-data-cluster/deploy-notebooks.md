---
title: Azure Data Studio ノートブックを使用して SQL Server ビッグ データ クラスターを展開する
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Azure Data Studio からノートブックを使用して、ビッグ データ クラスターを展開します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d68baa615f384dd5afb665f29decb6d72113c5a3
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028567"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Azure Data Studio ノートブックを使用して SQL Server ビッグ データ クラスターを展開する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] では、展開ノートブックを含む Azure Data Studio の拡張機能が提供されています。 展開ノートブックには、SQL Server ビッグ データ クラスターを作成するために Azure Data Studio 内で使用できるドキュメントとコードが含まれています。

もともとは、オープン ソース プロジェクトとして実装され、[ノートブック](notebooks-guidance.md)は [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download) 内に実装されていました。 テキスト セル内のテキストに対してはマークダウンを、また、コード セル内にコードを記述するには利用可能なカーネルの 1 つを使用できます。

ノートブックを使用して、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に対してビッグ データ クラスターを展開できます。

## <a name="prerequisites"></a>必須コンポーネント

ノートブックを起動できるようにするには、次の前提条件が要件となります。

* [Azure Data Studio insider ビルド](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)がインストールされている最新バージョン
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 拡張機能が Azure Data Studio にインストールされている

上記に加えて、SQL Server 2019 ビッグ データ クラスターを展開するには、以下も必要になります。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>ノートブックを起動する

1. Azure Data Studio Insider を起動します。

1. **[接続]** タブ上で、 **[...]** をクリックして、 **[Deploy SQL Server big data cluster...]\(SQL Server ビッグ データ クラスターを展開する\)** を選択します。

   ![AI と ML](media/deploy-notebooks/deploy-notebooks-1.png)

1. **[オプション]** 下にある **[展開ターゲット]** から、 **[New Azure Kubernetes Cluster]\(新しい Azure Kubernetes クラスター\)** または **[Existing Azure Kubernetes Service cluster]\(既存の Azure Kubernetes Service クラスター\)** のどちらかを選択します。

1. **[選択]** ボタンをクリックします。

1. この操作では、ユーザー入力を収集するダイアログを起動し、必要な情報を入力して、既定値を確認します。

1. **[Notebook を開く]** ボタンをクリックします。
この操作により、適切なノートブックが起動されます。 展開を完了するには、ノートブックでの指示に従って、既存または新しい Azure Kubernetes Service クラスター上に [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に対するビッグ データ クラスターを展開します。

## <a name="next-steps"></a>次の手順

展開の詳細については、[SQL Server ビッグ データ クラスターの展開ガイダンス](deployment-guidance.md)に関するページを参照してください。
