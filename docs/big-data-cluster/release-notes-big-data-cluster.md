---
title: SQL Server ビッグ データ クラスターのリリース ノート
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server ビッグ データ クラスターの最新の更新プログラムと既知の問題について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ba9d87d4985655b314faf391eaffb8f28ba35519
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75721690"
---
# <a name="sql-server-2019-big-data-clusters-release-notes"></a>SQL Server 2019 ビッグ データ クラスターのリリース ノート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次のリリース ノートは、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]に適用されます。 この記事は、リリースごとのセクションに分けられています。 各リリースには、Linux パッケージのダウンロードへのリンクに加えて、CU の変更について説明するサポート記事へのリンクが含まれています。 この記事には、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) の最新リリースに関する[既知の問題](#known-issues)の一覧もあります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

このセクションでは、[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) でサポートされているプラットフォームについて説明します。

### <a name="kubernetes-platforms"></a>Kubernetes プラットフォーム

|プラットフォーム|サポートされているバージョン|
|---------|---------|
|Kubernetes|BDC に必要な Kubernetes の最小バージョンは 1.13 です。 Kubernetes バージョンのサポート ポリシーについては、[Kubernetes バージョンとバージョン スキュー サポート](https://kubernetes.io/docs/setup/release/version-skew-policy/)に関するページを参照してください。|
|Azure Kubernetes Service (AKS)|BDC に必要な AKS の最小バージョンは 1.13 です。<br/>バージョンのサポート ポリシーについては、[AKS でサポートされている Kubernetes のバージョン](/azure/aks/supported-kubernetes-versions)に関するページを参照してください。|

### <a name="host-os-for-kubernetes"></a>Kubernetes のホスト OS

|プラットフォーム|サポートされているバージョン|
|---------|---------|
|Red Hat Enterprise Linux|7.3、7.4、7.5、7.6|
|Ubuntu|16.04|

### <a name="sql-server-editions"></a>SQL Server のエディション

|Edition|Notes|
|---------|---------|
|Enterprise<br/>Standard<br/>Developer| ビッグ データ クラスターのエディションは、SQL Server マスター インスタンスのエディションによって決まります。 展開時に、Developer エディションが既定で展開されます。 エディションは、展開後に変更できます。 [SQL Server マスター インスタンスの構成](../big-data-cluster/configure-sql-server-master-instance.md)に関するページを参照してください。 |

## <a name="tools"></a>ツール

|プラットフォーム|サポートされているバージョン|
|---------|---------|
|`azdata`|サーバーと同じマイナー バージョンを指定する必要があります (SQL Server マスター インスタンスと同様)。<br/>`azdata –-version` を実行して、バージョンを検証します。 現時点では、このバージョンは `15.0.2070` です。|
|Azure Data Studio|[Azure Data Studio](https://aka.ms/getazuredatastudio) の最新のビルドを取得します。|

## <a name="release-history"></a>リリース履歴

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] のリリース履歴の一覧を次の表に示します。

| Release               | Version       | リリース日 |
|-----------------------|---------------|--------------|
| [CU1](#cu1)           | 15.0.4003.23   | 2020-01-07   |
| [GDR1](#rtm)            | 15.0.2070.34  | 2019-11-04   |

## <a name="how-to-install-updates"></a>更新プログラムのインストール方法

更新プログラムをインストールする方法については、「[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]をアップグレードする方法](deployment-upgrade.md)」を参照してください。

## <a id="cu1"></a> CU1 (2020 年 1 月)

これは SQL Server 2019 の Cumulative Update 1 (CU1) リリースです。 このリリースに対する SQL Server データベース エンジンのバージョンは 15.0.4003.23 です。

|パッケージ バージョン | イメージ タグ |
|-----|-----|
|15.0.4003.23|[2019-CU1-ubuntu-16.04]

## <a id="rtm"></a> GDR1 (2019 年 11 月)

SQL Server 2019 一般配布リリース 1 (GDR1) で [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-nover.md)]の一般提供が開始されました。 このリリースの SQL Server データベース エンジンのバージョンは、15.0.2070.34 です。

|パッケージ バージョン | イメージ タグ |
|-----|-----|
|15.0.2070.34|[2019-GDR1-ubuntu-16.04]

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="known-issues"></a>既知の問題

### <a name="deployment-with-private-repository"></a>プライベート リポジトリを使用した展開

- **問題およびユーザーへの影響**:プライベート リポジトリからアップグレードする場合に特定の要件があります。

- **回避策**:プライベート リポジトリを使用して BDC を展開またはアップグレードするためにイメージを事前にプルする場合は、現在のビルド イメージとターゲット ビルド イメージがプライベート リポジトリ内にあることを確認します。 これにより、必要な場合に正常にロールバックすることが可能になります。 また、最初の展開以降にプライベート リポジトリの資格情報を変更した場合は、アップグレードする前に Kubernetes で対応するシークレットを更新します。 `azdata` では、`AZDATA_PASSWORD` と `AZDATA_USERNAME` の環境変数を使用した資格情報の更新はサポートされていません。 [`kubectl edit secrets`](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret) を使用してシークレットを更新します。 

別のリポジトリを使用した現在のビルドとターゲット ビルドのアップグレードはサポートされていません。

### <a name="upgrade-may-fail-due-to-timeout"></a>タイムアウトによりアップグレードが失敗することがある

- **問題およびユーザーへの影響**:タイムアウトによりアップグレードが失敗することがあります。

   次のコードにエラー例を示します。

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

   このエラーは、Azure Kubernetes Service (AKS) で BDC を更新した場合によく発生します。

- **回避策**:アップグレードのタイムアウトを増やします。 

   アップグレードのタイムアウトを増やすには、アップグレード構成マップを編集します。 アップグレード構成マップを編集するには:

   1. 次のコマンドを実行します。

      ```bash
      kubectl edit configmap controller-upgrade-configmap
      ```

   2.   次のフィールドを編集します。

       **`controllerUpgradeTimeoutInMinutes`** : コントローラーまたはコントローラー db のアップグレードが完了するまでの待機時間を分単位で指定します。 既定値は 5 です。 20 以上に更新します。

       **`totalUpgradeTimeoutInMinutes`** :コントローラーとコントローラー db の両方のアップグレード (コントローラー+ コラボレーション db のアップグレード) が完了するまでの合計時間を指定します。既定値は 10 です。 40 以上に更新します。

       **`componentUpgradeTimeoutInMinutes`** :これ以降のアップグレードの各フェーズの完了時間を指定します。  既定値は 30 です。 45 に更新します。

   3.   保存して終了

   別の方法として、次の Python スクリプトでタイムアウトを設定することも可能です。

   ```python
   from kubernetes import client, config
   import json

   def set_upgrade_timeouts(namespace, controller_timeout=20, controller_total_timeout=40, component_timeout=45):
       """ Set the timeouts for upgrades

       The timeout settings are as follows

       controllerUpgradeTimeoutInMinutes: sets the max amount of time for the controller
           or controllerdb to finish upgrading

       totalUpgradeTimeoutInMinutes: sets the max amount of time to wait for both the
           controller and controllerdb to complete their upgrade

       componentUpgradeTimeoutInMinutes: sets the max amount of time allowed for
           subsequent phases of the upgrade to complete
       """
       config.load_kube_config()

       upgrade_config_map = client.CoreV1Api().read_namespaced_config_map("controller-upgrade-configmap", namespace)

       upgrade_config = json.loads(upgrade_config_map.data["controller-upgrade"])

       upgrade_config["controllerUpgradeTimeoutInMinutes"] = controller_timeout

       upgrade_config["totalUpgradeTimeoutInMinutes"] = controller_total_timeout

       upgrade_config["componentUpgradeTimeoutInMinutes"] = component_timeout

       upgrade_config_map.data["controller-upgrade"] = json.dumps(upgrade_config)

       client.CoreV1Api().patch_namespaced_config_map("controller-upgrade-configmap", namespace, upgrade_config_map)
   ```

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Azure Data Studio (ADS) または curl からの Livy ジョブの送信が 500 エラーで失敗する

- **問題およびユーザーへの影響**:HA 構成で、Spark 共有リソース `sparkhead` が複数のレプリカで構成されています。 この場合、Azure Data Studio (ADS) または `curl` からの Livy ジョブの送信でエラーが発生する可能性があります。 確認するには、`sparkhead` ポッドに `curl` を実行すると、接続が拒否されます。 たとえば、`curl https://sparkhead-0:8998/` または `curl https://sparkhead-1:8998` によって 500 エラーが返されます。

   これは、次のシナリオで発生します。

   - 各 Zookeeper インスタンスの Zookeeper ポッドまたはプロセスが数回再起動します。
   - `sparkhead` ポッドと Zookeeper ポッド間のネットワーク接続が信頼できない場合。

- **回避策**:両方の Livy サーバーを再起動します。

   ```bash
   kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

   ```bash
   kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>可用性グループのマスター インスタンスの場合にメモリ最適化テーブルを作成する

- **問題およびユーザーへの影響**:可用性グループ データベース (リスナー) に接続するために公開されているプライマリ エンドポイントを使用して、メモリ最適化テーブルを作成することはできません。

- **回避策**:SQL Server マスター インスタンスが可用性グループの構成である場合にメモリ最適化テーブルを作成するには、新しい接続で作成されたセッションで、[SQL Server インスタンスに接続](deployment-high-availability.md#instance-connect)し、エンドポイントを公開し、SQL Server データベースに接続して、メモリ最適化テーブルを作成します。

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>外部テーブルの Active Directory 認証モードに挿入する

- **問題およびユーザーへの影響**:SQL Server マスター インスタンスが Active Directory 認証モードになっている場合、外部テーブルのうち少なくとも 1 つがストレージプール内にある場合に外部テーブルからのみ選択され、別の外部テーブルに挿入されるクエリでは、次のように返されます。

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **回避策**:次のいずれかの方法でクエリを変更します。 ストレージ プール テーブルをローカル テーブルに結合するか、最初にローカル テーブルに挿入し、ローカル テーブルからデータを読み取ってデータ プールに挿入します。

### <a name="transparent-data-encryption-capabilities-can-not-be-used-with-databases-that-are-part-of-the-availability-group-in-the-sql-server-master-instance"></a>Transparent Data Encryption 機能が、SQL Server のマスター インスタンスの可用性グループの一部であるデータベースで使用できない

- **問題およびユーザーへの影響**:HA 構成では、暗号化に使用されるマスター キーがレプリカごとに違うため、暗号化が有効になっているデータベースをフェールオーバー後に使用することはできません。 

- **回避策**:この問題の回避策はありません。 修正が適用されるまでは、この構成では暗号化を有効にしないことをお勧めします。

## <a name="next-steps"></a>次のステップ

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]の詳細については、[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]の概要](big-data-cluster-overview.md)に関するページを参照してください。
