---
title: "Linux 上の SQL Server エージェントのインストール |Microsoft ドキュメント"
description: "この記事では、Linux に SQL Server エージェントをインストールする方法について説明します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.workload: On Demand
ms.openlocfilehash: 7db50a59a4a6ce9ab7aa416e4ac8d597449541b7
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="install-sql-server-agent-on-linux"></a>Linux 上の SQL Server エージェントをインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次の手順は、SQL Server エージェントをインストール (**mssql server エージェント**) on Linux です。 [SQL Server エージェント](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)SQL Server のスケジュールされたジョブを実行します。 SQL Server エージェントのこのリリースでサポートされる機能については、次を参照してください。、 [Release Notes](sql-server-linux-release-notes.md)です。

> [!NOTE]
> まず、SQL Server エージェントをインストールする前に[インストールの SQL Server 2017](sql-server-linux-setup.md#platforms)です。 これにより、キーとリポジトリをインストールするときに使用する構成、 **mssql server エージェント**パッケージです。

プラットフォームの SQL Server エージェントをインストールします。

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">RHEL をインストールします。</a>

インストールする次の手順を使用して、 **mssql server エージェント**Red Hat Enterprise Linux にします。 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

既に存在する場合**mssql server エージェント**インストールされている、次のように、次のコマンドで最新バージョンに更新できます。

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

オフラインでインストールする場合は、検索で SQL Server エージェントのパッケージのダウンロード、[リリース ノート](sql-server-linux-release-notes.md)です。 記事で説明されている同じ、オフライン インストール手順に従って[SQL Server のインストール](sql-server-linux-setup.md#offline)です。

## <a name="ubuntu">Ubuntu をインストールします。</a>

インストールする次の手順を使用して、 **mssql server エージェント**Ubuntu でします。 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

既に存在する場合**mssql server エージェント**インストールされている、次のように、次のコマンドで最新バージョンに更新できます。

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

オフラインでインストールする場合は、検索で SQL Server エージェントのパッケージのダウンロード、[リリース ノート](sql-server-linux-release-notes.md)です。 記事で説明されている同じ、オフライン インストール手順に従って[SQL Server のインストール](sql-server-linux-setup.md#offline)です。

## <a name="SLES">SLES をインストールします。</a>

インストールする次の手順を使用して、 **mssql server エージェント**SUSE Linux Enterprise Server にします。 

インストール**mssql server エージェント** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

既に存在する場合**mssql server エージェント**インストールされている、次のように、次のコマンドで最新バージョンに更新できます。

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

オフラインでインストールする場合は、検索で SQL Server エージェントのパッケージのダウンロード、[リリース ノート](sql-server-linux-release-notes.md)です。 記事で説明されている同じ、オフライン インストール手順に従って[SQL Server のインストール](sql-server-linux-setup.md#offline)です。

## <a name="next-steps"></a>次の手順
SQL Server エージェントを使用して、作成、スケジュール、およびジョブを実行する方法の詳細については、次を参照してください。 [Linux に SQL Server エージェント ジョブを実行](sql-server-linux-run-sql-server-agent-job.md)です。
