---
title: サンプル データを読み込む
titleSuffix: SQL Server big data clusters
description: このチュートリアルでは、SQL Server ビッグ データ クラスターにサンプル データを読み込む方法について説明します。 サンプル データには、SQL Server マスター インスタンス内のリレーショナル データが含まれています。 また、記憶域プール内の HDFS データも取り込まれています。 このデータは、このセクションの他のチュートリアルにも対応しています。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 52285164928e1a4811abc17e931a1af1921c6d07
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "76831409"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>チュートリアル:SQL Server ビッグ データ クラスターにサンプル データを読み込む

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、スクリプトを使用して [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]にサンプル データを読み込む方法について説明します。 ドキュメントに記載されている他のチュートリアルの多くで、このサンプル データが使用されています。

> [!TIP]
> [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]の追加のサンプルは、[sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) GitHub リポジトリにあります。 それらは、パス **sql-server-samples/samples/features/sql-big-data-cluster/** に置かれています。

## <a name="prerequisites"></a>前提条件

- [展開済みのビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**
 
## <a id="sampledata"></a> サンプル データを読み込む

次の手順では、ブートストラップ スクリプトを使用して SQL Server データベースのバックアップをダウンロードし、ご利用のビッグ データ クラスターにそのデータを読み込みます。 使いやすいように、これらの手順は 「[Windows](#windows)」セクションと「[Linux](#linux)」セクションに分けられています。 認証メカニズムとして基本的なユーザー名とパスワードを使用する場合は、スクリプトを実行する前に AZDATA_USERNAME と AZDATA_PASSWORD の環境変数を設定します。 それ以外の場合、スクリプトでは SQL Server マスター インスタンスと Knox ゲートウェイへの接続に統合認証が使用されます。 また、統合認証を使用するには、エンドポイントに対して DNS 名を指定する必要があります。

## <a id="windows"></a> Windows

次の手順では、Windows クライアントを使用して、ご利用のビッグ データ クラスターにサンプル データを読み込む方法について説明します。

1. 新しい Windows コマンド プロンプトを開きます。

   > [!IMPORTANT]
   > これらの手順には、Windows PowerShell を使用しないでください。 Powershell では、PowerShell バージョンの **curl** が使用されるため、スクリプトは失敗します。

1. **curl** を使用して、サンプル データ用のブートストラップ スクリプトをダウンロードします。

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. **bootstrap-sample-db.sql** Transact-SQL スクリプトがダウンロードされます。 このスクリプトは、ブートストラップ スクリプトによって呼び出されます。

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートストラップ スクリプトでは、ご利用のビッグ データ クラスターに関する次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | <CLUSTER_NAMESPACE> | ビッグ データ クラスターに付ける名前。 |
   | <SQL_MASTER_ENDPOINT> | マスター インスタンスの DNS 名または IP アドレス。 |
   | <KNOX_ENDPOINT> | HDFS および Spark ゲートウェイの DNS 名または IP アドレス。 |
   
   > [!TIP]
   > [kubectl](cluster-troubleshooting-commands.md) を使用して、SQL Server マスター インスタンスと Knox の IP アドレスを検索します。 `kubectl get svc -n <your-big-data-cluster-name>` を実行して、マスター インスタンスの EXTERNAL-IP アドレス (**master-svc-external**) と Knox (**gateway-svc-external**) を確認します。 クラスターの既定の名前は **mssql-cluster** です。

1. ブートストラップ スクリプトを実行します。

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_ENDPOINT> <KNOX_ENDPOINT>
   ```

## <a id="linux"></a> Linux

次の手順では、Linux クライアントを使用して、ご利用のビッグ データ クラスターにサンプル データを読み込む方法について説明します。

1. ブートストラップ スクリプトをダウンロードし、実行可能ファイルのアクセス許可を割り当てます。

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. **bootstrap-sample-db.sql** Transact-SQL スクリプトがダウンロードされます。 このスクリプトは、ブートストラップ スクリプトによって呼び出されます。

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートストラップ スクリプトでは、ご利用のビッグ データ クラスターに関する次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | <CLUSTER_NAMESPACE> | ビッグ データ クラスターに付ける名前。 |
   | <SQL_MASTER_ENDPOINT> | マスター インスタンスの DNS 名または IP アドレス。 |
   | <KNOX_ENDPOINT> | HDFS および Spark ゲートウェイの DNS 名または IP アドレス。 |

   > [!TIP]
   > [kubectl](cluster-troubleshooting-commands.md) を使用して、SQL Server マスター インスタンスと Knox の IP アドレスを検索します。 `kubectl get svc -n <your-big-data-cluster-name>` を実行して、マスター インスタンスの EXTERNAL-IP アドレス (**master-svc-external**) と Knox (**gateway-svc-external**) を確認します。 クラスターの既定の名前は **mssql-cluster** です。

1. ブートストラップ スクリプトを実行します。

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_ENDPOINT> <KNOX_ENDPOINT>
   ```

## <a name="next-steps"></a>次のステップ

ブートストラップ スクリプトが実行されると、ご利用のビッグ データ クラスターにはサンプル データベースと HDFS データが取り込まれます。 次のチュートリアルでは、サンプル データを使用してビッグ データ クラスターの機能を実演します。

データの仮想化:

- [チュートリアル:SQL Server ビッグ データ クラスター内の HDFS にクエリを実行する](tutorial-query-hdfs-storage-pool.md)
- [チュートリアル:SQL Server ビッグ データ クラスターから Oracle にクエリを実行する](tutorial-query-oracle.md)

データ インジェスト:

- [チュートリアル:Transact-SQL を使用して SQL Server のデータ プールにデータを取り込む](tutorial-data-pool-ingest-sql.md)
- [チュートリアル:Spark ジョブを使用して SQL Server のデータ プールにデータを取り込む](tutorial-data-pool-ingest-spark.md)

Notebooks:

- [チュートリアル:SQL Server 2019 ビッグ データ クラスターでサンプルのノートブックを実行する](tutorial-notebook-spark.md)
