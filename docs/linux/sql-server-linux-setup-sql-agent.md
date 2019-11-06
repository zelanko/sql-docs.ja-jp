---
title: Linux 上に SQL Server エージェントをインストールする
description: この記事では、Linux 上に SQL Server エージェントをインストールする方法について説明します。
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032467"
---
# <a name="install-sql-server-agent-on-linux"></a>Linux 上に SQL Server エージェントをインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [SQL Server エージェント](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)は、スケジュールされた SQL Server ジョブを実行します。 SQL Server 2017 CU4 以降、SQL Server エージェントは **mssql-Server** パッケージに含まれており、既定で無効になっています。 このリリースの SQL Server エージェントでサポートされている機能とバージョン情報については、[リリース ノート](sql-server-linux-release-notes.md)を参照してください。

 SQL Server エージェントをインストールする/有効にする:
- [2017 CU4 以降のバージョンで SQL Server エージェントを有効にする](#EnableAgentAfterCU4)
- [2017 CU3 以前のバージョンで SQL Server エージェントをインストールする](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">2017 CU4 以降のバージョンで SQL Server エージェントを有効にする</a>

 SQL Server エージェントを有効にするには、次の手順に従います。

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> エージェントがインストールされている 2017 CU3 以前からアップグレードすると、SQL Server エージェントが自動的に有効になり、前のエージェント パッケージはアンインストールされます。  

## <a name="InstallAgentBelowCU4">2017 CU3 以前のバージョンで SQL Server エージェントをインストールする</a>

> [!NOTE]
> 以下のインストール手順は SQL Server バージョン 2017 CU3 以前に適用されます。 SQL Server エージェントをインストールする前に、まず [SQL Server をインストール](sql-server-linux-setup.md#platforms)してください。 これにより **mssql-server-agent** パッケージをインストールするときに使用されるキーとリポジトリが構成されます。

お使いのプラットフォーム用の SQL Server エージェントをインストールします。
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">RHEL へのインストール</a>

次の手順を使用して、Red Hat Enterprise Linux に **mssql-server-agent** をインストールします。 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

既に **mssql-server-agent** がインストールされている場合は、次のコマンドを使用して最新バージョンに更新できます。

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合は、[リリース ノート](sql-server-linux-release-notes.md)の SQL Server エージェント パッケージのダウンロードを参照してください。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

### <a name="ubuntu">Ubuntu へのインストール</a>

次の手順を使用して、Ubuntu に **mssql-server-agent** をインストールします。 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

既に **mssql-server-agent** がインストールされている場合は、次のコマンドを使用して最新バージョンに更新できます。

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合は、[リリース ノート](sql-server-linux-release-notes.md)の SQL Server エージェント パッケージのダウンロードを参照してください。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

### <a name="SLES">SLES へのインストール</a>

次の手順を使用して、SUSE Linux Enterprise Server に **mssql-server-agent** をインストールします。 

**mssql-server-agent** をインストールします。 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

既に **mssql-server-agent** がインストールされている場合は、次のコマンドを使用して最新バージョンに更新できます。

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合は、[リリース ノート](sql-server-linux-release-notes.md)の SQL Server エージェント パッケージのダウンロードを参照してください。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

## <a name="next-steps"></a>次の手順
SQL Server エージェントを使用してジョブを作成、スケジュール設定、および実行する方法について詳しくは、[Linux 上での SQL Server エージェント ジョブの実行](sql-server-linux-run-sql-server-agent-job.md)に関するページをご覧ください。
