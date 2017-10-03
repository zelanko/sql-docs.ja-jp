---
title: "PowerShell を使用した Linux に SQL Server の管理 |Microsoft ドキュメント"
description: "このトピックでは、SQL Server on Linux での windows PowerShell の使用の概要を示します。"
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: a3492ce1-5d55-4505-983c-d6da8d1a94ad
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 7b607d624207b75ac2488f55fb75353110cf252c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Windows PowerShell を使用して、Linux 上の SQL Server を管理するには

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックで紹介[SQL Server PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx)と Linux 上の SQL Server 2017 で使用する方法の例をいくつか使用について説明します。 SQL Server の PowerShell のサポートは、Linux 上のリモート SQL Server インスタンスに接続できる Windows マシンがあるときに使用できるように Windows では、現在使用可能なです。

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Windows 上の SQL PowerShell の最新バージョンをインストールします。

[SQL PowerShell](https://msdn.microsoft.com/en-us/library/mt740629.aspx) Windows に付属している[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md)です。 SQL Server を使用する場合は、常に最新バージョンの SSMS および SQL PowerShell を使用する必要があります。 SSMS の最新バージョンは継続的に更新および最適化されている 2017 on Linux を SQL Server で現在動作します。 ダウンロードして、最新バージョンをインストールを参照してください。 [SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)です。 最新の状態に、SSMS の最新バージョンように求められますダウンロード可能な新しいバージョンがある場合。

## <a name="before-you-begin"></a>アンインストールの準備

読み取り、[既知の問題](sql-server-linux-release-notes.md)for Linux に SQL Server 2017 です。

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>PowerShell を起動し、インポート、 *sqlserver*モジュール

Windows PowerShell を起動してスタートしましょう。 開く、*コマンド プロンプト*Windows コンピューターと型の**PowerShell**新しい Windows PowerShell セッションを起動します。

```
PowerShell
```

SQL Server という名前の Windows PowerShell モジュールを提供する**SqlServer** PowerShell 環境またはスクリプトへの SQL Server コンポーネント (SQL Server プロバイダーとコマンドレット) をインポートに使用できます。

コピーしてインポートする PowerShell プロンプトで、以下のコマンドを貼り付ける、 **SqlServer**現在の PowerShell セッションにモジュール。

```powershell
Import-Module SqlServer
```

確認する PowerShell プロンプトで、以下のコマンドを入力、 **SqlServer**モジュールが正しくインポートされました。

```powershell
Get-Module -Name SqlServer
```

PowerShell には、対象に以下のような情報が表示されます。

```
ModuleType Version    Name          ExportedCommands
---------- -------    ----          ----------------
Script     0.0        SqlServer
Manifest   20.0       SqlServer     {Add-SqlAvailabilityDatabase, Add-SqlAvailabilityGroupList...
```

## <a name="connect-to-sql-server-and-get-server-information"></a>SQL Server に接続し、サーバーの情報の取得

みましょう PowerShell を使用して Windows を Linux に SQL Server 2017 インスタンスに接続し、いくつかのサーバーのプロパティを表示します。

コピーし、PowerShell プロンプトで次のコマンドを貼り付けます。 PowerShell は、これらのコマンドを実行するときに行います。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*)、SQL Server 2017 に接続するにはLinux 上のインスタンス
- SQL Server 管理オブジェクト (SMO) アセンブリを読み込み
- インスタンスを作成、[サーバー](https://msdn.microsoft.com/en-us/library/microsoft.sqlserver.management.smo.server.aspx)オブジェクト
- 接続、**サーバー**といくつかのプロパティを表示

置き換えます **\<your_server_instance\>**  IP アドレスまたは Linux に SQL Server 2017 インスタンスのホスト名です。

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

PowerShell の下に表示される内容のような情報が表示されます。

```
Edition          : Developer Edition (64-bit)
HostPlatform     : Linux
HostDistribution : Ubuntu
```
> [!NOTE]
> これらの値を何も表示が、対象の SQL Server インスタンスへの接続を可能性がありますが失敗した場合。 SQL Server Management Studio から接続する、同じ接続情報を使用することを確認します。 次に、[接続のトラブルシューティングに関する推奨事項](sql-server-linux-troubleshooting-guide.md#connection)を確認します。

## <a name="examine-sql-server-error-logs"></a>SQL Server エラー ログを調べます

接続して、エラー ログを調査する Windows PowerShell を使用して Linux 上の SQL Server 2017 インスタンスにします。 使用しても、 **Out-gridview**エラーからの情報を表示するコマンドレットをグリッド ビューの表示でログに記録します。

コピーし、PowerShell プロンプトで次のコマンドを貼り付けます。 実行するまで数分がかかる場合があります。 これらのコマンドは、次を操作します。
- 表示、 *Windows PowerShell 資格情報要求*資格情報の入力を求めるダイアログ (*SQL ユーザー名*と*SQL パスワード*)、SQL Server 2017 に接続するにはLinux 上のインスタンス
- 使用して、 **Get SqlErrorLog** Linux 上の SQL Server 2017 インスタンスに接続し、エラーを取得するコマンドレットをログに記録されてから**昨日**
- 出力をパイプ処理、 **Out-gridview**コマンドレット

置き換えます **\<your_server_instance\>**  IP アドレスまたは Linux に SQL Server 2017 インスタンスのホスト名です。

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

