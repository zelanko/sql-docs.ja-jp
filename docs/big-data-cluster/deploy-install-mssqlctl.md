---
title: mssqlctl をインストールする
titleSuffix: SQL Server big data clusters
description: インストールして、SQL Server 2019 ビッグ データ クラスター (プレビュー) の管理の mssqlctl ツールをインストールする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9c35971c0c0acf69065734cdcdbe670710ef5e4
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582386"
---
# <a name="install-mssqlctl-to-manage-sql-server-big-data-clusters"></a>SQL Server のビッグ データ クラスターを管理する mssqlctl をインストールします。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事は、インストールする方法を説明します、 **mssqlctl** Windows または Linux でのツール。

**mssqlctl**は Python で記述された、により、クラスター管理者のブートス トラップし、REST Api を使用してビッグ データ クラスターを管理するコマンド ライン ユーティリティです。 必要な最小の Python バージョン v3.5 です。 必要がある`pip`をダウンロードしてインストールに使用される**mssqlctl**ツール。 以下の手順では、Windows および Ubuntu の例を紹介します。 他のプラットフォームで Python をインストールするため、次を参照してください。、 [Python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)します。

> [!IMPORTANT]
> データをバックアップし、以前のクラスターを削除する必要がありますビッグ データ クラスターの新しいバージョンをインストールする場合*する前に*アップグレード**mssqlctl**と新しいリリースをインストールします。 詳細については、次を参照してください。[新しいリリースにアップグレードする](deployment-guidance.md#upgrade)します。

## <a id="windows"></a> Windows mssqlctl インストール

1. Windows クライアントでは、上から必要な Python パッケージをダウンロード[ https://www.python.org/downloads/](https://www.python.org/downloads/)します。 Python3.5.3 以降、Python をインストールすると、pip3 もインストールします。 

   > [!TIP] 
   > Python を追加する選択を Python3 をインストールするときに、**パス**します。 そうでない場合は、pip3 がある場所を後で検索し、手動で追加して、**パス**します。

1. Python の使用が最新のパスを取得できるように、新しい Windows PowerShell セッションを開きます。

1. 以前のリリースがあれば**mssqlctl**をインストールすることが重要アンインストール**mssqlctl**最初、最新バージョンをインストールする前にします。

   CTP 2.2 またはそれ以下のバージョンに対応する unisntalling mssqlctl をする場合は次のコマンドを実行します。

   ```powershell
   pip3 uninstall mssqlctl
   ```

   CTP2.3 または高い実行 (置換`ctp-2.3`バージョンをアンインストールする mssqlctl のコマンドで)。

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt
   ```

## <a id="linux"></a> Linux mssqlctl のインストール

Linux は、Python 3.5 をインストールしてから pip をアップグレードする必要があります。 次の例では、Ubuntu で使用するコマンドを示します。 その他の Linux プラットフォームでは、次を参照してください。、 [Python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)します。

1. 必要な Python パッケージをインストールします。

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip
   ```

1. Pip3 をアップグレードします。

   ```bash
   sudo -H pip3 install --upgrade pip
   ```

1. 以前のリリースがあれば**mssqlctl**をインストールすることが重要アンインストール**mssqlctl**最初、最新バージョンをインストールする前にします。

   CTP 2.2 またはそれ以下のバージョンに対応する unisntalling mssqlctl をする場合は次のコマンドを実行します。

   ```bash
   pip3 uninstall mssqlctl
   ```

   CTP2.3 または高い実行 (置換`ctp-2.3`バージョンをアンインストールする mssqlctl のコマンドで)。

   ```bash
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt --user
   ```

   > [!NOTE]
   > `--user`スイッチ mssqlctl を Python のユーザーのインストール ディレクトリにインストールされます。 これは通常`~/.local/bin`Linux 上。 いずれか、パスにこのディレクトリを追加かユーザー インストール ディレクトリに移動して実行`./mssqlctl`そこから。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
