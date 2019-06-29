---
title: mssqlctl をインストールする
titleSuffix: SQL Server big data clusters
description: インストールして、SQL Server 2019 ビッグ データ クラスター (プレビュー) の管理の mssqlctl ツールをインストールする方法について説明します。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 31167ae419c98fcd0166b1bd8056ea0d7976b674
ms.sourcegitcommit: 9d3ece500fa0e4a9f4fefc88df4af1db9431c619
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463449"
---
# <a name="install-mssqlctl-to-manage-sql-server-big-data-clusters"></a>SQL Server のビッグ データ クラスターを管理する mssqlctl をインストールします。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事は、インストールする方法を説明します、 **mssqlctl** Windows または Linux に CTP 3.1 用ツール。

**mssqlctl**は Python で記述された、により、クラスター管理者のブートス トラップし、REST Api を使用してビッグ データ クラスターを管理するコマンド ライン ユーティリティです。 必要な最小の Python バージョン v3.5 です。 必要がある`pip`をダウンロードしてインストールに使用される**mssqlctl**ツール。 以下の手順では、Windows および Ubuntu の例を紹介します。 他のプラットフォームで Python をインストールするため、次を参照してください。、 [Python のドキュメント](https://wiki.python.org/moin/BeginnersGuide/Download)します。

> [!IMPORTANT]
> データをバックアップし、以前のクラスターを削除する必要がありますビッグ データ クラスターの新しいバージョンをインストールする場合*する前に*アップグレード**mssqlctl**と新しいリリースをインストールします。 詳細については、次を参照してください。[新しいリリースにアップグレードする](deployment-upgrade.md)します。

## <a id="windows"></a> Windows mssqlctl インストール

1. Windows クライアントでは、上から必要な Python パッケージをダウンロード[ https://www.python.org/downloads/](https://www.python.org/downloads/)します。 Python3.5.3 以降、Python をインストールすると、pip3 もインストールします。 

   > [!TIP] 
   > Python を追加する選択を Python3 をインストールするときに、**パス**します。 そうでない場合は、pip3 がある場所を後で検索し、手動で追加して、**パス**します。

1. Python の使用が最新のパスを取得できるように、新しい Windows PowerShell セッションを開きます。

1. 以前のリリースがあれば**mssqlctl**をインストールすることが重要アンインストール**mssqlctl**最初、最新バージョンをインストールする前にします。

   アンインストールする場合は**mssqlctl** CTP 2.2 またはそれ以下のバージョンに対応するを実行します。

   ```powershell
   pip3 uninstall mssqlctl
   ```

   CTP 2.3 以降、次のコマンドを実行します。 置換`ctp3.0`のバージョンでのコマンドで**mssqlctl**アンインストールします。 CTP 3.0 より前のバージョンの場合は、追加のバージョン番号の前にダッシュ (たとえば、 `ctp-2.5`)。

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
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

   アンインストールする場合は**mssqlctl** CTP 2.2 またはそれ以下のバージョンに対応するを実行します。

   ```powershell
   pip3 uninstall mssqlctl
   ```

   CTP 2.3 以降、次のコマンドを実行します。 置換`ctp3.0`のバージョンでのコマンドで**mssqlctl**アンインストールします。 CTP 3.0 より前のバージョンの場合は、追加のバージョン番号の前にダッシュ (たとえば、 `ctp-2.5`)。

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. インストール**mssqlctl**次のコマンドを使用します。

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt --user
   ```

   > [!NOTE]
   > `--user`スイッチ mssqlctl を Python のユーザーのインストール ディレクトリにインストールされます。 これは通常`~/.local/bin`Linux 上。 いずれか、パスにこのディレクトリを追加かユーザー インストール ディレクトリに移動して実行`./mssqlctl`そこから。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
