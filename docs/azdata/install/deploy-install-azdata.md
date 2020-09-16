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
ms.openlocfilehash: 408dec76480a36ff2280926147b948859fa7088d
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733897"
---
# <a name="install-azdata"></a>`azdata` のインストール

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

`azdata` は、REST API 経由でビッグ データ クラスターをブートストラップし管理できる、Python で記述されたコマンドライン ユーティリティです。 

## <a name="find-latest-version"></a>最新バージョンを探す

最新バージョンのファイル一覧は、常に [https://aka.ms/azdata](https://aka.ms/azdata) にあります。

インストール済みのバージョンを見つけ、更新する必要があるかどうかを確認するには、`azdata --version` を実行します。

## <a name="os-specific-instructions"></a>OS 固有の手順

* [Windows へのインストール](../install/deploy-install-azdata-installer.md)
* [macOS へのインストール](../install/deploy-install-azdata-macos.md)
* Linux または [Windows Subsystem for Linux (WSL)](/windows/wsl/about/) へのインストール
   * [Debian または Ubuntu での apt を使用したインストール](../install/deploy-install-azdata-linux-package.md)
   * [RHEL または CentOS での yum を使用したインストール](../install/deploy-install-azdata-yum.md)
   * [openSUSE または SLE での Zypper を使用したインストール](../install/deploy-install-azdata-zypper.md)
   * [スクリプトからのインストール](../install/deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、「[[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]とは](../../big-data-cluster/big-data-cluster-overview.md)」を参照してください。
