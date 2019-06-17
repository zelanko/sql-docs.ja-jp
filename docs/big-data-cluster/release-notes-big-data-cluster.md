---
title: リリース ノート
titleSuffix: SQL Server big data clusters
description: この記事では、最新の更新プログラムと SQL Server 2019 ビッグ データ クラスター (プレビュー) の既知の問題について説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d3967da74969556cd96483d4a9c3afa3135fa342
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66779220"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>ビッグ データ クラスターは、SQL Server のリリース ノート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、更新プログラムの一覧し、ビッグ データの SQL Server クラスターの最新のリリースに関する問題を把握します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp30"></a> CTP 3.0 (月)

次のセクションでは、新機能と SQL Server 2019 CTP 3.0 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| **mssqlctl** の更新 | 複数の **mssqlctl** [コマンドとパラメーターが更新されました](../big-data-cluster/reference-mssqlctl.md)。 これには、コントローラーのユーザー名とエンドポイントをターゲットにするようになった **mssqlctl login** コマンドの更新も含まれています。 |
| ストレージの機能強化 | ログとデータのさまざまなストレージ構成のサポート。 また、ビッグ データ クラスターへの永続ボリューム要求の数が削減されました。 |
| 複数のコンピューティング プール インスタンス | 複数のコンピューティング プール インスタンスのサポート。 |
| 新しいプールの動作と機能 | コンピューティング プールは、既定で **ROUND_ROBIN** 配布内​​のストレージ プールおよびデータ プールの操作にのみ使用されるようになりました。 データ プールで新しい **REPLICATED** 分布の種類が使用できるようになりました。これは、同じデータがすべてのデータ プール インスタンスに存在することを意味します。 |
| 外部テーブルの機能強化 | HADOOP データ ソースの種類の外部テーブルで、最大サイズ 1 MB の行の読み取りがサポートされるようになりました。 外部テーブル (ODBC、記憶域プール、データ プール) で、SQL Server テーブルと同じ幅の行がサポートされるようになりました。 |

### <a name="known-issues"></a>既知の問題

次のセクションでは、このリリースでの制限事項と既知の問題について説明します。

#### <a name="hdfs"></a>HDFS

- Azure Data Studio は、HDFS に新しいフォルダーを作成しようとしたときにエラーを返します。 この機能を有効にするのには、Azure Data Studio の insider ビルドをインストールします。
  
   - [Windows ユーザー インストーラー - **Insider のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-user/insider)
   - [Windows システムのインストーラー - **Insider のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64/insider)
   - [Windows - ZIP **Insider のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/win32-x64-archive/insider)
   - [macOS - ZIP **Insider のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/darwin/insider)
   - [Linux TAR します。GZ - **Insider のビルド**](https://azuredatastudio-update.azurewebsites.net/latest/linux-x64/insider)

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="deployment"></a>展開

- GPU 対応のビッグ データ クラスターの以前の展開手順は、CTP 3.0 ではサポートされません。 代替のデプロイの手順を調査中です。 ここでは、記事「展開ビッグ データ クラスターの GPU サポートと共にと TensorFlow を実行」を一時的に混乱を避けるため未発行されています。

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > データをバックアップし、既存のビッグ データ クラスターを削除する必要があります (の以前のバージョンを使用して**mssqlctl**) 最新リリースを展開する前にします。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="external-tables"></a>外部テーブル

- ビッグ データ クラスターのデプロイを作成しなく、 **SqlDataPool**と**SqlStoragePool**外部データ ソース。 データのプールと記憶域プールへのデータ仮想化をサポートするために手動でこれらのデータ ソースを作成することができます。

   > [!NOTE]
   > これらの外部データ ソースを作成するための URI では、Ctp で異なります。 それらを作成する方法については、次の TRANSACT-SQL コマンドを参照してください。 

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://controller-svc:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://controller-svc:8080/default');
   ```

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用して Oracle に外部テーブルを作成する場合、Data Studio の Azure の仮想化ウィザードはこれらの列を VARCHAR として、外部テーブル定義で解釈されます。 外部テーブル DDL にエラーがなります。 いずれか NVARCHAR2 の種類を使用または EXTERNAL TABLE ステートメントを手動で作成し、ウィザードを使用してではなく NVARCHAR を指定するには、Oracle スキーマを変更します。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すときに、呼び出しがタイムアウトに 5 分でします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp25"></a> CTP 2.5 (年 4 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.5 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| 展開プロファイル | ビッグ データ クラスターの展開には、環境変数の代わりに、既定およびカスタマイズした[展開構成 JSON ファイル](deployment-guidance.md#configfile)を使用します。 |
| 入力が求められる展開 | `mssqlctl cluster create` では、既定の展開に必要な設定の入力が求められるようになりました。 |
| サービス エンドポイントとのポッド名の変更 | 次の外部エンドポイントの名前が変更されました。<br/>&nbsp;&nbsp;&nbsp;- **endpoint-master-pool** => **master-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-controller** => **controller-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-service-proxy** => **mgmtproxy-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-security** => **gateway-svc-external**<br/>&nbsp;&nbsp;&nbsp;- **endpoint-app-service-proxy** => **appproxy-svc-external**|
| **mssqlctl** の機能強化 | **mssqlctl** を使用して[外部エンドポイントを一覧表示](deployment-guidance.md#endpoints)し、**mssqlctl** のバージョンを `--version` パラメーターを使用して確認します。 |
| オフライン インストール | オフラインのビッグ データ クラスターの展開のガイダンスです。 |
| HDFS 階層の機能強化 | ADLS Gen2 の S3 が階層化、マウントは、次のキャッシュ、および OAuth をサポートします。 |
| 新しい`mssql`Spark SQL Server コネクタ | |

### <a name="known-issues"></a>既知の問題

次のセクションでは、このリリースでの制限事項と既知の問題について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > データをバックアップし、既存のビッグ データ クラスターを削除する必要があります (の以前のバージョンを使用して**mssqlctl**) 最新リリースを展開する前にします。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="external-tables"></a>外部テーブル

- ビッグ データ クラスターのデプロイを作成しなく、 **SqlDataPool**と**SqlStoragePool**外部データ ソース。 データのプールと記憶域プールへのデータ仮想化をサポートするために手動でこれらのデータ ソースを作成することができます。

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://nmnode-0-svc:50070');
   ```

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用して Oracle に外部テーブルを作成する場合、Data Studio の Azure の仮想化ウィザードはこれらの列を VARCHAR として、外部テーブル定義で解釈されます。 外部テーブル DDL にエラーがなります。 いずれか NVARCHAR2 の種類を使用または EXTERNAL TABLE ステートメントを手動で作成し、ウィザードを使用してではなく NVARCHAR を指定するには、Oracle スキーマを変更します。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すときに、呼び出しがタイムアウトに 5 分でします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp24"></a> CTP 2.4 (3 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.4 でビッグ データ クラスターの既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
|:---|:---|
| Spark で TensorFlow を使用しディープ ラーニングを実行する場合の GPU でのサポートに関するガイダンス。 | [GPU をサポートしているビッグ データ クラスターを展開し、TensorFlow を実行します](spark-gpu-tensorflow.md)。 |
| データ ソース **SqlDataPool** と **SqlStoragePool** は、既定では作成されなくなりました。 | 必要に応じてこれらを手動で作成します。 [既知の問題](#externaltablesctp24)を参照してください。 |
| データ プール用の `INSERT INTO SELECT` のサポート。 | 例については、「[Tutorial:Ingest data into a SQL Server data pool with Transact-SQL](tutorial-data-pool-ingest-sql.md)」 (チュートリアル: Transact SQL を使用して SQL Server のデータ プールにデータを取り込む) を参照してください。 |
| オプション `FORCE SCALEOUTEXECUTION` と `DISABLE SCALEOUTEXECUTION` | 強制的に有効または無効にコンピューティングの使用は、外部テーブルに対するクエリのプールです。 たとえば、`SELECT TOP(100) * FROM web_clickstreams_hdfs_book_clicks OPTION(FORCE SCALEOUTEXECUTION)` のようにします。 |
| 更新された AKS の展開に関する推奨事項 | AKS でビッグ データ クラスターを評価するときには、サイズ **Standard_L8s** の単一ノードを使用することをお勧めします。 |
| Spark 2.4 への Spark のランタイムのアップグレード。 | |

### <a name="known-issues"></a>既知の問題

次のセクションでは、このリリースでの制限事項と既知の問題について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > データをバックアップし、既存のビッグ データ クラスターを削除する必要があります (の以前のバージョンを使用して**mssqlctl**) 最新リリースを展開する前にします。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="kubeadm-deployments"></a>kubeadm 展開

複数のコンピューターでの Kubernetes のデプロイに kubeadm を使用する場合、クラスターの管理ポータルのビッグ データ クラスターに接続するために必要なエンドポイントは正しく表示されません。 この問題が発生する場合は、次の回避を使用して、サービス エンドポイントの IP アドレスを検出します。

- クラスター内から接続する場合は、サービスの ip アドレスに接続するエンドポイントの Kubernetes を照会します。 たとえば、次**kubectl**コマンドには、SQL Server のマスター インスタンスの IP アドレスが表示されます。

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- クラスターの外部から接続する場合は、次の手順を使用して接続します。

   1. SQL Server のマスター インスタンスを実行しているノードの IP アドレスを取得:`kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`します。

   1. この IP アドレスを使用して SQL Server マスター インスタンスに接続します。

   1. クエリ、 **cluster_endpoint_table**他の外部エンドポイントの master データベースにします。

      これは、接続タイムアウトで失敗すると、そのそれぞれのノードは、ファイアウォールで隔て可能性があります。 ここでは、Kubernetes クラスター管理者に連絡して、外部に公開されているノードの IP を要求します。 これは、任意のノード。 クラスターで実行されているさまざまなサービスに接続し、その ip アドレスと対応するポートを使用できます。 たとえば、管理者は、実行して、この IP を確認できます。

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a name="delete-cluster-fails"></a>削除クラスターが失敗しました。

使用するクラスターを削除しようとする**mssqlctl**、次のエラーで失敗します。

```
2019-03-26 20:38:11.0614 UTC | INFO | Deleting cluster ...
Error processing command: "TypeError"
delete_namespaced_service() takes 3 positional arguments but 4 were given
Makefile:61: recipe for target 'delete-cluster' failed
make[2]: *** [delete-cluster] Error 1
Makefile:223: recipe for target 'deploy-clean' failed
make[1]: *** [deploy-clean] Error 2
Makefile:203: recipe for target 'deploy-clean' failed
make: *** [deploy-clean] Error 2
```

新しい Python Kubernetes クライアント (バージョン 9.0.0) に変更されており、現在それが削除名前空間 API、 **mssqlctl**します。 これは、新しい Kubernetes python クライアントをインストールした場合にのみ発生します。 この問題を回避するには、クラスターを使用して、直接削除することによって**kubectl** (`kubectl delete ns <ClusterName>`) を使用して古いバージョンをインストールすることも`sudo pip install kubernetes==8.0.1`します。

#### <a id="externaltablesctp24"></a> 外部テーブル

- ビッグ データ クラスターのデプロイを作成しなく、 **SqlDataPool**と**SqlStoragePool**外部データ ソース。 データのプールと記憶域プールへのデータ仮想化をサポートするために手動でこれらのデータ ソースを作成することができます。

   ```sql
   -- Create default data sources for SQL Big Data Cluster
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
       CREATE EXTERNAL DATA SOURCE SqlDataPool
       WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
 
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   ```

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用して Oracle に外部テーブルを作成する場合、Data Studio の Azure の仮想化ウィザードはこれらの列を VARCHAR として、外部テーブル定義で解釈されます。 外部テーブル DDL にエラーがなります。 いずれか NVARCHAR2 の種類を使用または EXTERNAL TABLE ステートメントを手動で作成し、ウィザードを使用してではなく NVARCHAR を指定するには、Oracle スキーマを変更します。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すときに、呼び出しがタイムアウトに 5 分でします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp23"></a> CTP 2.3 (2 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.3 でビッグ データ クラスターの既知の問題について説明します。

### <a name="whats-new"></a>新機能

| 新機能または更新 | 詳細 |
| :---------- | :------ |
| IntelliJ のビッグ データ クラスターでの Spark ジョブの送信。 | [IntelliJ の SQL Server ビッグ データ クラスターで Spark ジョブを送信する](spark-submit-job-intellij-tool-plugin.md) |
| アプリケーションの展開およびクラスター管理の一般的な CLI。 | [SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリを展開する方法](big-data-cluster-create-apps.md) |
| ビッグ データ クラスターにアプリケーションを展開するための VS Code の拡張機能。 | [VS Code を使用して SQL Server のビッグ データ クラスターにアプリケーションを展開する方法](app-deployment-extension.md) |
| **mssqlctl**ツール コマンドの使用方法の変更。 | 詳細については、[mssqlctl の既知の問題](#mssqlctlctp23)を参照してください。 |
| Sparklyr を使用して、ビッグ データ クラスター | [SQL Server 2019 のビッグ データ クラスターで Sparklyr を使用する](sparklyr-from-RStudio.md) |
| **HDFS 階層**を使用した、外部の HDFS 互換ストレージのビッグ データ クラスターへのマウント。 | [HDFS 階層](hdfs-tiering.md)に関するページを参照してください。 |
| SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイの新しい統一された接続エクスペリエンス。 | [SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイ](connect-to-big-data-cluster.md)に関するページを参照してください。 |
| **mssqlctl cluster delete** を使用してクラスターを削除すると、ビッグ データ クラスターの一部であった名前空間内のオブジェクトのみが削除されるようになりました。 | 名前空間は削除されません。 ただし、以前のリリースでは、このコマンドを使用すると、名前空間全体が削除されました。 |
| _セキュリティ_ エンドポイントの名前が変更され、統合されました。 | **service-security-lb** と **service-security-nodeport** は、**endpoint-security** エンドポイントに統合されました。 |
| _プロキシ_ エンドポイントの名前が変更され、統合されました。 | **service-proxy-lb** と **service-proxy-nodeport** は、**endpoint-service-proxy** エンドポイントに統合されました。 |
| _コントローラー_ エンドポイントの名前が変更され、統合されました。 | **service-mssql-controller-lb** と **service-mssql-controller-nodeport** は、**endpoint-controller** エンドポイントに統合されました。 |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>既知の問題

次のセクションでは、このリリースでの制限事項と既知の問題について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > データをバックアップし、既存のビッグ データ クラスターを削除する必要があります (の以前のバージョンを使用して**mssqlctl**) 最新リリースを展開する前にします。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- **ACCEPT_EULA**環境変数が、EULA に同意するには、"Yes"または"yes"にする必要があります。 以前のリリースには、"y"と"Y"が許可されているが、これらは受け入れられないと、展開に失敗すると、します。

- **CLUSTER_PLATFORM**環境変数は以前のリリースと同様、既定値がありません。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="kubeadm-deployments"></a>kubeadm 展開

複数のコンピューターでの Kubernetes のデプロイに kubeadm を使用する場合、クラスターの管理ポータルのビッグ データ クラスターに接続するために必要なエンドポイントは正しく表示されません。 この問題が発生する場合は、次の回避を使用して、サービス エンドポイントの IP アドレスを検出します。

- クラスター内から接続する場合は、サービスの ip アドレスに接続するエンドポイントの Kubernetes を照会します。 たとえば、次**kubectl**コマンドには、SQL Server のマスター インスタンスの IP アドレスが表示されます。

   ```bash
   kubectl get service endpoint-master-pool -n <clusterName> -o=custom-columns="IP:.spec.clusterIP,PORT:.spec.ports[*].nodePort"
   ```

- クラスターの外部から接続する場合は、次の手順を使用して接続します。

   1. SQL Server のマスター インスタンスを実行しているノードの IP アドレスを取得:`kubectl get pod mssql-master-pool-0 -o jsonpath="Name: {.metadata.name} Status: {.status.hostIP}" -n <clusterName>`します。

   1. この IP アドレスを使用して SQL Server マスター インスタンスに接続します。

   1. クエリ、 **cluster_endpoint_table**他の外部エンドポイントの master データベースにします。

      これは、接続タイムアウトで失敗すると、そのそれぞれのノードは、ファイアウォールで隔て可能性があります。 ここでは、Kubernetes クラスター管理者に連絡して、外部に公開されているノードの IP を要求します。 これは、任意のノード。 クラスターで実行されているさまざまなサービスに接続し、その ip アドレスと対応するポートを使用できます。 たとえば、管理者は、実行して、この IP を確認できます。

      ```
      [root@m12hn01 config]# kubectl cluster-info
      Kubernetes master is running at https://172.50.253.99:6443
      KubeDNS is running at https://172.30.243.91:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
      ```

#### <a id="mssqlctlctp23"></a> mssqlctl

- **Mssqlctl**名詞-動詞の注文に順序付けの動詞-名詞コマンドからツールを変更します。 たとえば、`mssqlctl create cluster`が`mssqlctl cluster create`します。

- `--name`パラメーターが使用するクラスターを作成するときに必要な`mssqlctl cluster create`。

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- 最新バージョンのビッグ データ クラスターへのアップグレードに関する重要な情報と**mssqlctl**を参照してください[を新しいリリースにアップグレード](deployment-upgrade.md)します。

#### <a name="external-tables"></a>外部テーブル

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用して Oracle に外部テーブルを作成する場合、Data Studio の Azure の仮想化ウィザードはこれらの列を VARCHAR として、外部テーブル定義で解釈されます。 外部テーブル DDL にエラーがなります。 いずれか NVARCHAR2 の種類を使用または EXTERNAL TABLE ステートメントを手動で作成し、ウィザードを使用してではなく NVARCHAR を指定するには、Oracle スキーマを変更します。

#### <a name="application-deployment"></a>アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すときに、呼び出しがタイムアウトに 5 分でします。

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp22"></a> CTP 2.2 (2018 の年 12 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.2 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- クラスターの管理ポータルを使用してアクセス`/portal`(**https://\<ip アドレス\>: 30777/ポータル**)。
- マスターのプールのサービス名から変更`service-master-pool-lb`と`service-master-pool-nodeport`に`endpoint-master-pool`します。
- 新しいバージョンの**mssqlctl**イメージを更新します。
- その他のバグ修正と機能強化。

### <a name="known-issues"></a>既知の問題

次のセクションでは、このリリースでの制限事項と既知の問題について説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。 バックアップし、最新のリリースを展開する前に、既存のビッグ データ クラスターを削除する必要があります。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="cluster-administration-portal"></a>クラスターの管理ポータル

クラスターの管理ポータルでは、SQL Server のマスター インスタンスのエンドポイントは表示されません。 マスター インスタンスの IP アドレスとポートを検索するには、次を使用**kubectl**コマンド。

```
kubectl get svc endpoint-master-pool -n <your-big-data-cluster-name>
```

#### <a name="external-tables"></a>外部テーブル

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp21"></a> CTP 2.1 (2018 年 11 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.1 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- [Python および R のアプリを展開する](big-data-cluster-create-apps.md)でビッグ データ クラスター。
- 新しいバージョンの**mssqlctl**イメージを更新します。 
- その他のバグ修正と機能強化。

### <a name="known-issues"></a>既知の問題

次のセクションでは、CTP 2.1 での SQL Server のビッグ データ クラスターの既知の問題を説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。 バックアップし、最新のリリースを展開する前に、既存のビッグ データ クラスターを削除する必要があります。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-upgrade.md)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="admin-portal"></a>管理ポータル

- ときにする[msqlctl ctp コマンドを使用してアプリを作成](big-data-cluster-create-apps.md)しビッグ データ クラスター、クラスターの管理ポータルでは表示ポッド Admin 部分のコント ローラーのセクションでは、「不明」として、アプリケーションが配置された SQL Server に展開します。

#### <a name="external-tables"></a>外部テーブル

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp20"></a> CTP 2.0 (2018 の年 10 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.0 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="new-features"></a>新しい機能

- Mssqlctl 管理ツールを使用してシンプルなデプロイ操作
- Azure Data Studio でネイティブのノートブック エクスペリエンス
- SQL Server のインスタンスのストレージを使用して HDFS ファイルをクエリします。
- マスター SQL Server、Oracle、MongoDB、および HDFS を使用してデータの仮想化
- SQL Server と Azure Data Studio での Oracle のデータ仮想化ウィザード
- マスターの ML サービス
- クラスターの監視とトラブルシューティングに使用できる管理ポータル
- Azure Data Studio で Spark ジョブを送信します。 
- クラスターの管理ポータルでの Spark UI
- ボリュームの記憶域クラスへのマウント
- マスターからのデータ プールに対するクエリ
- SSMS で、分散クエリ プランを表示します。
- Mssqlctl 管理ツールの pip パッケージ
- コント ローラー サービスを経由して組み込みの配置エンジン

### <a name="known-issues"></a>既知の問題

次のセクションでは、CTP 2.0 で SQL Server のビッグ データ クラスターの既知の問題を説明します。

#### <a name="deployment"></a>展開

- Azure Kubernetes Service (AKS) を使用している場合は、Kubernetes の推奨されるバージョン、1.10。 *、ディスクのサイズ変更はサポートされていません。 ストレージ サイズの変更はそれに応じてことを確認する必要がありますデプロイ時にします。 ストレージのサイズを調整する方法の詳細については、次を参照してください。、[データ永続化](concept-data-persistence.md)記事。 Vm にデプロイされた kubernetes は、推奨されるバージョンは、1.11 です。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="external-tables"></a>外部テーブル

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

#### <a name="spark-and-notebooks"></a>Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

#### <a name="hdfs"></a>HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

#### <a name="security"></a>セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a name="next-steps"></a>次のステップ

ビッグ データの SQL Server クラスターの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
