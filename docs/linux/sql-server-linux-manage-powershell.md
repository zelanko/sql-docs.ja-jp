---
title: PowerShell を使用した Linux 上の SQL Server の管理 |Microsoft Docs
description: この記事では、SQL Server on Linux での Windows で PowerShell の使用の概要を提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: 903d2d89ca0d551cbb78cfb69dd305f852f62313
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158768"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Windows で PowerShell を使用して、SQL Server on Linux を管理するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事で紹介[SQL Server PowerShell](../powershell/sql-server-powershell.md)と SQL Server on Linux で使用する方法の例のいくつかについて説明します。 Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に使用できるように、for SQL Server PowerShell のサポートは現在、Windows で使用できます。

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Windows 上の SQL PowerShell の最新バージョンをインストールします。

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) Windows では、PowerShell ギャラリーに格納されます。 SQL Server を使用する場合は、SqlServer PowerShell モジュールの最新バージョンを常に使用する必要があります。

## <a name="before-you-begin"></a>アンインストールの準備

読み取り、[既知の問題](sql-server-linux-release-notes.md)for SQL Server on Linux。

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>PowerShell を起動し、インポート、 *sqlserver*モジュール

Windows で PowerShell を起動してみましょう。 開く、*コマンド プロンプト*、Windows コンピューターでは、型に**PowerShell**新しい Windows PowerShell セッションを起動します。

```
PowerShell
```

SQL Server という名前の Windows PowerShell モジュールを提供する**SqlServer** PowerShell 環境またはスクリプトに SQL Server コンポーネント (SQL Server プロバイダーとコマンドレット) をインポートして使用できます。

コピーをインポートする PowerShell プロンプトで次のコマンドを貼り付けて、 **SqlServer**現在の PowerShell セッションにモジュール。

```powershell
Import-Module SqlServer
```

確認する PowerShell プロンプトで次のコマンドを入力、 **SqlServer**モジュールが正しくインポートされました。

```powershell
Get-Module -Name SqlServer
```

PowerShell では、次の出力のような情報を表示する必要があります。

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     21.1.18102 SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>SQL Server に接続し、サーバーの情報を取得します。

Linux 上の SQL Server インスタンスに接続し、いくつかのサーバーのプロパティを表示する、Windows で PowerShell を使用しましょう。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 これらのコマンドを実行すると、PowerShell が行われます。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*)、SQL Server に接続するにはLinux 上のインスタンス
- インスタンスを作成、 [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx)オブジェクト
- 接続、 **Server**といくつかのプロパティを表示

置き換えてください**\<your_server_instance\>** IP アドレスまたは Linux 上の SQL Server インスタンスのホスト名でします。

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Connect to the Server and get a few properties
Get-SqlInstance -ServerInstance $serverInstance -Credential $credential
# done
```

PowerShell では、次の出力のような情報を表示する必要があります。

```
Instance Name                   Version    ProductLevel UpdateLevel  HostPlatform HostDistribution                
-------------                   -------    ------------ -----------  ------------ ----------------                
your_server_instance            14.0.3048  RTM          CU13         Linux        Ubuntu 
```
> [!NOTE]
> これらの値は何も表示場合、ほとんどの場合、ターゲット SQL Server インスタンスに接続が失敗しました。 SQL Server Management Studio から接続する、同じ接続情報を使用することを確認します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。

## <a name="examine-sql-server-error-logs"></a>SQL Server エラー ログを調べます

エラー ログを確認する Windows PowerShell を使用しては、Linux 上の SQL Server インスタンスに接続しましょう。 また、 **Out-gridview**グリッド ビューの表示で、エラーからの情報を表示するコマンドレットのログします。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 実行するまで数分がかかる場合があります。 これらのコマンドを以下に示します。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*)、SQL Server に接続するにはLinux 上のインスタンス
- 使用して、 **Get SqlErrorLog** Linux 上の SQL Server インスタンスに接続し、エラーを取得するコマンドレットのログ以降**昨日**
- 出力をパイプ処理、 **Out-gridview**コマンドレット

置き換えてください**\<your_server_instance\>** IP アドレスまたは Linux 上の SQL Server インスタンスのホスト名でします。

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>参照
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
