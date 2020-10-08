---
title: azdata をインストールする
titleSuffix: ''
description: azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 83da4e1554e1a6fa112c6fc8f629d30cbcb97d4d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725257"
---
# <a name="install-azdata"></a>`azdata` のインストール

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

`azdata` は、REST API 経由でデータ サービスをブートストラップし管理できる、Python で記述されたコマンドライン ユーティリティです。 

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

ビッグ データ クラスターで azdata を使用する方法については、「[[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)] とは](../../big-data-cluster/big-data-cluster-overview.md)」を参照してください。

[Azure Arc 対応データ サービス](/azure/azure-arc/data/)で azdata を使用する
