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
ms.openlocfilehash: dbb484c6858e9024fdbbaa4d12c15480d7314bc9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784273"
---
# <a name="install-azdata"></a>`azdata` のインストール

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

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
