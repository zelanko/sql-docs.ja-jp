---
title: yum を使用した azdata のインストール
titleSuffix: SQL Server big data clusters
description: yum を使用して、ビッグ データ クラスターをインストールおよび管理する azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cf6e061b0ca4fca7c843575a87038a801ab8f758
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75728553"
---
# <a name="install-azdata-with-yum"></a>yum での `azdata` のインストール

`yum` を使用した Linux ディストリビューションには、`azdata-cli` 用のパッケージが用意されています。 この CLI パッケージは、`yum` を使用する Linux バージョンでテストされています。

- RHEL 7、RHEL 8


[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-yum"></a>yum でのインストール

>[!IMPORTANT]
> `azdata-cli` の RPM パッケージは、python3 のパッケージによって異なります。 これは、お使いのシステムでは *Python 3.6.x* の要件より前から存在する Python バージョンである可能性があります。 これが問題となる場合、代わりの python3 パッケージを見つけるか、[`pip`](deploy-install-azdata-pip.md) を使用する手動でのインストール手順に従ってください。

1. Microsoft リポジトリ キーをインポートします

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. ローカル リポジトリ情報を作成します

   RHEL 7 クライアントには次を実行します。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo
   ```
  
   RHEL 8 クライアントには次を実行します。

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo
   ```

1. `yum install` コマンドを使用してインストールします

   ```bash
   sudo yum install azdata-cli
   ```

## <a name="verify-install"></a>インストールの確認

```
azdata
azdata --version
```

## <a name="update"></a>更新

`yum update` コマンドで `azdata-cli` を更新します。

```bash
sudo yum update azdata-cli
```

## <a name="uninstall"></a>アンインストール

1. システムからのパッケージを削除します

   ```bash
   sudo yum remove azdata-cli
   ```

1. `azdata-cli` を再インストールする予定がない場合は、リポジトリ情報を削除します

   ```bash
   sudo rm /etc/yum.repos.d/azdata-cli.repo
   ```

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、「[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]とは](big-data-cluster-overview.md)」を参照してください。
