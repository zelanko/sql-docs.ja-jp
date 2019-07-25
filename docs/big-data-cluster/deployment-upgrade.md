---
title: 新しいリリースにアップグレードする
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグデータクラスター (プレビュー) を新しいリリースにアップグレードする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7bdb1eb59fd36d065df9dba0f6d6879c1a294914
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419387"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>ビッグデータクラスター SQL Server アップグレードする方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server ビッグデータクラスターを新しいリリースにアップグレードする方法に関するガイダンスを提供します。 この記事の手順は、プレビューリリース間でアップグレードする方法に特に当てはまります。

## <a name="backup-and-delete-the-old-cluster"></a>以前のクラスターをバックアップして削除する

現時点では、ビッグデータクラスターを新しいリリースにアップグレードする唯一の方法は、クラスターを手動で削除して再作成することです。 各リリースには、以前のバージョンと互換性のない**azdata**の一意のバージョンがあります。 また、古いクラスターで新しいノードのイメージをダウンロードする必要があった場合は、最新のイメージがクラスター上の古いイメージと互換性がない可能性があります。 最新のリリースにアップグレードするには、次の手順を使用します。

1. 以前のクラスターを削除する前に、SQL Server マスターインスタンスと HDFS にデータをバックアップします。 SQL Server master インスタンスでは、 [SQL Server のバックアップと復元](data-ingestion-restore-database.md)を使用できます。 HDFS の場合は、 [ **curl**を使用してデータをコピーでき](data-ingestion-curl.md)ます。

1. `azdata delete cluster`コマンドを使用して、古いクラスターを削除します。

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > クラスターに一致する**azdata**のバージョンを使用します。 古いクラスターは、新しいバージョンの**azdata**では削除しないでください。

1. CTP 3.2 より前では、 **azdata**は**mssqlctl**と呼ばれていました。 以前のリリースの**mssqlctl**または**azdata**がインストールされている場合は、 **azdata**の最新バージョンをインストールする前に、まずをアンインストールすることが重要です。

   CTP 2.3 以降の場合は、次のコマンドを実行します。 コマンド`ctp3.1`内のを、アンインストールする**mssqlctl**のバージョンに置き換えます。 バージョンが CTP 3.1 より前である場合は、バージョン番号の前にダッシュ ( `ctp-2.5`など) を追加します。

   ```powershell
   pip3 uninstall -r https://mcr.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. **Azdata**の最新バージョンをインストールします。 次のコマンドを実行すると、CTP 3.2 の**azdata**がインストールされます。

   **ウィンドウ**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **マシン**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > 各リリースで、 **azdata**へのパスが変更されます。 **Azdata**または**mssqlctl**を以前にインストールした場合でも、新しいクラスターを作成する前に、最新のパスからを再インストールする必要があります。

## <a id="azdataversion"></a>Azdata バージョンを確認する

新しいビッグデータクラスターをデプロイする前に、パラメーターを指定し`--version`て最新バージョンの**azdata**を使用していることを確認します。

```bash
azdata --version
```

## <a name="install-the-new-release"></a>新しいリリースをインストールする

前のビッグデータクラスターを削除し、最新の**azdata**をインストールしたら、現在のデプロイ手順に従って、新しいビッグデータクラスターをデプロイします。 詳細については、「 [How to deploy SQL Server big data クラスター on The Kubernetes](deployment-guidance.md)」を参照してください。 次に、必要なデータベースまたはファイルを復元します。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [SQL Server ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
