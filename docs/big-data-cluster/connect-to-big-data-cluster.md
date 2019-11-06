---
title: Master および HDFS ビッグデータクラスターへの接続
description: の SQL Server マスターインスタンスと HDFS/Spark ゲートウェイに接続する方法について説明[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: fb6e1f684a277740c06fbd0a2fdc23dbd77f8e5c
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652420"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Azure Data Studio を使用して SQL Server ビッグ データ クラスターに接続する

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Azure Data Studio からに接続する方法について説明します。

## <a name="prerequisites"></a>前提条件

- 展開済みの [SQL Server 2019 ビッグ データ クラスター](deployment-guidance.md)。
- [SQL Server 2019 ビッグ データ ツール](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **kubectl**

## <a id="master"></a> クラスターに接続する

Azure Data Studio を使用してビッグ データ クラスターに接続するには、クラスター内の SQL Server マスター インスタンスへの新しい接続を作成します。 以下の手順では、Azure Data Studio を使用してマスター インスタンスに接続する方法について説明します。

1. コマンド ラインから、次のコマンドを使用してマスター インスタンスの IP を調べます。

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > 展開構成ファイルで名前をカスタマイズしていない限り、ビッグ データ クラスター名は既定で **mssql-cluster** になります。 詳細については、「[ビッグ データ クラスターの展開設定を構成する](deployment-custom-configuration.md#clustername)」を参照してください。

1. Azure Data Studio で、**F1 キー** >  **[新しい接続]** から新しい接続を作成します。

1. **[接続の種類]** で **[Microsoft SQL Server]** を選択します。

1. **[サーバー名]** に SQL Server マスター インスタンスの IP アドレスを入力します (例: **\<IP アドレス\>,31433**)。

1. SQL ログインの **[ユーザー名]** と **[パスワード]** を入力します。

   > [!TIP]
   > 既定では、ユーザー名は **SA** であり、変更されていない限り、パスワードは展開時に使用される **MSSQL_SA_PASSWORD** 環境変数に対応します。

1. ターゲットの **[データベース名]** を、使用しているリレーショナル データベースのいずれかに変更します。

   ![マスター インスタンスに接続する](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. **[接続]** をクリックすると、**サーバー ダッシュボード**が表示されます。

Azure Data Studio の 2019 年 2 月リリースでは、SQL Server マスター インスタンスに接続することで、HDFS/Spark ゲートウェイを操作することもできます。 これは、次のセクションで説明する HDFS および Spark 用に別の接続を使用する必要がないことを意味します。

- オブジェクト エクスプローラーに、新しいノートブックの作成や Spark ジョブの送信などのビッグ データ クラスター タスクの右クリック サポートを備えた、新しい **[Data Services]** ノードが追加されました。 
- **[Data Services]** ノードには、HDFS 探索と、外部テーブルの作成や Notebook で分析などのアクションを実行するための **HDFS** フォルダーが含まれています。
- 接続の**サーバー ダッシュボード**には、拡張機能がインストールされている場合、**SQL Server ビッグ データ クラスター**と **SQL Server 2019 (プレビュー)** のタブも含まれています。

   ![Azure Data Studio の [Data Services] ノード](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>次の手順

の詳細[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]について[は[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ](big-data-cluster-overview.md)、「」を参照してください。