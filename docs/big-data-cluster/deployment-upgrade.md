---
title: 新しいリリースにアップグレードする
titleSuffix: SQL Server Big Data Clusters
description: SQL Server ビッグ データ クラスターを新しいリリースにアップグレードする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: afb12477dd220e71cf2cf97d6a13b54aa2d35be4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75831835"
---
# <a name="how-to-upgrade-big-data-clusters-2019"></a>[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]をアップグレードする方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

アップグレード パスは、SQL Server ビッグ データ クラスター (BDC) の現在のバージョンによって異なります。 一般配布リリース (GDR)、累積的な更新プログラム (CU)、または Quick Fix Engineering (QFE) 更新プログラムを含め、サポートされているリリースからアップグレードするには、インプレース アップグレードを行うことができます。 Customer Technology Preview (CTP) またはリリース候補バージョンの BDC からのインプレース アップグレードはサポートされていません。 クラスターを削除し、再作成する必要があります。 次のセクションでは、各シナリオの手順について説明します。

- [サポートされているリリースからのアップグレード](#upgrade-from-supported-release)
- [CTP またはリリース候補からの BDC 展開の更新](#update-a-bdc-deployment-from-ctp-or-release-candidate)

>[!NOTE]
>ビッグ データ クラスターの最初のサポートされるリリースは、SQL Server 2019 GDR1 です。

## <a name="upgrade-release-notes"></a>アップグレードのリリース ノート

次に進む前に、[既知の問題に関するアップグレードのリリース ノート](release-notes-big-data-cluster.md#known-issues)を確認します。

## <a name="upgrade-from-supported-release"></a>サポートされているリリースからのアップグレード

このセクションでは、SQL Server BDC を、サポートされているリリース (SQL Server 2019 GDR1 以降) から新しいサポートされているリリースにアップグレードする方法について説明します。

1. SQL Server マスター インスタンスをバックアップします。
2. HDFS をバックアップします。

   ```
   azdata bdc hdfs cp --from-path <path> --to-path <path>
   ```
   
   次に例を示します。 

   ```
   azdata bdc hdfs cp --from-path hdfs://user/hive/warehouse/%%D --to-path ./%%D
   ```

3. `azdata` を更新します。

   `azdata` のインストール手順に従います。 
   - [Windows インストーラー](deploy-install-azdata-installer.md)
   - [Linux (apt を使用)](deploy-install-azdata-linux-package.md)
   - [Linux (yum を使用)](deploy-install-azdata-yum.md)
   - [Linux (zypper を使用)](deploy-install-azdata-zypper.md)

   >[!NOTE]
   >`azdata` が `pip` と共にインストールされている場合は、Windows インストーラーまたは Linux パッケージ マネージャーを使ってインストールする前に、手動で削除する必要があります。

1. ビッグ データ クラスターを更新します。

   ```
   azdata bdc upgrade -n <clusterName> -t <imageTag> -r <containerRegistry>/<containerRepository>
   ```

   たとえば、次のスクリプトでは `2019-CU1-ubuntu-16.04` イメージ タグを使用しています。

   ```
   azdata bdc upgrade -n bdc -t 2019-CU1-ubuntu-16.04 -r mcr.microsoft.com/mssql/bdc
   ```

>[!NOTE]
>最新のイメージ タグは、[SQL Server 2019 ビッグ データ クラスターのリリース ノート](release-notes-big-data-cluster.md)で入手できます。

>[!IMPORTANT]
>プライベート リポジトリを使用して BDC を展開またはアップグレードするためにイメージを事前にプルする場合は、現在のビルド イメージとターゲット ビルド イメージがプライベート リポジトリ内にあることを確認します。 これにより、必要に応じて正常にロールバックすることができます。 また、元の展開以降にプライベート リポジトリの資格情報を変更した場合は、アップグレードする前に Kubernetes で対応するシークレットを更新します。 DOCKER_PASSWORD と DOCKER_USERNAME の環境変数を使用した資格情報の更新はサポートされていません。 シークレットを更新するには、[kubectl edit secrets](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret) を使用します。 現在のビルドとターゲット ビルドに異なるプライベート リポジトリを使用したアップグレードはサポートされていません。

### <a name="increase-the-timeout-for-the-upgrade"></a>アップグレードのタイムアウトを増やす

割り当てられた時間内に特定のコンポーネントがアップグレードされない場合、タイムアウトが発生する可能性があります。 次のコードは、エラーの例を示しています。

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

アップグレードのタイムアウトを増やすには、アップグレード構成マップを編集します。 アップグレード構成マップを編集するには:

次のコマンドを実行します。

   ```bash
   kubectl edit configmap controller-upgrade-configmap
   ```

次のフィールドを編集します。

   **controllerUpgradeTimeoutInMinutes** コントローラーまたはコントローラー db のアップグレードが完了するまでの待機時間を分単位で指定します。 既定値は 5 です。 20 以上に更新します。
   **totalUpgradeTimeoutInMinutes**:コントローラーとコントローラー db の両方のアップグレード (コントローラー+ コラボレーション db のアップグレード) が完了するまでの合計時間を指定します。既定値は 10 です。 40 以上に更新します。
   **componentUpgradeTimeoutInMinutes**:アップグレードの後続の各フェーズが完了するまでの時間を指定します。 既定値は 30 です。 45 に更新します。

保存して終了します。

## <a name="update-a-bdc-deployment-from-ctp-or-release-candidate"></a>CTP またはリリース候補からの BDC 展開の更新

SQL Server ビッグ データ クラスターの CTP またはリリース候補ビルドからのインプレース アップグレードはサポートされていません。 次のセクションでは、クラスターを手動で削除し、再作成する方法について説明します。

### <a name="backup-and-delete-the-old-cluster"></a>以前のクラスターをバックアップして削除する

SQL Server 2019 GDR1 リリースの前に展開されたビッグ データ クラスターのインプレース アップグレードはありません。 新しいリリースにアップグレードする唯一の方法は、クラスターを手動で削除して再作成することです。 各リリースには、以前のバージョンと互換性のない固有のバージョンの `azdata` があります。 また、別の以前のバージョンで展開されたクラスターに新しいコンテナー イメージをダウンロードした場合、最新のイメージはクラスター上の以前のイメージと互換性がない可能性があります。 コンテナー設定の展開構成ファイルで `latest` イメージ タグを使用している場合は、新しいイメージがプルされます。 既定では、各リリースには、SQl Server のリリース バージョンに対応する固有のイメージ タグがあります。 最新のリリースにアップグレードするには、次の手順に従います。

1. 以前のクラスターを削除する前に、SQL Server マスター インスタンス上と HDFS 上のデータをバックアップします。 SQL Server マスター インスタンスの場合は、[SQL Server のバックアップと復元](data-ingestion-restore-database.md)を使用できます。 HDFS の場合は、[`curl` を使用してデータをコピーできます](data-ingestion-curl.md)。

1. `azdata delete cluster` コマンドを使用して、古いクラスターを削除します。

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > クラスターと一致するバージョンの `azdata` を使用します。 新しいバージョンの `azdata` で古いクラスターを削除しないでください。

   > [!Note]
   > `azdata bdc delete` コマンドを発行すると、そのビッグ データ クラスター名で示される名前空間内で作成されたすべてのオブジェクトは削除されますが、名前空間自体は削除されません。 名前空間は、空で、他のアプリケーションが中に作成されていない限り、後の展開に再利用できます。

1. 以前のバージョンの `azdata` をアンインストールします。

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. 最新バージョンの `azdata` をインストールします。 次のコマンドでは、最新のリリースから `azdata` がインストールされます。

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > 各リリースで、`azdata` の `n-1` バージョンへのパスが変更されます。 以前に `azdata` をインストールしている場合でも、新しいクラスターを作成する前に、最新のパスから再インストールする必要があります。

### <a id="azdataversion"></a> azdata のバージョンを確認する

新しいビッグ データ クラスターを展開する前に、`--version` パラメーターを指定して、最新バージョンの `azdata` を使用していることを確認します。

```bash
azdata --version
```

### <a name="install-the-new-release"></a>新しいリリースをインストールする

以前のビッグ データ クラスターを削除し、最新の `azdata` をインストールしたら、現在の展開手順に従って、新しいビッグ データ クラスターを展開します。 詳細については、「[Kubernetes に [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]を展開する方法](deployment-guidance.md)」を参照してください。 次に、必要なデータベースまたはファイルを復元します。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] とは](big-data-cluster-overview.md)の概要に関するページを参照してください。
