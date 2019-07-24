---
title: Azdata のインストール
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) をインストールして管理するために azdata ツールをインストールする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9444842081456563f411ad618f32b8dbd59f7513
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426442"
---
# <a name="install-azdata-to-manage-sql-server-big-data-clusters"></a>SQL Server ビッグデータクラスターを管理するために azdata をインストールする

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、CTP 3.2 用の**azdata** Tool を Windows または Linux にインストールする方法について説明します。

## <a id="prerequisites"></a> 前提条件

**azdata**は Python で記述されたコマンドラインユーティリティで、クラスター管理者は REST api を使用してビッグデータクラスターをブートストラップし、管理することができます。 最低限必要な Python バージョンは v1.0 です。 また、 `pip` **azdata**ツールをダウンロードしてインストールするためにも使用する必要があります。 以下の手順は、Windows と Ubuntu の例を示しています。 他のプラットフォームに Python をインストールする方法については、 [python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)を参照してください。
また、最新バージョンの*要求*Python パッケージをインストールして更新する必要もあります。
```bash
pip3 install -U requests
```

> [!IMPORTANT]
> 新しいバージョンのビッグデータクラスターをインストールする場合は、 **azdata**をアップグレードして新しいリリースをインストールする*前に*、データをバックアップして古いクラスターを削除する必要があります。 詳細については、「[新しいリリースへのアップグレード](deployment-upgrade.md)」を参照してください。

## <a id="windows"></a>Windows azdata のインストール

1. Windows クライアントで、から[https://www.python.org/downloads/](https://www.python.org/downloads/)必要な Python パッケージをダウンロードします。 Python 3.5.3 以降では、Python をインストールするときに pip3 もインストールされます。 

   > [!TIP] 
   > Python3 をインストールするときに、**パス**に Python を追加することを選択します。 そうでない場合は、後で pip3 が配置されている場所を見つけて、**パス**に手動で追加することができます。

1. 新しい Windows PowerShell セッションを開き、Python で最新のパスを取得します。

1. 以前のリリースのツールがインストールされている場合 ( **mssqlctl**という名前の previosly)、 **azdata**の最新バージョンをインストールする前に、最初にアンインストールすることが重要です。

   CTP 3.1 またはそれ以下の場合は、次のコマンドを実行します。 コマンド`ctp3.1`内のを、アンインストールする**mssqlctl**のバージョンに置き換えます。 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. 以前のリリースの**azdata**がインストールされている場合は、最新バージョンをインストールする前に最初にアンインストールすることが重要です。

   CTP 3.2 以降の場合は、次のコマンドを実行します。 コマンド`ctp3.2`内のを、アンインストールする**azdata**のバージョンに置き換えます。

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. 次のコマンドを使用して**azdata**をインストールします。

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

## <a id="linux"></a>Linux azdata のインストール

Linux では、Python 3.5 をインストールしてから、pip をアップグレードする必要があります。 次の例は、Ubuntu で動作するコマンドを示しています。 その他の Linux プラットフォームについては、 [Python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)を参照してください。

1. 必要な Python パッケージをインストールします。

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Upgrade pip3:

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. 以前のリリースのツールがインストールされている場合 (以前は**mssqlctl**)、 **azdata**の最新バージョンをインストールする前に、最初にアンインストールすることが重要です。

   CTP 3.1 またはそれ以下の場合は、次のコマンドを実行します。 コマンド`ctp3.1`内のを、アンインストールする**mssqlctl**のバージョンに置き換えます。 

   ```powershell
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. 以前のリリースの**azdata**がインストールされている場合は、最新バージョンをインストールする前に最初にアンインストールすることが重要です。

   CTP 3.2 以降の場合は、次のコマンドを実行します。 コマンド`ctp3.2`内のを、アンインストールする**azdata**のバージョンに置き換えます。

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. 次のコマンドを使用して**azdata**をインストールします。

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!NOTE]
   > スイッチ`--user`により、azdata が Python ユーザーインストールディレクトリにインストールされます。 これは通常`~/.local/bin` 、Linux 上で行います。 このディレクトリをパスに追加するか、ユーザーインストールディレクトリに移動して`./azdata` 、そこからを実行します。

## <a name="next-steps"></a>次のステップ

ビッグデータクラスターの詳細については、「 [SQL Server 2019 ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
