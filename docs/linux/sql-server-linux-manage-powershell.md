---
title: PowerShell を使用した Linux 上の SQL Server の管理 |Microsoft Docs
description: この記事では、SQL Server on Linux での Windows で PowerShell の使用の概要を提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.openlocfilehash: e198ae15b5f618b25f7d4391a0a09be33621c2da
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085734"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Windows で PowerShell を使用して、SQL Server on Linux を管理するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事で紹介[SQL Server PowerShell](https://msdn.microsoft.com/library/mt740629.aspx)と、SQL Server 2017 on Linux での使用方法については、いくつかの例について説明します。 Linux 上のリモート SQL Server インスタンスに接続できる Windows コンピューターがある場合に使用できるように、for SQL Server PowerShell のサポートは現在、Windows で使用できます。

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Windows 上の SQL PowerShell の最新バージョンをインストールします。

[SQL PowerShell](https://msdn.microsoft.com/library/mt740629.aspx) Windows に含まれている[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)します。 SQL Server を使用する場合は、SSMS および SQL PowerShell の最新バージョンを常に使用する必要があります。 SSMS の最新バージョンは更新は継続的に最適化し、2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)します。 最新の情報、ダウンロード可能な新しいバージョンがある場合にする最新バージョンの SSMS を求めます。

## <a name="before-you-begin"></a>アンインストールの準備

読み取り、[既知の問題](sql-server-linux-release-notes.md)SQL Server 2017 on Linux の。

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
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>SQL Server に接続し、サーバーの情報を取得します。

Linux 上の SQL Server 2017 インスタンスに接続し、いくつかのサーバーのプロパティを表示する、Windows で PowerShell を使用しましょう。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 これらのコマンドを実行すると、PowerShell が行われます。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*) SQL Server 2017 に接続するにはLinux 上のインスタンス
- SQL Server 管理オブジェクト (SMO) アセンブリを読み込み
- インスタンスを作成、 [Server](https://msdn.microsoft.com/library/microsoft.sqlserver.management.smo.server.aspx)オブジェクト
- 接続、 **Server**といくつかのプロパティを表示

置き換えてください**\<your_server_instance\>** IP アドレスまたは Linux 上の SQL Server 2017 インスタンスのホスト名でします。

```powershell
# Prompt for credentials to login into SQL Server
$serverInstance = "<your_server_instance>"
$credential = Get-Credential

# Load the SMO assembly and create a Server object
[System.Reflection.Assembly]::LoadWithPartialName('Microsoft.SqlServer.SMO') | out-null
$server = New-Object ('Microsoft.SqlServer.Management.Smo.Server') $serverInstance

# Set credentials
$server.ConnectionContext.LoginSecure=$false
$server.ConnectionContext.set_Login($credential.UserName)
$server.ConnectionContext.set_SecurePassword($credential.Password)

# Connect to the Server and get a few properties
$server.Information | Select-Object Edition, HostPlatform, HostDistribution | Format-List
# done
```

PowerShell では、次の出力のような情報を表示する必要があります。

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> これらの値は何も表示場合、ほとんどの場合、ターゲット SQL Server インスタンスに接続が失敗しました。 SQL Server Management Studio から接続する、同じ接続情報を使用することを確認します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。

## <a name="examine-sql-server-error-logs"></a>SQL Server エラー ログを調べます

エラー ログを確認する Windows PowerShell を使用しては、Linux 上の SQL Server 2017 インスタンスに接続しましょう。 また、 **Out-gridview**グリッド ビューの表示で、エラーからの情報を表示するコマンドレットのログします。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 実行するまで数分がかかる場合があります。 これらのコマンドを以下に示します。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*) SQL Server 2017 に接続するにはLinux 上のインスタンス
- 使用して、 **Get SqlErrorLog** Linux 上の SQL Server 2017 インスタンスに接続し、エラーを取得するコマンドレットのログ以降**昨日**
- 出力をパイプ処理、 **Out-gridview**コマンドレット

置き換えてください**\<your_server_instance\>** IP アドレスまたは Linux 上の SQL Server 2017 インスタンスのホスト名でします。

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
