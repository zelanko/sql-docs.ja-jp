---
title: macOS 用の azdata のインストール
titleSuffix: SQL Server big data clusters
description: macOS 用のビッグ データ クラスターをインストールおよび管理する azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f6662a5ff7ced4c260e2b1a3fbd1efe5a285cf4a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733870"
---
# <a name="install-azdata-on-macos"></a>`azdata` の macOS へのインストール

`azdata-cli` は、macOS プラットフォームには、Homebrew パッケージ マネージャーでインストールできます。 この CLI パッケージは、macOS の次のバージョンでテストされています。 
* 10.13 High Sierra
* 10.14 Mojave
* 10.15 Catalina

## <a name="install-with-homebrew"></a>Homebrew でインストールする

```bash
brew tap microsoft/azdata-cli-release
brew update
brew install azdata-cli
```

>[!IMPORTANT]
>`azdata-cli` は Homebrew の `python3`、`freetds`、`unixodbc`、`zeromq` パッケージに依存しており、それらをインストールします。 `azdata-cli` は、Homebrew で公開されるこれらの依存関係の最新バージョンとの互換性が保証されています。

## <a name="verify-install"></a>インストールの確認

```bash
azdata
azdata --version
```

## <a name="update"></a>更新

ローカル リポジトリ情報を更新してから、`azdata-cli` パッケージをアップグレードします。

```bash
brew tap microsoft/azdata-cli-release
brew update
brew upgrade azdata-cli
```

## <a name="uninstall"></a>アンインストール

Homebrew を使用して、`azdata-cli` パッケージをアンインストールします。

```bash
brew uninstall azdata-cli
```

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターの詳細については、「[[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]とは](../../big-data-cluster/big-data-cluster-overview.md)」を参照してください。