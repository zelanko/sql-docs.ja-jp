---
title: マスターに接続し、HDFS
titleSuffix: SQL Server 2019 big data clusters
description: SQL Server のマスター インスタンスと SQL Server 2019 ビッグ データ クラスター (プレビュー) の HDFS/Spark ゲートウェイに接続する方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 8bccadd8fbce9fe2a8cc6f16db75dbd09f3d1ed0
ms.sourcegitcommit: edf7372cb674179f03a330de5e674824a8b4118f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53264364"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Azure Data Studio での SQL Server のビッグ データ クラスターに接続します。

この記事では、Azure Data Studio から SQL Server 2019 ビッグ データ クラスター (プレビュー) に接続する方法について説明します。

## <a name="prerequisites"></a>前提条件

- 展開済み[SQL Server 2019 ビッグ データ クラスター](deployment-guidance.md)します。
- [SQL Server 2019 ビッグ データ ツール](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
   - **kubectl**

## <a name="connect-to-the-cluster"></a>クラスターに接続します。

ビッグ データ クラスターに接続するときに、SQL Server に接続するオプションがある[マスター インスタンス](concept-master-instance.md)または HDFS/Spark ゲートウェイ。 次のセクションでは、それぞれに接続する方法を示します。

## <a id="master"></a> マスター インスタンス

SQL Server のマスター インスタンスは、SQL Server のリレーショナル データベースを含む従来の SQL Server インスタンスです。 次の手順では、Azure Data Studio を使用して、マスター インスタンスに接続する方法について説明します。

1. コマンドラインでは、次のコマンドを使用して、マスター インスタンスの ip アドレスを見つけます。

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

## <a id="hdfs"></a> HDFS/Spark ゲートウェイ

**HDFS/Spark ゲートウェイ**HDFS の記憶域プールを使用するには、Spark ジョブを実行して接続することができます。 次の手順では、Azure Data Studio に接続する方法について説明します。

1. コマンドラインで、次のコマンドのいずれかの HDFS/Spark ゲートウェイの IP アドレスを検索します。
   
   **AKS のデプロイ:**

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```

   **非 AKS デプロイ**:

   ```
   kubectl get svc service-security-nodeport -n <your-cluster-name>
   ```
 
1. Azure Data Studio でキーを押して**F1** > **新しい接続**します。

1. **接続の種類**、**ビッグ データの SQL Server クラスター**します。

1. ビッグ データのクラスターの IP アドレスを入力**サーバー名**(ポートを指定しません)。

1. 入力`root`の**ユーザー**を指定し、**パスワード**ビッグ データ クラスターにします。

   ![HDFS/Spark ゲートウェイへの接続します。](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > ユーザー名は、既定では、**ルート**に対応するパスワードと、 **KNOX_PASSWORD**環境変数の展開時に使用します。

1. キーを押して**Connect**、および**Server ダッシュ ボード**が表示されます。

## <a name="next-steps"></a>次の手順

SQL Server 2019 ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターは](big-data-cluster-overview.md)します。