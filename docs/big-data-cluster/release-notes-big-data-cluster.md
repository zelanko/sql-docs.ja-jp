---
title: リリース ノート
titleSuffix: SQL Server 2019 big data clusters
description: この記事では、最新の更新プログラムと SQL Server 2019 ビッグ データ クラスター (プレビュー) の既知の問題について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 4c178c5868789bec2dc80a4b68558f12afbc90d2
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58073228"
---
# <a name="release-notes-for-big-data-clusters-on-sql-server"></a>ビッグ データ クラスターは、SQL Server のリリース ノート

この記事では、更新プログラムの一覧し、ビッグ データの SQL Server クラスターの最新のリリースに関する問題を把握します。

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="ctp23"></a> CTP 2.3 (SQL 2019)

2019年 2 月&nbsp; &nbsp;  /  &nbsp; &nbsp; SQL Server 2019 &nbsp; &nbsp;  /  &nbsp; &nbsp; CTP2.3

### <a name="new-features"></a>新しい機能

| 新機能 | 詳細 |
| :---------- | :------ |
| [SQL Server ビッグ データ クラスター上で IntelliJ での Spark ジョブを送信する](spark-submit-job-intellij-tool-plugin.md)します。 | &nbsp; |
| [アプリケーションの展開とクラスターの管理のための一般的な CLI](big-data-cluster-create-apps.md)します。 | &nbsp; |
| [SQL Server のビッグ データ クラスターにアプリケーションを展開する VS Code 拡張機能](app-deployment-extension.md)します。 | &nbsp; |
| [変更、 **mssqlctl**コマンドの使用方法をツール](#mssqlctlctp23)します。 | &nbsp; |
| [Sparklyr を使用して、SQL Server 2019 ビッグ データ クラスターで](sparklyr-from-RStudio.md)します。 | &nbsp; |
| ビッグ データ クラスター外部の HDFS と互換性のあるストレージにマウント**HDFS が階層化**します。 | 参照してください[HDFS が階層化](hdfs-tiering.md)します。 |
| SQL Server のマスター インスタンスと HDFS/Spark ゲートウェイの新しい統一された接続エクスペリエンス。 | 参照してください[master の SQL Server インスタンスと HDFS/Spark ゲートウェイ](connect-to-big-data-cluster.md)します。 |
| クラスターを削除して**mssqlctl クラスター削除**これで、名前空間内のビッグ データ クラスターの一部であったオブジェクトのみを削除します。 | 名前空間は削除されません。 ただし、以前のリリースでこのコマンドは、名前空間の全体を削除しました。 |
| _セキュリティ_エンドポイントの名前が変更され、統合します。 | _前のエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-security-nodeport**<br/><br/>_新しいエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-security** |
| _プロキシ_エンドポイントの名前が変更され、統合します。 | _前のエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-proxy-nodeport**<br/><br/>_新しいエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-service-proxy** |
| _コント ローラー_エンドポイントの名前が変更され、統合します。 | _前のエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-lb**<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **service-mssql-controller-nodeport**<br/><br/>_新しいエンドポイント:_<br/> &nbsp; &nbsp; &nbsp; &bull; &nbsp; **endpoint-controller** |
| &nbsp; | &nbsp; |

### <a name="known-issues-deployment"></a>既知の問題:展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。

   > [!IMPORTANT]
   > データをバックアップし、既存のビッグ データ クラスターを削除する必要があります (の以前のバージョンを使用して**mssqlctl**) 最新リリースを展開する前にします。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-guidance.md#upgrade)します。

- **ACCEPT_EULA**環境変数が、EULA に同意するには、"Yes"または"yes"にする必要があります。 以前のリリースには、"y"と"Y"が許可されているが、これらは受け入れられないと、展開に失敗すると、します。

- **CLUSTER_PLATFORM**環境変数は以前のリリースと同様、既定値がありません。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

### <a name="known-issues-kubeadm-deployments"></a>既知の問題: kubeadm 展開

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

### <a id="mssqlctlctp23"></a> 既知の問題: mssqlctl

- **Mssqlctl**名詞-動詞の注文に順序付けの動詞-名詞コマンドからツールを変更します。 たとえば、`mssqlctl create cluster`が`mssqlctl cluster create`します。

- `--name`パラメーターが使用するクラスターを作成するときに必要な`mssqlctl cluster create`。

   ```bash
   mssqlctl cluster create --name <cluster_name>
   ```

- 最新バージョンのビッグ データ クラスターへのアップグレードに関する重要な情報と**mssqlctl**を参照してください[を新しいリリースにアップグレード](deployment-guidance.md#upgrade)します。

### <a name="known-issues-external-tables"></a>既知の問題:外部テーブル

- 列の型はサポートされていないテーブルのデータ プール外部テーブルを作成することになります。 外部テーブルを照会する場合はメッセージが表示、次のような。

   `Msg 7320, Level 16, State 110, Line 44 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 105079; Columns with large object types are not supported for external generic tables.`

- 記憶域プールの外部テーブルをクエリすると、同時に、基になるファイルを HDFS にコピーするは場合にエラーが発生する可能性があります。

   `Msg 7320, Level 16, State 110, Line 157 Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "(null)". 110806;A distributed query failed: One or more errors occurred.`

- 文字データ型を使用して Oracle に外部テーブルを作成する場合、Data Studio の Azure の仮想化ウィザードはこれらの列を VARCHAR として、外部テーブル定義で解釈されます。 外部テーブル DDL にエラーがなります。 いずれか NVARCHAR2 の種類を使用または EXTERNAL TABLE ステートメントを手動で作成し、ウィザードを使用してではなく NVARCHAR を指定するには、Oracle スキーマを変更します。

### <a name="known-issues-application-deployment"></a>既知の問題:アプリケーションの展開

- RESTful API から R、Python、または MLeap アプリケーションを呼び出すときに、呼び出しがタイムアウトに 5 分でします。

### <a name="known-issues-spark-and-notebooks"></a>既知の問題:Spark と notebook

- ポッド IP アドレスは、ポッドの再起動時に Kubernetes 環境で変更できます。 マスター ポッドを再起動する場合、Spark セッションが失敗とする`NoRoteToHostException`します。 これは、原因は新しい IP で更新しない JVM キャッシュでアドレスします。

- Windows に既にインストールされている Jupyter と別の Python がある、Spark のノートブックが失敗する可能性があります。 この問題を回避するには、Jupyter を最新バージョンにアップグレードします。

- Notebook をクリックした場合に、**テキストの追加**コマンド、テキスト セルが編集モードではなく、プレビュー モードで追加されます。 編集モードとセルの編集に切り替え、プレビュー アイコンをクリックすることができます。

### <a name="known-issues-hdfs"></a>既知の問題:HDFS

- プレビューするために HDFS 内のファイルを右クリックした場合は、次のエラーを参照してください可能性があります。

   `Error previewing file: File exceeds max size of 30MB`

   現時点で Azure Data Studio 30 MB より大きいファイルをプレビューする方法はありません。

- HDFS hdfs-site.xml への変更に関連する構成の変更はサポートされていません。

### <a name="known-issues-security"></a>既知の問題:セキュリティ

- SA_PASSWORD は、(たとえば、コードのダンプ ファイル) 内の一部の環境で見つけやすいです。 デプロイ後に、マスター インスタンスで SA_PASSWORD をリセットする必要があります。 これはありませんが、バグ、セキュリティ手順です。 Linux コンテナーで SA_PASSWORD を変更する方法の詳細については、次を参照してください。 [SA パスワードの変更](../linux/quickstart-install-connect-docker.md#sapassword)します。

- AKS のログは、ビッグ データ クラスターのデプロイの SA パスワードを含めることができます。

## <a id="ctp22"></a> CTP 2.2 (2018 の年 12 月)

次のセクションでは、新機能と SQL Server 2019 CTP 2.2 でのビッグ データ クラスターの既知の問題について説明します。

### <a name="whats-in-the-ctp-22-release"></a>CTP 2.2 のリリースの新機能ですか。

- クラスターの管理ポータルを使用してアクセス`/portal`(**https://\<ip アドレス\>: 30777/ポータル**)。
- マスターのプールのサービス名から変更`service-master-pool-lb`と`service-master-pool-nodeport`に`endpoint-master-pool`します。
- 新しいバージョンの**mssqlctl**イメージを更新します。
- その他のバグ修正と機能強化。

### <a name="known-issues"></a>既知の問題

次のセクションでは、CTP 2.2 での SQL Server のビッグ データ クラスターの既知の問題を説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。 バックアップし、最新のリリースを展開する前に、既存のビッグ データ クラスターを削除する必要があります。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-guidance.md#upgrade)します。

- を AKS にデプロイした後、展開から、次の 2 つの警告イベントを表示があります。 2 つのイベントには既知の問題が、それらが妨げられないして AKS でビッグ データ クラスターを正常に展開します。

   `Warning  FailedMount: Unable to mount volumes for pod "mssql-storage-pool-default-1_sqlarisaksclus(c83eae70-c81b-11e8-930f-f6b6baeb7348)": timeout expired waiting for volumes to attach or mount for pod "sqlarisaksclus"/"mssql-storage-pool-default-1". list of unmounted volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs]. list of unattached volumes=[storage-pool-storage hdfs storage-pool-mlservices-storage hadoop-logs storage-pool-java-storage secrets default-token-q9mlx]`

   `Warning  Unhealthy: Readiness probe failed: cat: /tmp/provisioner.done: No such file or directory`

- ビッグ データ クラスターのデプロイが失敗した場合、関連付けられた名前空間は削除されません。 これは、結果、クラスターの孤立した、名前空間。 回避策では、同じ名前のクラスターをデプロイする前に、名前空間を手動で削除します。

#### <a name="cluster-administration-portal"></a>クラスターの管理ポータル

クラスターの管理ポータルでは、SQL Server のマスター インスタンスのエンドポイントは表示されません。 マスター インスタンスの IP アドレスとポートを検索するには、次を使用**kubectl**コマンド。

```
kubectl get svc endpoint-master-pool -n <your-cluster-name>
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

### <a name="whats-in-the-ctp-21-release"></a>CTP 2.1 リリースの新機能ですか。

- [Python および R のアプリを展開する](big-data-cluster-create-apps.md)でビッグ データ クラスター。
- 新しいバージョンの**mssqlctl**イメージを更新します。 
- その他のバグ修正と機能強化。

### <a name="known-issues"></a>既知の問題

次のセクションでは、CTP 2.1 での SQL Server のビッグ データ クラスターの既知の問題を説明します。

#### <a name="deployment"></a>展開

- 以前のリリースからのビッグ データのデータのクラスターのアップグレードはサポートされていません。 バックアップし、最新のリリースを展開する前に、既存のビッグ データ クラスターを削除する必要があります。 詳細については、次を参照してください。[を新しいリリースにアップグレード](deployment-guidance.md#upgrade)します。

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

### <a name="whats-in-the-ctp-20-release"></a>CTP 2.0 リリースの新機能ですか。

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
