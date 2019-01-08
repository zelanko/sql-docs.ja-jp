---
title: サンプル データを読み込む
titleSuffix: SQL Server 2019 big data clusters
description: このチュートリアルでは、SQL Server のビッグ データ クラスターにサンプル データを読み込む方法を示します。 サンプル データには、SQL Server のマスター インスタンス内のリレーショナル データが含まれます。 記憶域プールでの HDFS データも含まれています。 このデータは、このセクションでは、他のチュートリアルをサポートします。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 67e97774a00fed123ba6733688e002f1b57ba743
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53439389"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-2019-big-data-cluster"></a>チュートリアル:SQL Server 2019 のビッグ データ クラスターにサンプル データを読み込む

このチュートリアルでは、SQL Server 2019 ビッグ データ クラスター (プレビュー) にサンプル データを読み込むスクリプトを使用する方法について説明します。 ドキュメント内の他のチュートリアルの多くは、次のサンプル データを使用します。

> [!TIP]
> SQL Server 2019 ビッグ データ クラスター (プレビュー) の他のサンプルを見つけることができます、 [sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster)GitHub リポジトリ。 内にある、 **sql-server-samples/samples/features/sql-big-data-cluster/** パス。

## <a name="prerequisites"></a>前提条件

- [デプロイされたビッグ データ クラスター](deployment-guidance.md)
- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **mssqlctl**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a> サンプル データを読み込む

次の手順では、ブートス トラップ スクリプトを使用して SQL Server データベースのバックアップをダウンロードして、ビッグ データ クラスターにデータを読み込みます。 使いやすいように、次の手順に分割されている[Windows](#windows)と[Linux](#linux)セクション。

## <a id="windows"></a> Windows

次の手順では、Windows クライアントを使用して、ビッグ データ クラスターにサンプル データを読み込む方法について説明します。

1. 新しい Windows コマンド プロンプトを開きます。

   > [!IMPORTANT]
   > これらの手順については、Windows PowerShell を使用しないでください。 スクリプトは PowerShell での PowerShell のバージョンを使用するため失敗します**curl**します。

1. 使用**curl**サンプル データのブートス トラップ スクリプトをダウンロードします。

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. ダウンロード、**します。 ブートス トラップのサンプル**Transact SQL スクリプト。 このスクリプトは、ブートス トラップ スクリプトによって呼び出されます。

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートス トラップのスクリプトでは、ビッグ データ クラスターに、次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | &LT; CLUSTER_NAMESPACE &GT; | ビッグ データ クラスターを指定した名前。 |
   | &LT; SQL_MASTER_IP &GT; | マスター インスタンスの IP アドレス。 |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | マスター インスタンスの SA パスワード。 |
   | &LT; KNOX_IP &GT; | HDFS/Spark ゲートウェイの IP アドレス。 |
   | &LT; KNOX_PASSWORD &GT; | HDFS/Spark ゲートウェイのパスワード。 |

   > [!TIP]
   > 使用[kubectl](cluster-troubleshooting-commands.md) master の SQL Server インスタンスおよび Knox の IP アドレスが見つかりません。 実行`kubectl get svc -n <your-cluster-name>`マスター インスタンスの外部 IP アドレスを確認し、(**エンドポイント-マスター プール**) および Knox (**サービス-セキュリティ-lb**または**サービス セキュリティ nodeport**).

1. ブートス トラップ スクリプトを実行します。

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

次の手順では、Linux クライアントを使用して、ビッグ データ クラスターにサンプル データを読み込む方法について説明します。

1. ブートス トラップのスクリプトをダウンロードして実行可能アクセス許可を割り当てます。

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. ダウンロード、**します。 ブートス トラップのサンプル**Transact SQL スクリプト。 このスクリプトは、ブートス トラップ スクリプトによって呼び出されます。

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. ブートス トラップのスクリプトでは、ビッグ データ クラスターに、次の位置指定パラメーターが必要です。

   | パラメーター | 説明 |
   |---|---|
   | &LT; CLUSTER_NAMESPACE &GT; | ビッグ データ クラスターを指定した名前。 |
   | &LT; SQL_MASTER_IP &GT; | マスター インスタンスの IP アドレス。 |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | マスター インスタンスの SA パスワード。 |
   | &LT; KNOX_IP &GT; | HDFS/Spark ゲートウェイの IP アドレス。 |
   | &LT; KNOX_PASSWORD &GT; | HDFS/Spark ゲートウェイのパスワード。 |

   > [!TIP]
   > 使用[kubectl](cluster-troubleshooting-commands.md) master の SQL Server インスタンスおよび Knox の IP アドレスが見つかりません。 実行`kubectl get svc -n <your-cluster-name>`マスター インスタンスの外部 IP アドレスを確認し、(**エンドポイント-マスター プール**) および Knox (**サービス-セキュリティ-lb**または**サービス セキュリティ nodeport**).

1. ブートス トラップ スクリプトを実行します。

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>次の手順

ブートス トラップ スクリプトを実行した後、ビッグ データ クラスターは、サンプル データベースと HDFS のデータを持ちます。 このデータとクラスターのビッグ データの探索を開始するを参照してください。、[チュートリアル](tutorial-query-hdfs-storage-pool.md)このセクションでします。