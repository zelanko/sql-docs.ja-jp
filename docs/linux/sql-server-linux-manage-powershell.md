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
ms.openlocfilehash: 73d9780e2980eeecf49cf420901e7e6f1dc4a669
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089386"
---
# <a name="use-powershell-on-windows-to-manage-sql-server-on-linux"></a>Windows で PowerShell を使用して、SQL Server on Linux を管理するには

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事で紹介[SQL Server PowerShell](../powershell/sql-server-powershell.md)と SQL Server on Linux で使用する方法の例のいくつかについて説明します。 SQL Server の PowerShell のサポートは、Windows、MacOS、Linux で現在使用可能なです。 この記事には、Linux 上のリモート SQL Server インスタンスへの接続に Windows マシンを使用して、について説明します。

## <a name="install-the-newest-version-of-sql-powershell-on-windows"></a>Windows 上の SQL PowerShell の最新バージョンをインストールします。

[SQL PowerShell](../powershell/download-sql-server-ps-module.md) Windows では、PowerShell ギャラリーに格納されます。 SQL Server を使用する場合は、SqlServer PowerShell モジュールの最新バージョンを常に使用する必要があります。

## <a name="before-you-begin"></a>アンインストールの準備

読み取り、[既知の問題](sql-server-linux-release-notes.md)for SQL Server on Linux。

## <a name="launch-powershell-and-import-the-sqlserver-module"></a>PowerShell を起動し、インポート、 *sqlserver*モジュール

Windows で PowerShell を起動してみましょう。 使用<kbd>Win</kbd>+<kbd>R</kbd>では、Windows コンピューターと種類、 **PowerShell**新しい Windows PowerShell セッションを起動します。

```
PowerShell
```

SQL Server という名前の PowerShell モジュールを提供する**SqlServer**します。 使用することができます、 **SqlServer** PowerShell 環境またはスクリプトに SQL Server コンポーネント (SQL Server プロバイダーとコマンドレット) をインポートするモジュール。

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
- ホスト名またはインスタンスの IP アドレスの入力を求めるダイアログを表示します。
- 表示、 *Windows PowerShell 資格情報要求*ダイアログ ボックスで、資格情報が求められます。 使用することができます、 *SQL ユーザー名*と*SQL パスワード*Linux 上の SQL Server インスタンスに接続するには
- 使用して、 **Get SqlInstance**コマンドレットへの接続を使用して、 **Server**といくつかのプロパティを表示

必要に応じて、置き換えることができますのみ、 `$serverInstance` IP アドレスまたは SQL Server インスタンスのホスト名で変数。

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
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

## <a name="using-the-sql-server-powershell-provider"></a>SQL Server PowerShell プロバイダーを使用します。

SQL Server インスタンスに接続するためのもう 1 つのオプションは、使用する、 [SQL Server PowerShell プロバイダー](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider)します。  このプロバイダーでは、オブジェクト エクスプ ローラーでは、コマンドラインでのツリー構造を移動した場合とのような SQL Server インスタンスを移動できます。  既定では、このプロバイダーがという名前の PSDrive として表示される`SQLSERVER:\`接続 (&)、ドメイン アカウントがアクセスできる SQL Server インスタンスの移動に使用できます。  参照してください[構成手順](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps)Linux 上の SQL Server の Active Directory 認証をセットアップする方法についてはします。

SQL Server PowerShell プロバイダーと SQL 認証を使用することもできます。 これを行うには、使用、`New-PSDrive`新しい PSDrive を作成し、接続するために適切な資格情報を提供するコマンドレットです。

、次の例では、SQL 認証を使用して新しい PSDrive の作成方法の 1 つの例が表示されます。

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.
New-PSDrive -Name SQLonDocker -PSProvider SqlServer -Root 'SQLSERVER:\SQL\localhost,10002\Default\' -Credential $credential
```

実行して、ドライブが作成されたことを確認できます、`Get-PSDrive`コマンドレット。

```powershell
Get-PSDrive
```

新しい PSDrive を作成した後に操作を開始できます。

```powershell
dir SQLonDocker:\Databases
```

次の出力のように示します。  出力は SSMS は、[データベース] ノードに表示するように注意してください可能性があります。  ユーザーのデータベースがシステム データベースではなくが表示されます。

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.76 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.57 MB Simple       140 sa
```

1 つのオプションを使用するが、インスタンスのすべてのデータベースを表示する必要がある場合、[が Get-sqldatabase](https://docs.microsoft.com/powershell/module/sqlserver/Get-SqlDatabase)コマンドレット。

## <a name="examine-sql-server-error-logs"></a>SQL Server エラー ログを調べます

次の手順では、Windows で PowerShell を使用して、ログは、Linux 上の SQL Server インスタンスに接続エラーを調べます。 また、 **Out-gridview**グリッド ビューの表示で、エラーからの情報を表示するコマンドレットのログします。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 実行するまで数分がかかる場合があります。 これらのコマンドを以下に示します。
- ホスト名またはインスタンスの IP アドレスの入力を求めるダイアログを表示します。
- 表示、 *Windows PowerShell 資格情報要求*ダイアログ ボックスで、資格情報が求められます。 使用することができます、 *SQL ユーザー名*と*SQL パスワード*Linux 上の SQL Server インスタンスに接続するには
- 使用して、 **Get SqlErrorLog** Linux 上の SQL Server インスタンスに接続し、エラーを取得するコマンドレットのログ以降**昨日**
- 出力をパイプ処理、 **Out-gridview**コマンドレット

必要に応じて置き換えることができます、 `$serverInstance` IP アドレス、または SQL Server インスタンスのホスト名の変数。

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday | Out-GridView
# done
```
## <a name="see-also"></a>関連項目
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
- [SqlServer のコマンドレット](https://docs.microsoft.com/powershell/module/sqlserver)
