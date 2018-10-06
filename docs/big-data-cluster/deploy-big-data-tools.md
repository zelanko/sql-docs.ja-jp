---
title: Azure Data Studio で SQL Server クラスターのビッグ データへの接続 |Microsoft Docs
description: Azure Data Studio での SQL Server 2019 ビッグ データ クラスターに接続する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 971fc2f8e8a77b00f3d2c5cd6390fec351ffc0f3
ms.sourcegitcommit: c7d3a903eb7f410db3a0230101d24de0af17621a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2018
ms.locfileid: "48827303"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Azure Data Studio での SQL Server のビッグ データ クラスターに接続します。

この記事では、Azure Data Studio、SQL Server 2019 拡張機能 (プレビュー) をインストールし、ビッグ データ クラスターに接続する方法について説明します。 新しい SQL Server 2019 拡張機能にはプレビュー サポートが含まれています[SQL Server 2019 ビッグ データ クラスター](big-data-cluster-overview.md)、統合された[ノートブック エクスペリエンス](notebooks-guidance.md)と、PolyBase [の外部テーブルの作成ウィザード](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-azure-data-studio"></a>Azure Data Studio をインストールします。

Azure Data Studio をインストールするを参照してください。[をダウンロードして Azure Data Studio の最新バージョンをインストール](../azure-data-studio/download.md)します。

## <a name="install-the-sql-server-2019-extension-preview"></a>SQL Server 2019 拡張機能 (プレビュー) のインストールします。

拡張機能をインストールするを参照してください。 [SQL Server 2019 拡張機能 (プレビュー) のインストール](../azure-data-studio/sql-server-2019-extension.md)します。

## <a name="connect-to-the-cluster"></a>クラスターに接続します。

ビッグ データ クラスターに接続するときに、SQL Server に接続するオプションがある[マスター インスタンス](concept-master-instance.md)または HDFS/Spark ゲートウェイ。 次のセクションでは、それぞれに接続する方法を示します。

## <a name="master-instance"></a>マスター インスタンス

1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。
1. **接続の種類**、 **Microsoft SQL Server**します。
1. SQL Server のマスター インスタンスの IP アドレスを入力**サーバー名**(例:  **\<IP アドレス\>31433、**)。
1. 変更、**データベース名**を**high_value_data**データベース。

   ![マスター インスタンスに接続します。](./media/deploy-big-data-tools/connect-to-cluster.png)

1. キーを押して**Connect**、および**Server ダッシュ ボード**が表示されます。

## <a name="hdfsspark-gateway"></a>HDFS/Spark ゲートウェイ

1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。
1. **接続の種類**、**ビッグ データの SQL Server クラスター**します。
1. ビッグ データのクラスターの IP アドレスを入力**サーバー名**します。

   ![HDFS/Spark ゲートウェイへの接続します。](./media/deploy-big-data-tools/connect-to-cluster-hdfs-spark.png)

1. キーを押して**Connect**、および**Server ダッシュ ボード**が表示されます。

## <a name="next-steps"></a>次の手順

Azure Data Studio でノートブックを実行するを参照してください。 [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。
