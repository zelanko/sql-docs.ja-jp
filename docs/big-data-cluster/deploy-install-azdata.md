---
title: azdata をインストールする
titleSuffix: SQL Server big data clusters
description: ビッグ データ クラスターをインストールおよび管理する azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 40338c4083241fedd113bca3a1beb839dbdd3fca
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75721737"
---
# <a name="install-azdata"></a>`azdata` のインストール

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

`azdata` は、REST API 経由でビッグ データ クラスターをブートストラップし管理できる、Python で記述されたコマンドライン ユーティリティです。 

## <a name="find-latest-version"></a>最新バージョンを探す

最新バージョンのファイル一覧は、常に [https://aka.ms/azdata](https://aka.ms/azdata) にあります。

インストール済みのバージョンを見つけ、更新する必要があるかどうかを確認するには、`azdata --version` を実行します。

## <a name="os-specific-instructions"></a>OS 固有の手順

* [Windows へのインストール](deploy-install-azdata-installer.md)
* [macOS へのインストール](deploy-install-azdata-macos.md)
* Linux または [Windows Subsystem for Linux (WSL)](/windows/wsl/about/) へのインストール
   * [Debian または Ubuntu での apt を使用したインストール](deploy-install-azdata-linux-package.md)
   * [RHEL または CentOS での yum を使用したインストール](deploy-install-azdata-yum.md)
   * [openSUSE または SLE での Zypper を使用したインストール](deploy-install-azdata-zypper.md)
   * [スクリプトからのインストール](deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、「[[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]とは](big-data-cluster-overview.md)」を参照してください。
