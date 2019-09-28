---
title: インストーラーを使用して azdata を Linux にインストールする
titleSuffix: SQL Server big data clusters
description: インストーラー (Linux) を使用して [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (プレビュー) をインストールして管理するための azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2795178cb975ecb620528c4a5dc8715b70d447fd
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342006"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Linux で [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] を管理するには `azdata` をインストールします

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Linux で SQL Server 2019 ビッグデータクラスターリリース候補の `azdata` をインストールする方法について説明します。 これらのパッケージマネージャーを使用できるようにするには、`azdata` のインストール `pip` が必要です。

パッケージマネージャーは、さまざまなオペレーティングシステムおよびディストリビューション向けに設計されています。

- Linux (Ubuntu) の場合は、 [`apt` を使用して `azdata` をインストール](#azdata-apt)します。

現時点では、他のオペレーティングシステムまたはディストリビューションに @no__t 0 をインストールするパッケージマネージャーはありません。 これらのプラットフォームについては、「[パッケージマネージャーを使用しない `azdata` のインストール](./deploy-install-azdata.md)」を参照してください。

## <a id="linux"></a>Linux 用の `azdata` のインストール

@no__t 0 のインストールパッケージは、`apt` の Ubuntu で使用できます。

### <a id="azdata-apt"></a>Apt (Ubuntu) を使用して `azdata` をインストールする

>[!NOTE]
>@No__t 0 のパッケージは、システム Python を使用せず、独自の Python インタープリターをインストールします。

1. インストールプロセスに必要なパッケージを取得します。

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. 署名キーをダウンロードしてインストールします。

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. @No__t 0 のリポジトリ情報を追加します。

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. リポジトリ情報を更新して `azdata` をインストールします。

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. インストールの確認:

    ```bash
    azdata --version
    ```

### <a name="update"></a>更新

@No__t-0 のみをアップグレードします。

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>アンインストール

1. Apt を使用したアンインストール-削除:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. @No__t 0 のリポジトリ情報を削除します。

    >[!NOTE]
    >今後 `azdata` をインストールする予定の場合、この手順は必要ありません。

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. 署名キーを削除します。

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Azdata CLI を使用してインストールされた、不要な依存関係を削除します。

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] とは](big-data-cluster-overview.md)」を参照してください。
