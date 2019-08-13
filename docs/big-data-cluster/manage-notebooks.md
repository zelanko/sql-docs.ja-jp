---
title: Azure Data Studio ノートブックを使用して SQL Server ビッグ データ クラスターを管理する
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Azure Data Studio のノートブックを使用して、ビッグ データ クラスターの管理とトラブルシューティングを行います。
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9c8edd91ced01135d740fecdf6cf837df9cac6b
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470735"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Azure Data Studio ノートブックを使用して SQL Server のビッグ データ クラスターを管理する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] は、ノートブックを含む Azure Data Studio の拡張機能を提供します。 ノートブックには、SQL Server のビッグ データ クラスターを管理するために Azure Data Studio で使用できるドキュメントとコードが含まれています。

[ノートブック](notebooks-guidance.md)は、もともとはオープン ソース プロジェクトとして実装され、[Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download) に実装されていました。 テキスト セルのテキストにマークダウンを使用し、使用できるカーネルのいずれかを使用してコード セル内にコードを記述できます。

ノートブックを使用して、[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] に対してビッグ データ クラスターを展開できます。

ノートブックに加え、ユーザーは Jupyter Book と呼ばれるノートブックのコレクションを表示できます。 Jupyter Book には、ノートブックのコレクション内を移動できる目次が用意されています。これにより、ユーザーは必要なノートブックを見つけたり、SQL Server のトラブルシューティングを行ったり、クラスターの状態を表示したりすることができます。

## <a name="prerequisites"></a>Prerequisites

ノートブックを起動できるようにするには、次の前提条件が要件となります。

* [Azure Data Studio Insiders ビルド](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)の最新バージョン
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] 拡張機能が Azure Data Studio にインストールされている

上記に加えて、SQL Server 2019 ビッグ データ クラスターを展開するには、以下も必要になります。

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>ノートブックのトラブルシューティングへのアクセス

1. Azure Data Studio Insider をインストールした後、SQL Server ビッグ データ クラスター インスタンスに接続します。
2. 接続が正常に完了したら、[Connections]\(接続\) ビューレットでサーバー名を右クリックし、 **[Manage]\(管理\)** をクリックします。
3. ダッシュボードで、 **[SQL Server Big Data Cluster]\(SQL Server ビッグ データ クラスター\)** をクリックします。 **[SQL Server 2019 guide]\(SQL Server 2019 ガイド\)** をクリックして、必要なノートブックを含む Jupyter Book を開きます。
    ![ボタン](media/manage-notebooks/jupyter-book-button.png)

1. フォルダーの選択ウィンドウで、Jupyter Book を保存する場所を選択します。
2. **[Reload]\(再読み込み\)** をクリックして Azure Data Studio を再度読み込み、Jupyter Book を表示します。 **[Open new instance]\(新しいインスタンスを開く\)** をクリックして、Jupyter Book を含む Azure Data Studio の新しいインスタンスを開きます。
3. [Explorer]\(エクスプローラー\) ビューに、"**Books**" というセクションが表示されます。 展開されていない場合は、クリックしてノートブックを表示します。
4. 完了する必要があるタスクのノートブックをクリックします。

## <a name="next-steps"></a>Next Steps
Azure Data Studio のノードブックの詳細については、「[SQL Server 2019 プレビューでノートブックを使用する方法](notebooks-guidance.md)」を参照してください。