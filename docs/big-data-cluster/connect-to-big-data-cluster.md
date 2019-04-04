---
title: マスターに接続し、HDFS
titleSuffix: SQL Server big data clusters
description: SQL Server のマスター インスタンスと SQL Server 2019 ビッグ データ クラスター (プレビュー) の HDFS/Spark ゲートウェイに接続する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed563fe6d0bfd69ce5dfb7484d4213bc9a47dd54
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860173"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Azure Data Studio での SQL Server のビッグ データ クラスターに接続します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Azure Data Studio から SQL Server 2019 ビッグ データ クラスター (プレビュー) に接続する方法について説明します。 これには、ビッグ データ クラスターとの対話に使用される 2 つのメイン エンドポイントがあります。

| エンドポイント | 説明 |
|---|---|
| SQL Server マスター インスタンス | SQL Server のリレーショナル データベースを含むクラスターで SQL Server マスター インスタンス。 |
| HDFS/Spark ゲートウェイ | HDFS の記憶域クラスターで Spark ジョブを実行する機能へのアクセス。 |

> [!TIP]
> Azure Data Studio の 2019年 2 月リリースでは、SQL Server のマスター インスタンスへの接続を自動的に HDFS/Spark ゲートウェイへの UI アクセスを提供します。

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
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。

1. **接続の種類**、 **Microsoft SQL Server**します。

1. SQL Server のマスター インスタンスの IP アドレスを入力**サーバー名**(例。**\<IP アドレス\>31433、**)。

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

> [!IMPORTANT]
> 表示された場合**不明なエラー** UI では、する必要があります[HDFS/Spark ゲートウェイに直接接続](#hdfs)します。 このエラーの原因の 1 つは、SQL Server のマスター インスタンスおよび HDFS/Spark ゲートウェイの別のパスワードです。 Azure Data Studio では、両方に同じパスワードを使用することを前提としています。
  
## <a id="hdfs"></a> HDFS/Spark ゲートウェイへの接続します。

ほとんどの場合、SQL Server のマスター インスタンスへの接続にアクセスできる、HDFS と Spark の使用も、 **Data Services**ノード。 、への専用接続がまだ作成することができます、 **HDFS/Spark ゲートウェイ**必要な場合。 次の手順では、Azure Data Studio に接続する方法について説明します。

1. コマンドラインから次のコマンドのいずれかを使用して、HDFS/Spark gateway の IP アドレスを検索します。

   ```
   kubectl get svc endpoint-security -n <your-cluster-name>
   ```
 
1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。

1. **接続の種類**、**ビッグ データの SQL Server クラスター**します。

   > [!TIP]
   > 表示されない場合、**ビッグ データの SQL Server クラスター**接続入力をインストールしたかどうかを確認、[拡張機能の SQL Server 2019](../azure-data-studio/sql-server-2019-extension.md)と拡張機能の完了後に Azure Data Studio を再起動します。インストールします。

1. ビッグ データのクラスターの IP アドレスを入力**サーバー名**(ポートを指定しません)。

1. 入力`root`の**ユーザー**を指定し、**パスワード**ビッグ データ クラスターにします。

   ![HDFS/Spark ゲートウェイへの接続します。](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > ユーザー名は、既定では、**ルート**に対応するパスワードと、 **KNOX_PASSWORD**環境変数の展開時に使用します。

1. キーを押して**Connect**、および**Server ダッシュ ボード**が表示されます。

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスターに関する詳細については、[SQL Server 2019 ビッグ データ クラスターは](big-data-cluster-overview.md)を参照してください。