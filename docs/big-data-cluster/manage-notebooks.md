---
title: Azure Data Studio notebook を使用して SQL Server ビッグデータクラスターを管理する
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Azure Data Studio のノートブックを使用して、ビッグデータクラスターの管理とトラブルシューティングを行います。
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8d87b09878539cccd40191d870bf97487579dca2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426402"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Azure Data Studio notebook を使用した SQL Server 用のビッグデータクラスターの管理

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]配置ノートブックを含む Azure Data Studio の拡張機能を提供します。 デプロイノートブックには、SQL Server 用のビッグデータクラスターを管理するために Azure Data Studio で使用できるドキュメントとコードが含まれています。

もともと、オープンソースプロジェクトとして実装されており、[ノートブック](notebooks-guidance.md)は[Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)に実装されています。 テキストセル内のテキストに markdown を使用し、使用可能なカーネルの1つを使用してコードセルにコードを記述することができます。

Notebook を使用して、の[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]ビッグデータクラスターを展開できます。

## <a name="prerequisites"></a>必須コンポーネント

Notebook を起動するには、次の前提条件が必要です。

* [Azure Data Studio insider ビルド](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)の最新バージョン
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]Azure Data Studio にインストールされた拡張機能

上記に加えて、SQL Server 2019 ビッグデータクラスターを展開するには、次のものも必要です。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)
