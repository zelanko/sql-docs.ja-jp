---
title: Azure Data Studio notebook を使用して SQL Server ビッグデータクラスターを管理する
titleSuffix: Manage SQL Server Big Data Clusters with Azure Data Studio notebooks
description: Azure Data Studio のノートブックを使用して、ビッグ データ クラスターの管理とトラブルシューティングを行います。
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e22b16cf8658e53e6bdc5db0fcd82692f3730fc7
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313677"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Azure Data Studio notebook を使用して SQL Server ビッグデータクラスターを管理する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] は、ノートブックを含む Azure Data Studio の拡張機能を提供します。 Notebook には、SQL Server 2019 ビッグデータクラスターを管理するために Azure Data Studio で使用できるドキュメントとコードが用意されています。

もともと、オープンソースプロジェクトとして実装されており、[ノートブック](notebooks-guidance.md)は[Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download)に組み込まれています。 テキスト セル内のテキストに対してはマークダウンを、また、コード セル内にコードを記述するには利用可能なカーネルの 1 つを使用できます。

ノートブックを使用して、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に対してビッグ データ クラスターを展開できます。

ノートブックに加えて、Jupyter ブックと呼ばれるノートブックのコレクションを表示することもできます。 Jupyter ブックには、ノートブックのコレクション内を移動するのに役立つ目次が用意されています。これにより、SQL Server のトラブルシューティングを行う場合でも、クラスターの状態を表示する場合でも、必要なノートブックを簡単に見つけることができます。

## <a name="prerequisites"></a>前提条件

Notebook を開くには、次の前提条件が必要です。

* [Azure Data Studio insider ビルド](https://aka.ms/azuredatastudio-rc)の最新バージョン
* にインストールされている @no__t 0 の拡張機能 Azure Data Studio

これらの前提条件に加えて、SQL Server 2019 のビッグデータクラスターをデプロイするには、次のものも必要です。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>トラブルシューティングノートブックにアクセスする
トラブルシューティングノートブックにアクセスするには、次の3つの方法があります。

### <a name="command-palette"></a>コマンド パレット
1. [**表示** > **コマンドパレット**] を選択します。
2. @No__t-0Jupyter ブックを入力します。SQL Server 2019 Guide @ no__t-0

Jupyter Books viewlet、SQL Server ビッグデータクラスターに関連するトラブルシューティングノートブックを含む Jupyter ブックを開きます。

### <a name="sql-master-dashboard"></a>SQL マスターダッシュボード
1. Azure Data Studio Insider をインストールした後、SQL Server ビッグデータクラスターインスタンスに接続します。
2. インスタンスに接続した後、 **[接続]** でサーバー名を右クリックし、 **[管理]** を選択します。
3. ダッシュボードで、 **[SQL Server ビッグデータクラスター]** を選択します。 **SQL Server 2019 ガイド**を選択して、必要なノートブックを含む Jupyter ブックを開きます。
    ダッシュボードの @no__t 0Jupyter notebook @ no__t-1

1. 完了する必要があるタスクの notebook を選択します。

### <a name="controller-dashboard"></a>コントローラーダッシュボード
1. **[接続]** ビューで、 **[ビッグデータクラスターの SQL Server]** を展開します。
2. コントローラーエンドポイントの詳細を追加します。
3. コントローラーに接続した後、エンドポイントを右クリックし、 **[管理]** を選択します。
4. ダッシュボードが読み込まれたら、 **[トラブルシューティング]** を選択して Jupyter Book のトラブルシューティングガイドを開きます。

## <a name="use-troubleshooting-notebooks"></a>トラブルシューティングノートブックの使用
1. Jupyter Book の目次で必要なトラブルシューティングガイドを見つけます。
1. ノートブックは最適化されているため、 **[セルの実行]** を選択するだけでかまいません。 この操作により、notebook が完成するまで、ノートブック内の各セルが個別に実行されます。
1. エラーが検出された場合、Jupyter ブックは、エラーを修正するために実行できる notebook を提案します。 推奨される手順に従って、もう一度 notebook を実行します。

## <a name="next-steps"></a>次の手順
Azure Data Studio のノードブックの詳細については、「[SQL Server 2019 Preview でノートブックを使用する方法](notebooks-guidance.md)」を参照してください。
