---
title: インストーラーを使用して azdata を Linux にインストールする
titleSuffix: SQL Server big data clusters
description: SQL Server ビッグ データ クラスターをインストールおよび管理するためにインストーラー (Linux) を使用して azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ac50d0c20f76e78aaa5016f62cefb8c7cc7f075a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75728583"
---
# <a name="install-azdata-with-apt"></a>apt での `azdata` のインストール

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Linux に SQL Server 2019 ビッグ データ クラスター用の `azdata` をインストールする方法について説明します。 これらのパッケージ マネージャーが使用可能になる前は、`azdata` をインストールするために `pip` が必要でした。

[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-azdata-for-linux"></a><a id="linux"></a>Linux 用の `azdata` をインストールする

Ubuntu で使用可能な `azdata` インストール パッケージは `apt` を使用して入手できます。

### <a name="install-azdata-with-apt-ubuntu"></a><a id="azdata-apt"></a>apt (Ubuntu) を使用して `azdata` をインストールする

>[!NOTE]
>`azdata` パッケージでは、システム Python は使用されず、独自の Python インタープリターがインストールされます。

1. インストール プロセスに必要なパッケージを取得します。

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
    ```

2. 署名キーをダウンロードし、インストールします。

    ```bash
    curl -sL https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
    ```

3. `azdata` リポジトリ情報を追加します。

   Ubuntu 16.04 クライアントには次を実行します。
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
    ```

   Ubuntu 18.04 クライアントには次を実行します。
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"
    ```

4. リポジトリ情報を更新し、`azdata` をインストールします。

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. インストールを確認します。

    ```bash
    azdata --version
    ```

### <a name="update"></a>更新

`azdata` のみをアップグレードします。

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>アンインストール

1. apt-get remove を使用してアンインストールします。

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. `azdata` リポジトリ情報を削除します。

    >[!NOTE]
    >今後 `azdata` をインストールする予定がある場合、この手順は必要ありません

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

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、「[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]とは](big-data-cluster-overview.md)」を参照してください。
