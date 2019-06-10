---
title: マスターに接続し、HDFS
titleSuffix: SQL Server big data clusters
description: SQL Server のマスター インスタンスと SQL Server 2019 ビッグ データ クラスター (プレビュー) の HDFS/Spark ゲートウェイに接続する方法について説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 245e88034194a01908b69d545deb9fa717c19a4a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782983"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Azure Data Studio での SQL Server のビッグ データ クラスターに接続します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Azure Data Studio から SQL Server 2019 ビッグ データ クラスター (プレビュー) に接続する方法について説明します。

## <a name="prerequisites"></a>前提条件

- 展開済み[SQL Server 2019 ビッグ データ クラスター](deployment-guidance.md)します。
- [SQL Server 2019 ビッグ データ ツール](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **kubectl**

## <a id="master"></a> クラスターに接続します。

Azure データ Studio を使用したビッグ データ クラスターに接続するには、クラスターで SQL Server のマスター インスタンスに新しい接続を行います。 次の手順では、Azure Data Studio を使用して、マスター インスタンスに接続する方法について説明します。

1. コマンドラインから次のコマンドを使用して、マスター インスタンスの ip アドレスを見つけます。

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > ビッグ データ クラスター名の既定値に**mssql クラスター**展開構成ファイル内の名前をカスタマイズしていない限り、します。 詳細については、次を参照してください。[ビッグ データ クラスターのデプロイ設定を構成する](deployment-custom-configuration.md#clustername)します。

1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。

1. **接続の種類**、 **Microsoft SQL Server**します。

1. SQL Server のマスター インスタンスの IP アドレスを入力**サーバー名**(例。 **\<IP アドレス\>31433、** )。

1. SQL ログインを入力**ユーザー名**と**パスワード**します。

   > [!TIP]
   > ユーザー名は、既定では、 **SA**と、変更されない限り、パスワードに対応する、 **MSSQL_SA_PASSWORD**環境変数の展開時に使用します。

1. ターゲットを変更**データベース名**リレーショナル データベースのいずれかにします。

   ![マスター インスタンスに接続します。](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. キーを押して**Connect**、および**Server ダッシュ ボード**が表示されます。

Azure Data Studio の 2019年 2 月リリースでは、SQL Server のマスター インスタンスに接続することもできます HDFS/Spark ゲートウェイとやり取りします。 つまり、HDFS と、次のセクションで説明する Spark の個別の接続を使用する必要はありません。

- オブジェクト エクスプ ローラーを今すぐ新しい含む**Data Services**ノードを右クリックして新しいノートブックを作成または spark ジョブの送信などのビッグ データ クラスター タスク サポートします。 
- **Data Services**ノードも含まれています、 **HDFS**の HDFS の探索と Notebook で外部テーブルの作成や分析などのアクションを実行するフォルダー。
- **Server ダッシュ ボード**に、接続は、タブも含まれています。 **SQL Server のビッグ データ クラスター**と**SQL Server 2019 (プレビュー)** 、拡張機能がインストールされている場合。

   ![Azure Data Studio データ サービス ノード](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターは](big-data-cluster-overview.md)します。