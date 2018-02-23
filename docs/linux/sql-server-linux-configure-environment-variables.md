---
title: "環境変数と SQL Server の設定を構成する |Microsoft ドキュメント"
description: "この記事では、環境変数を使用して、Linux の特定の SQL Server 2017 設定を構成する方法について説明します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.workload: On Demand
ms.openlocfilehash: e6d21c8f2e7636ee787bbd735b3d69b71ac20671
ms.sourcegitcommit: 57f45ee008141ddf009b1c1195442529e0ea1508
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2018
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Linux 上の環境変数と SQL Server の設定を構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

いくつかの別の環境変数を使用して、Linux 上の SQL Server 2017 を構成することができます。 これらの変数は、2 つのシナリオで使用されます。

- 初期セットアップの構成、`mssql-conf setup`コマンド。
- 新しい構成を[Docker でコンテナーを SQL Server](quickstart-install-connect-docker.md)です。

> [!TIP]
> これらのシナリオのセットアップ後に SQL Server を構成する必要がある場合は、次を参照してください。 [mssql conf ツールを使用して Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

## <a name="environment-variables"></a>環境変数

| 環境変数 | Description |
|-----|-----|
| **ACCEPT_EULA** | 任意の値 (たとえば、' Y') に設定すると SQL Server のライセンス契約に同意します。 |
| **MSSQL_SA_PASSWORD** | SA パスワードを構成します。 |
| **MSSQL_PID** | SQL Server のエディションまたはプロダクト キーを設定します。 有効な値は次のとおりです。 </br></br>**Evaluation**</br>**開発者**</br>**Express**</br>Web</br>**Standard**</br>**Enterprise**</br>**プロダクト キー**</br></br>プロダクト キーを指定する場合は、###-###-###-###-###、ここで、'#' は、数または文字の形式でなければなりません。|
| **MSSQL_LCID** | SQL Server に使用する言語 ID を設定します。 たとえば 1036 はフランス語です。 |
| **MSSQL_COLLATION** | SQL Server の既定の照合順序を設定します。 照合順序には、言語 id (LCID) の既定のマッピングが上書きされます。 |
| **MSSQL_MEMORY_LIMIT_MB** | 最大メモリ (MB) SQL Server が使用できる量を設定します。 既定では、合計物理メモリの 80% を勧めします。 |
| **MSSQL_TCP_PORT** | SQL Server が (既定は 1433) をリッスンする TCP ポートを構成します。 |
| **MSSQL_IP_ADDRESS** | IP アドレスを設定します。 現時点では、IP アドレスは IPv4 スタイル (0.0.0.0) にする必要があります。 |
| **MSSQL_BACKUP_DIR** | 既定のバックアップ ディレクトリの場所を設定します。 |
| **MSSQL_DATA_DIR** | 新しい SQL Server データベース データ ファイル (.mdf) の作成元ディレクトリを変更します。 |
| **MSSQL_LOG_DIR** | 新しい SQL Server データベースのログ (.ldf) ファイルが作成されるディレクトリを変更します。 |
| **MSSQL_DUMP_DIR** | ここで SQL Server が預金メモリ ダンプおよびその他のトラブルシューティング ファイル既定では、ディレクトリを変更します。 |
| **MSSQL_ENABLE_HADR** | 可用性グループを有効にします。 たとえば、'1' が有効になっているし、'0' が無効になっています |
| **MSSQL_AGENT_ENABLED** | SQL Server エージェントを有効にします。 たとえば、'true' が有効で、'false' は無効になっています。 既定では、エージェントが無効です。  |
| **MSSQL_MASTER_DATA_FILE** | Master データベースのデータ ファイルの場所を設定します。 |
| **MSSQL_MASTER_LOG_FILE** | Master データベース ログ ファイルの場所を設定します。 |


## <a name="example-initial-setup"></a>例: 初回セットアップ

この例では実行`mssql-conf setup`で環境変数を構成します。 次の環境変数が指定されます。

- **ACCEPT_EULA**使用許諾契約書を受け入れます。
- **MSSSQL_PID**自由にライセンス Developer Edition の SQL Server の非運用環境を指定します。
- **MSSQL_SA_PASSWORD**強力なパスワードを設定します。
- **MSSQL_TCP_PORT** 1234 に SQL Server がリッスンする TCP ポートを設定します。

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="example-docker"></a>例: Docker

この例の docker コマンドでは、次の環境変数を使用して、新しい SQL Server 2017 コンテナーを作成します。

- **ACCEPT_EULA**使用許諾契約書を受け入れます。
- **MSSSQL_PID**自由にライセンス Developer Edition の SQL Server の非運用環境を指定します。
- **MSSQL_SA_PASSWORD**強力なパスワードを設定します。
- **MSSQL_TCP_PORT** 1234 に SQL Server がリッスンする TCP ポートを設定します。 つまり、ことホスト ポートにマッピングのポート 1433 (既定値)、代わりにカスタムの TCP ポートのマッピングが必要で、`-p 1234:1234`この例ではコマンド。

Linux/macOS で Docker を実行している場合は、単一引用符で、次の構文を使用します。

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

Windows で Docker を実行している場合は、二重引用符で、次の構文を使用します。

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> コンテナーで実稼働のエディションを実行するためのプロセスは若干異なります。 詳細については 「[実稼働環境のコンテナー イメージを実行する](sql-server-linux-configure-docker.md#production)」を参照してください。

## <a name="next-steps"></a>次の手順

SQL Server の設定が記載されていないその他、次を参照してください。 [mssql conf ツールを使用して Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

インストールし、Linux 上の SQL Server を実行する方法の詳細については、次を参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。
