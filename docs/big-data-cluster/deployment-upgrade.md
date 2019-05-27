---
title: 新しいリリースにアップグレードする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) を新しいリリースにアップグレードする方法について説明します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 45c489d7bb2dc6f0fea5815dce4b2f0ef11ae5ad
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66015184"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>ビッグ データの SQL Server クラスターをアップグレードする方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、ビッグ データの SQL Server クラスターを新しいリリースにアップグレードする方法のガイダンスを提供します。 この記事の手順では、具体的には、プレビュー リリース間でアップグレードする方法に適用されます。

## <a name="backup-and-delete-the-old-cluster"></a>バックアップして、以前のクラスターの削除

現時点では、ビッグ データ クラスターを新しいリリースにアップグレードする唯一の方法は、手動で削除してクラスターを再作成します。 各リリースでは、一意のバージョンの**mssqlctl**ですが、以前のバージョンと互換性がありません。 また、古いクラスターを新しいノードにイメージをダウンロードする場合は、最新のイメージ可能性がありますと互換性がない、クラスター上で古いイメージ。 最新のリリースにアップグレードするには、次の手順を使用します。

1. 以前のクラスターを削除する前に、HDFS と SQL Server のマスター インスタンスにデータをバックアップします。 使用することができます、SQL Server のマスター インスタンスの[SQL Server のバックアップと復元](data-ingestion-restore-database.md)します。 HDFS のする[を使用してデータをコピーできます**curl**](data-ingestion-curl.md)します。

1. 以前のクラスターを削除、`mssqlctl delete cluster`コマンド。

   ```bash
    mssqlctl cluster delete --name <old-cluster-name>
   ```

   > [!Important]
   > バージョンを使用して、 **mssqlctl**クラスターに一致します。 新しいバージョンので、古いクラスターを削除しないでください**mssqlctl**します。

1. 以前のリリースがあれば**mssqlctl**をインストールすることが重要アンインストール**mssqlctl**最初、最新バージョンをインストールする前にします。

   アンインストールする場合は**mssqlctl** CTP 2.2] または [下の実行に対応します。

   ```powershell
   pip3 uninstall mssqlctl
   ```

   CTP 2.3 以降、次のコマンドを実行します。 置換`ctp-2.5`のバージョンでのコマンドで**mssqlctl**アンインストールします。

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.5/mssqlctl/requirements.txt
   ```

1. 最新バージョンのインストール**mssqlctl**します。 次のコマンド インストール**mssqlctl** CTP 3.0。

   **Windows:**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

   **Linux の場合:**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > 各リリースへのパス**mssqlctl**変更します。 以前にインストールした場合でも**mssqlctl**、新しいクラスターを作成する前に最新のパスから再インストールする必要があります。

## <a id="mssqlctlversion"></a> Mssqlctl バージョンを確認します。

新しいビッグ データ クラスターをデプロイする前に、最新バージョンを使用していることを確認します**mssqlctl**で、`--version`パラメーター。

```bash
mssqlctl --version
```

## <a name="install-the-new-release"></a>新しいリリースをインストールします。

前のビッグ データ クラスターを削除して、最新版のインストール後に**mssqlctl**、現在のデプロイの手順を使用して新しいビッグ データ クラスターをデプロイします。 詳細については、次を参照してください。[ビッグ データの SQL Server をデプロイする方法を Kubernetes クラスターの](deployment-guidance.md)します。 次に、任意の必要なデータベースまたはファイルを復元します。

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server のビッグ データ クラスターは](big-data-cluster-overview.md)します。
