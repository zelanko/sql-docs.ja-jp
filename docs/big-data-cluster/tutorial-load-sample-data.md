---
title: サンプル データを読み込む
titleSuffix: SQL Server big data clusters
description: このチュートリアルでは、SQL Server ビッグデータクラスターにサンプルデータを読み込む方法について説明します。 サンプルデータには、SQL Server master インスタンスのリレーショナルデータが含まれています。 また、記憶域プール内の HDFS データも含まれます。 このデータは、このセクションの他のチュートリアルをサポートしています。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b35eccece4df47cb483932386cf6a38e45d2dc8
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419278"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>チュートリアル:SQL Server ビッグデータクラスターへのサンプルデータの読み込み

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、サンプルデータを SQL Server 2019 ビッグデータクラスター (プレビュー) に読み込むスクリプトを使用する方法について説明します。 ドキュメントに記載されている他のチュートリアルの多くは、このサンプルデータを使用します。

> [!TIP]
> SQL Server 2019 ビッグデータクラスター (プレビュー) のその他のサンプルについては、 [SQL Server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster)GitHub リポジトリを参照してください。 これらは、「 **sql server-samples/samples/features/sql-ビッグデータ-クラスター/** パス」にあります。

## <a name="prerequisites"></a>必須コンポーネント

- [デプロイされたビッグデータクラスター](deployment-guidance.md)
- [ビッグデータツール](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a>サンプルデータの読み込み

次の手順では、ブートストラップスクリプトを使用して SQL Server データベースのバックアップをダウンロードし、ビッグデータクラスターにデータを読み込みます。 使いやすくするために、これらの手順は[Windows](#windows)および[Linux](#linux)のセクションに分けられています。

## <a id="windows"></a>ウィンドウ

次の手順では、Windows クライアントを使用して、ビッグデータクラスターにサンプルデータを読み込む方法について説明します。

1. 新しい Windows コマンドプロンプトを開きます。

   > [!IMPORTANT]
   > これらの手順には、Windows PowerShell を使用しないでください。 Powershell では、スクリプトは、PowerShell バージョンの**curl**を使用するので失敗します。

1. **Curl**を使用して、サンプルデータのブートストラップスクリプトをダウンロードします。

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. **Bootstrap-sample-db**スクリプトをダウンロードします。 このスクリプトはブートストラップスクリプトによって呼び出されます。

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートストラップスクリプトでは、ビッグデータクラスターに次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | < CLUSTER_NAMESPACE > | ビッグデータクラスターに付けた名前。 |
   | <SQL_MASTER_IP> | Master インスタンスの IP アドレス。 |
   | <SQL_MASTER_SA_PASSWORD> | Master インスタンスの SA パスワード。 |
   | <KNOX_IP> | HDFS/Spark ゲートウェイの IP アドレス。 |
   | <KNOX_PASSWORD> | HDFS/Spark ゲートウェイのパスワード。 |

   > [!TIP]
   > [Kubectl](cluster-troubleshooting-commands.md)を使用して、SQL Server マスターインスタンスと KNOX の IP アドレスを検索します。 を`kubectl get svc -n <your-big-data-cluster-name>`実行して、マスターインスタンスの外部 IP アドレス (**マスター svc-外部**) と Knox (**ゲートウェイ-svc**) を確認します。 クラスターの既定の名前は**mssql-cluster**です。

1. ブートストラップスクリプトを実行します。

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a>マシン

次の手順では、Linux クライアントを使用して、ビッグデータクラスターにサンプルデータを読み込む方法について説明します。

1. ブートストラップスクリプトをダウンロードし、実行可能なアクセス許可を割り当てます。

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. **Bootstrap-sample-db**スクリプトをダウンロードします。 このスクリプトはブートストラップスクリプトによって呼び出されます。

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートストラップスクリプトでは、ビッグデータクラスターに次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | < CLUSTER_NAMESPACE > | ビッグデータクラスターに付けた名前。 |
   | <SQL_MASTER_IP> | Master インスタンスの IP アドレス。 |
   | <SQL_MASTER_SA_PASSWORD> | Master インスタンスの SA パスワード。 |
   | <KNOX_IP> | HDFS/Spark ゲートウェイの IP アドレス。 |
   | <KNOX_PASSWORD> | HDFS/Spark ゲートウェイのパスワード。 |

   > [!TIP]
   > [Kubectl](cluster-troubleshooting-commands.md)を使用して、SQL Server マスターインスタンスと KNOX の IP アドレスを検索します。 を`kubectl get svc -n <your-big-data-cluster-name>`実行して、マスターインスタンスの外部 IP アドレス (**マスター svc-外部**) と Knox (**ゲートウェイ-svc**) を確認します。 クラスターの既定の名前は**mssql-cluster**です。

1. ブートストラップスクリプトを実行します。

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>次の手順

ブートストラップスクリプトを実行すると、ビッグデータクラスターにサンプルデータベースと HDFS データが含まれます。 次のチュートリアルでは、サンプルデータを使用してビッグデータクラスターの機能を示します。

データの仮想化:

- [チュートリアル: SQL Server ビッグデータクラスターでの HDFS のクエリ](tutorial-query-hdfs-storage-pool.md)
- [チュートリアル: SQL Server ビッグデータクラスターから Oracle にクエリを実行する](tutorial-query-oracle.md)

データの取り込み:

- [チュートリアル: Transact-sql を使用してデータを SQL Server データプールに取り込む](tutorial-data-pool-ingest-sql.md)
- [チュートリアル: Spark ジョブを使用して SQL Server データプールにデータを取り込む](tutorial-data-pool-ingest-spark.md)

向け

- [チュートリアル: SQL Server 2019 ビッグデータクラスターでサンプルノートブックを実行する](tutorial-notebook-spark.md)