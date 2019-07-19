---
title: Linux 上の SQL Server エージェントをインストールします。
description: この記事では、Linux に SQL Server エージェントをインストールする方法について説明します。
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032467"
---
# <a name="install-sql-server-agent-on-linux"></a>Linux 上の SQL Server エージェントをインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 [SQL Server エージェント](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)は SQL Server のスケジュールされたジョブを実行します。 SQL Server 2017 CU4 以降、SQL Server エージェントが付属、 **mssql server**パッケージ化し、既定で無効にします。 このリリースのバージョン情報と共に SQL Server エージェントのサポートされる機能については、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)します。

 SQL Server エージェントのインストール/有効化。
- [バージョン 2017 CU4 以降では、SQL Server エージェントを有効にします。](#EnableAgentAfterCU4)
- [バージョン 2017 CU3 と以下では、SQL Server エージェントをインストールします。](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">バージョン 2017 CU4 以降では、SQL Server エージェントを有効にします。</a>

 SQL Server エージェントを有効にするには、次の手順に従います。

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> 2017 CU3 からアップグレードするか下でエージェントをインストールするには、SQL Server エージェントが自動的に有効な以前の場合は、エージェント パッケージがアンインストールされます。  

## <a name="InstallAgentBelowCU4">バージョン 2017 CU3 と以下では、SQL Server エージェントをインストールします。</a>

> [!NOTE]
> SQL Server のバージョン 2017 CU3 と下、次のインストール手順が適用されます。 まず、SQL Server エージェントをインストールする前に[SQL Server インストール](sql-server-linux-setup.md#platforms)します。 これは、キーとをインストールするときに使用するリポジトリを構成します、 **mssql server エージェント**パッケージ。

お使いのプラットフォームの SQL Server エージェントをインストールします。
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">RHEL へのインストール</a>

次の手順を使用してインストールする、 **mssql server エージェント**Red Hat Enterprise linux。 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

既にある場合**mssql server エージェント**インストールされている場合、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合に、SQL Server エージェント パッケージのダウンロードを検索、[リリース ノート](sql-server-linux-release-notes.md)します。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

### <a name="ubuntu">Ubuntu にインストールします</a>

次の手順を使用してインストールする、 **mssql server エージェント**ubuntu の場合。 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

既にある場合**mssql server エージェント**インストールされている場合、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合に、SQL Server エージェント パッケージのダウンロードを検索、[リリース ノート](sql-server-linux-release-notes.md)します。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

### <a name="SLES">SLES へのインストール</a>

次の手順を使用してインストールする、 **mssql server エージェント**SUSE Linux Enterprise server。 

インストール**mssql server エージェント** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

既にある場合**mssql server エージェント**インストールされている場合、次のように次のコマンドで最新バージョンに更新できます。

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

オフライン インストールが必要な場合に、SQL Server エージェント パッケージのダウンロードを検索、[リリース ノート](sql-server-linux-release-notes.md)します。 次に、[SQL Server のインストール](sql-server-linux-setup.md#offline)の記事で説明されているのと同じオフライン インストール手順を使用します。

## <a name="next-steps"></a>次の手順
SQL Server エージェントを使用して、作成、スケジュール、およびジョブを実行する方法の詳細については、次を参照してください。 [Linux 上の SQL Server エージェント ジョブの実行](sql-server-linux-run-sql-server-agent-job.md)します。
