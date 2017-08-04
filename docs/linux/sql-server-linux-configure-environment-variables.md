---
title: "環境変数と SQL Server の設定を構成する |Microsoft ドキュメント"
description: "このトピックでは、環境変数を使用して、Linux の特定の SQL Server 2017 設定を構成する方法について説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/21/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 4951f503a7b5c395f86cb6daf2ba705ca69fbd83
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>Linux 上の環境変数と SQL Server の設定を構成します。

いくつかの別の環境変数を使用して、Linux 上の SQL Server 2017 RC2 を構成することができます。 これらの変数は、2 つのシナリオで使用されます。

- 初期セットアップの構成、`mssql-conf setup`コマンド。
- 新しい構成を[Docker でコンテナーを SQL Server](quickstart-install-connect-docker.md)です。

> [!TIP]
> これらのシナリオのセットアップ後に SQL Server を構成する必要がある場合は、次を参照してください。 [mssql conf ツールを使用して Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

## <a name="environment-variables"></a>環境変数

| 環境変数 | Description |
|-----|-----|
| **ACCEPT_EULA** | 任意の値 (たとえば、' Y') に設定すると SQL Server のライセンス契約に同意します。 |
| **MSSQL_SA_PASSWORD** | SA パスワードを構成します。 |
| **MSSQL_PID** | SQL Server のエディションまたはプロダクト キーを設定します。 使用可能な値が含まれます: Evaluation、Developer、Express、Web、Standard、Enterprise、または ###-###-###-###-###、ここで、'#' は、数または文字の形式で、プロダクト キー。 |
| **MSSQL_LCID** | SQL Server に使用する言語 ID を設定します。 たとえば 1036 はフランス語です。 |
| **MSSQL_COLLATION** | SQL Server の既定の照合順序を設定します。 照合順序には、言語 id (LCID) の既定のマッピングが上書きされます。 |
| **MSSQL_MEMORY_LIMIT_MB** | 最大メモリ (MB) SQL Server が使用できる量を設定します。 既定では、合計物理メモリの 80% を勧めします。 |
| **MSSQL_TCP_PORT** | SQL Server が (既定は 1433) をリッスンする TCP ポートを構成します。 |
| **MSSQL_IP_ADDRESS** | IP アドレスを設定します。 現時点では、IP アドレスは IPv4 スタイル (0.0.0.0) にする必要があります。 |
| **MSSQL_BACKUP_DIR** | 既定のバックアップ ディレクトリの場所を設定します。 |
| **MSSQL_DATA_DIR** | 新しい SQL Server データベース データ ファイル (.mdf) の作成元ディレクトリを変更します。 |
| **MSSQL_LOG_DIR** | 新しい SQL Server データベースのログ (.ldf) ファイルが作成されるディレクトリを変更します。 |
| **MSSQL_DUMP_DIR** | ここで SQL Server が預金メモリ ダンプおよびその他のトラブルシューティング ファイル既定では、ディレクトリを変更します。 |
| **MSSQL_ENABLE_HADR** | 可用性グループを有効にします。 |

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
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 --cap-add SYS_PTRACE -p 1234:1234 -d microsoft/mssql-server-linux
```

Windows で Docker を実行している場合は、二重引用符で、次の構文を使用します。

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 --cap-add SYS_PTRACE -p 1234:1234 -d microsoft/mssql-server-linux
```

## <a name="next-steps"></a>次の手順

SQL Server の設定が記載されていないその他、次を参照してください。 [mssql conf ツールを使用して Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

インストールし、Linux 上の SQL Server を実行する方法の詳細については、次を参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。

