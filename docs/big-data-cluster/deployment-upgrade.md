---
title: 新しいリリースにアップグレードする
titleSuffix: SQL Server big data clusters
description: '@No__t-0 (プレビュー) を新しいリリースにアップグレードする方法について説明します。'
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb1bf33c9ccb342e6afc4d22d67463791c0d67b6
ms.sourcegitcommit: 36c3ead6f2a3628f58040acf47f049f0b0957b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71688273"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>@No__t をアップグレードする方法-0

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server ビッグ データ クラスターを新しいリリースにアップグレードする方法に関するガイダンスを提供します。 この記事の手順は、具体的にはプレビュー リリース間でアップグレードする方法に適用されます。

## <a name="backup-and-delete-the-old-cluster"></a>以前のクラスターをバックアップして削除する

現時点では、ビッグ データ クラスターを新しいリリースにアップグレードする唯一の方法は、クラスターを手動で削除して再作成することです。 各リリースには、以前のバージョンと互換性のない @no__t 0 の一意のバージョンがあります。 また、古いクラスターで新しいノードにイメージをダウンロードする必要があった場合は、最新のイメージがクラスター上の古いイメージと互換性がない可能性があります。 最新のリリースにアップグレードするには、次の手順に従います。

1. 以前のクラスターを削除する前に、SQL Server マスター インスタンス上と HDFS 上のデータをバックアップします。 SQL Server マスター インスタンスの場合は、[SQL Server のバックアップと復元](data-ingestion-restore-database.md)を使用できます。 HDFS の場合、 [`curl` を使用してデータをコピーでき](data-ingestion-curl.md)ます。

1. `azdata delete cluster` コマンドを使用して、古いクラスターを削除します。

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > クラスターに一致する `azdata` のバージョンを使用します。 新しいバージョンの `azdata` を使用して古いクラスターを削除しないでください。

   > [!Note]
   > @No__t-0 コマンドを発行すると、その名前空間内に作成されたすべてのオブジェクトが、その名前空間自体ではなく、ビッグデータクラスター名で削除されます。 名前空間は、空で、他のアプリケーションが内に作成されていない限り、後続の配置に再利用できます。

1. CTP 3.2 より前では、`azdata` が `mssqlctl` と呼ばれていました。 以前のリリースの `mssqlctl` または `azdata` がインストールされている場合は、`azdata` の最新バージョンをインストールする前に、まずをアンインストールすることが重要です。

   CTP 2.3 以降の場合は、次のコマンドを実行します。 コマンドの `ctp3.1` を、アンインストールする `mssqlctl` のバージョンに置き換えます。 バージョンが CTP 3.1 より前の場合は、バージョン番号の前にダッシュ (例: `ctp-2.5`) を追加します。

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. @No__t-0 の最新バージョンをインストールします。 次のコマンドでは、リリース候補として `azdata` がインストールされます。

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > リリースごとに `azdata` のパスが変更されます。 @No__t-0 または `mssqlctl` を既にインストールしている場合でも、新しいクラスターを作成する前に、最新のパスからを再インストールする必要があります。

## <a id="azdataversion"></a> azdata のバージョンを確認する

新しいビッグデータクラスターをデプロイする前に、最新バージョンの `azdata` と `--version` パラメーターを使用していることを確認します。

```bash
azdata --version
```

## <a name="install-the-new-release"></a>新しいリリースをインストールする

前のビッグデータクラスターを削除し、最新の `azdata` をインストールしたら、現在の展開手順に従って、新しいビッグデータクラスターをデプロイします。 詳細については、「 [How to deploy [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] On Kubernetes](deployment-guidance.md)」を参照してください。 次に、必要なデータベースまたはファイルを復元します。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] とは](big-data-cluster-overview.md)」を参照してください。
