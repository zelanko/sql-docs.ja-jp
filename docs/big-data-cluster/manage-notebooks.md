---
title: Azure Data Studio ノートブックを使用して SQL Server ビッグ データ クラスターを管理する
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Azure Data Studio のノートブックを使用して、ビッグ データ クラスターの管理とトラブルシューティングを行います。
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cb2fcaf7431b5d79698af009b533ee49254777fe
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846651"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Azure Data Studio ノートブックを使用して SQL Server のビッグ データ クラスターを管理する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] は、ノートブックを含む Azure Data Studio の拡張機能を提供します。 ノートブックには、SQL Server のビッグ データ クラスターを管理するために Azure Data Studio で使用できるドキュメントとコードが含まれています。

[ノートブック](notebooks-guidance.md)は、もともとはオープン ソース プロジェクトとして実装され、[Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download) に実装されていました。 テキスト セル内のテキストに対してはマークダウンを、また、コード セル内にコードを記述するには利用可能なカーネルの 1 つを使用できます。

ノートブックを使用して、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に対してビッグ データ クラスターを展開できます。

Notebook に加えて、ユーザーは、Jupyter Books と呼ばれるノートブックのコレクションを表示できます。 Jupyter Book には、ノートブックのコレクション内を移動できる目次が用意されています。これにより、ユーザーは必要なノートブックを見つけたり、SQL Server のトラブルシューティングを行ったり、クラスターの状態を表示したりすることができます。

## <a name="prerequisites"></a>前提条件

ノートブックを起動できるようにするには、次の前提条件が要件となります。

* [Azure Data Studio Insiders ビルド](https://aka.ms/azuredatastudio-rc)の最新バージョン
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 拡張機能が Azure Data Studio にインストールされている

上記に加えて、SQL Server 2019 ビッグ データ クラスターを展開するには、以下も必要になります。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>ノートブックのトラブルシューティングへのアクセス
トラブルシューティングノートブックにアクセスするには、次の3つの方法があります。

### <a name="command-palette"></a>コマンド パレット
1. **[表示]** 、 **[コマンドパレット]** の順にクリック
2. 「Jupyter Books:SQL Server 2019 ガイド」を参照してください。
3. Jupyter Books Viewlet が開き、SQL Server ビッグデータクラスターに関連する TSG を含む Jupyter ブックが表示されます。

### <a name="sql-master-dashboard"></a>SQL マスターダッシュボード
1. Azure Data Studio Insider をインストールした後、SQL Server ビッグ データ クラスター インスタンスに接続します。
2. 接続が正常に完了したら、[Connections]\(接続\) ビューレットでサーバー名を右クリックし、 **[Manage]\(管理\)** をクリックします。
3. ダッシュボードで、 **[SQL Server Big Data Cluster]\(SQL Server ビッグ データ クラスター\)** をクリックします。 **[SQL Server 2019 guide]\(SQL Server 2019 ガイド\)** をクリックして、必要なノートブックを含む Jupyter Book を開きます。
    ![ボタン](media/manage-notebooks/jupyter-book-button.png)

1. これにより、TSG Jupyter ブックが既に開いている Jupyter Books viewlet が開きます。
4. 完了する必要があるタスクのノートブックをクリックします。

### <a name="controller-dashboard"></a>コントローラーダッシュボード
1. **[接続]** ビューで、 **[ビッグデータクラスターの SQL Server]** を展開します。
2. コントローラーエンドポイントの詳細を追加します。
3. コントローラーへの接続が正常に完了したら、エンドポイントを右クリックし、[管理] をクリックし**ます。**
4. ダッシュボードが読み込まれたら、[トラブルシューティング] をクリックして Jupyter Book TSG を起動します。

## <a name="how-to-use-troubleshooting-notebooks"></a>トラブルシューティングノートブックの使用方法
1. 必要な TSG が見つかるまで、既存の Jupyter Book の目次を参照してください。
1. すべてのノートブックは、ユーザーのみが実行セルをクリックする必要があるように最適化されてい**ます。** これにより、ノートブック内の各セルは、完了するまで個別に実行されます。
1. エラーが発生した場合は、Jupyter ブックで、エラーを修正するために実行できる notebook が提案されます。 手順に従って、notebook を再実行します。

## <a name="next-steps"></a>次の手順
Azure Data Studio のノードブックの詳細については、「[SQL Server 2019 プレビューでノートブックを使用する方法](notebooks-guidance.md)」を参照してください。
