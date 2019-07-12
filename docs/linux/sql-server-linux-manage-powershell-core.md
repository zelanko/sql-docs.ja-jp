---
title: PowerShell Core を使った Linux 上の SQL Server を管理します。
description: この記事では、SQL Server on Linux で PowerShell Core の使用の概要を示します。
ms.date: 04/22/2019
ms.prod: sql
ms.technology: linux
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
ms.reviewer: vanto
manager: jroth
ms.openlocfilehash: e96fe471f78e02e5667431f7065a169a5c136417
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834953"
---
# <a name="manage-sql-server-on-linux-with-powershell-core"></a>PowerShell Core を使った Linux 上の SQL Server を管理します。

この記事で紹介[SQL Server PowerShell](../powershell/sql-server-powershell.md) macOS および Linux での PowerShell Core (PS コア) で使用する方法の例のいくつかについて詳しく説明します。 PowerShell Core は現在はオープン ソース プロジェクト[GitHub](https://github.com/powershell/powershell)します。

## <a name="cross-platform-editor-options"></a>クロス プラットフォーム エディター オプション

正規のターミナルでは、すべての手順を次の PowerShell Core または VS Code または Azure Data Studio 内で、ターミナルから実行することができます。  VS Code と Azure Data Studio の両方が macOS および Linux で使用できます。  Azure Data Studio の詳細については、次を参照してください。[このクイック スタート](https://docs.microsoft.com/sql/azure-data-studio/quickstart-sql-server)します。  使用を検討することも、 [PowerShell 拡張機能](https://docs.microsoft.com/sql/azure-data-studio/powershell-extension)にします。

## <a name="installing-powershell-core"></a>PowerShell Core のインストール

サポートされていると実験用のさまざまなプラットフォームで PowerShell Core のインストールの詳細については、次の記事を参照してください。

- [Windows 上の PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6)
- [Linux 上の PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [MacOS での PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)
- [ARM の PowerShell Core のインストール](https://docs.microsoft.com/powershell/scripting/install/powershell-core-on-arm?view=powershell-6)

## <a name="install-the-sqlserver-module"></a>SqlServer モジュールをインストールします。

`SqlServer`モジュールの訳では、 [PowerShell ギャラリー](https://www.powershellgallery.com/packages/SqlServer/)します。 SQL Server を使用する場合は、SqlServer PowerShell モジュールの最新バージョンを常に使用する必要があります。

SqlServer モジュールをインストールするには、PowerShell Core のセッションを開き、次のコードを実行します。

```powerhsell
Install-Module -Name SqlServer
```

SqlServer モジュールを PowerShell ギャラリーからインストールする方法の詳細については、この参照してください。[ページ](../powershell/download-sql-server-ps-module.md)します。

## <a name="using-the-sqlserver-module"></a>SqlServer モジュールを使用します。

PowerShell Core を起動してみましょう。  MacOS または Linux、オープンしている場合、*ターミナル セッション*、コンピューター、および種類に**pwsh**新しい PowerShell Core のセッションを起動します。  Windows を使用して<kbd>Win</kbd>+<kbd>R</kbd>、および種類`pwsh`新しい PowerShell Core のセッションを起動します。

```
pwsh
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

次の手順では、Linux 上の SQL Server インスタンスに接続し、いくつかのサーバーのプロパティを表示する PowerShell Core を使用します。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 これらのコマンドを実行すると、PowerShell が行われます。
- ホスト名またはインスタンスの IP アドレスの入力を求めるダイアログを表示します。
- 表示、 *PowerShell 資格情報要求*ダイアログ ボックスで、資格情報が求められます。 使用することができます、 *SQL ユーザー名*と*SQL パスワード*Linux 上の SQL Server インスタンスに接続するには
- 使用して、 **Get SqlInstance**コマンドレットへの接続を使用して、 **Server**といくつかのプロパティを表示

必要に応じて、置き換えることができますのみ、 `$serverInstance` IP アドレスまたは SQL Server インスタンスのホスト名で変数。

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Connect to the Server and return a few properties
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

SQL Server インスタンスに接続するためのもう 1 つのオプションは、使用する、 [SQL Server PowerShell プロバイダー](https://docs.microsoft.com/sql/powershell/sql-server-powershell-provider)します。  プロバイダーを使用してオブジェクト エクスプ ローラーでは、コマンドラインでのツリー構造を移動した場合とのような SQL Server インスタンスを移動することができます。  既定では、このプロバイダーがという名前の PSDrive として表示される`SQLSERVER:\`接続 (&)、ドメイン アカウントがアクセスできる SQL Server インスタンスの移動に使用できます。  参照してください[構成手順](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-auth-overview#configuration-steps)Linux 上の SQL Server の Active Directory 認証をセットアップする方法についてはします。

SQL Server PowerShell プロバイダーと SQL 認証を使用することもできます。 これを行うには、使用、`New-PSDrive`新しい PSDrive を作成し、接続する適切な資格情報を提供するコマンドレットです。

、次の例では、SQL 認証を使用して新しい PSDrive の作成方法の例が表示されます。

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

次の出力のように示します。  この出力は、[データベース] ノードに SSMS が表示されますが分かります。  ユーザーのデータベースがシステム データベースではなくが表示されます。

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

1 つのオプションを使用するが、インスタンスのすべてのデータベースを表示する必要がある場合、`Get-SqlDatabase`コマンドレット。

## <a name="get-databases"></a>データベースを取得します。

知り、重要なコマンドレットは、`Get-SqlDatabase`します。  データベース、または、データベース内のオブジェクトに関連する多くの操作を`Get-SqlDatabase`コマンドレットを使用できます。  両方の値を指定する場合、`-ServerInstance`と`-Database`パラメーター、その 1 つのデータベース オブジェクトのみが取得されます。  ただし、のみを指定する場合、`-ServerInstance`パラメーター、そのインスタンス上のすべてのデータベースの完全な一覧が返されます。

```powershell
# NOTE: We are reusing the values saved in the $credential variable from the above example.

# Connect to the Instance and retrieve all databases
Get-SqlDatabase -ServerInstance ServerB -Credential $credential
```

上記の Get-sqldatabase コマンドによって返される内容のサンプルを次に示します。

```powershell
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2016   Normal      209.63 MB    1.31 MB Simple       130 sa
AdventureWorksDW2012 Normal      167.00 MB   32.47 MB Simple       110 sa
AdventureWorksDW2014 Normal      188.00 MB   78.10 MB Simple       120 sa
AdventureWorksDW2016 Normal      172.00 MB   74.88 MB Simple       130 sa
AdventureWorksDW2017 Normal      208.00 MB   40.63 MB Simple       140 sa
master               Normal        6.00 MB  600.00 KB Simple       140 sa
model                Normal       16.00 MB    5.70 MB Full         140 sa
msdb                 Normal       15.50 MB    1.14 MB Simple       140 sa
tempdb               Normal       16.00 MB    5.49 MB Simple       140 sa

```

## <a name="examine-sql-server-error-logs"></a>SQL Server エラー ログを調べます

次の手順では、PowerShell Core を使用して、Linux 上の SQL Server インスタンス上のログの接続エラーを調べます。

コピーして、PowerShell プロンプトで次のコマンドを貼り付けます。 実行するまで数分がかかる場合があります。 これらのコマンドは、次の手順を実行します。
- ホスト名またはインスタンスの IP アドレスの入力を求めるダイアログを表示します。
- 表示、 *PowerShell 資格情報要求*資格情報の入力を求めるダイアログ。 使用することができます、 *SQL ユーザー名*と*SQL パスワード*Linux 上の SQL Server インスタンスに接続するには
- 使用して、 **Get SqlErrorLog** Linux 上の SQL Server インスタンスに接続し、エラーを取得するコマンドレットのログ以降**昨日**

必要に応じて置き換えることができます、 `$serverInstance` IP アドレス、または SQL Server インスタンスのホスト名の変数。

```powershell
# Prompt for instance & credentials to login into SQL Server
$serverInstance = Read-Host "Enter the name of your instance"
$credential = Get-Credential

# Retrieve error logs since yesterday
Get-SqlErrorLog -ServerInstance $serverInstance -Credential $credential -Since Yesterday
# done
```

## <a name="explore-cmdlets-currently-available-in-ps-core"></a>PS Core で現在使用可能なコマンドレットを詳細します。
SqlServer モジュールには、Windows PowerShell で使用できる 106 コマンドレットは現在、唯一 59、106 の PSCore で使用できます。 現在使用可能な 59 コマンドレットの完全な一覧は、以下に示します。  SqlServer モジュールのすべてのコマンドレットの詳細なドキュメントを参照してください、SqlServer[コマンドレット リファレンス](https://docs.microsoft.com/powershell/module/sqlserver/)します。

次のコマンドに表示 すべての利用可能なコマンドレットを使用する PowerShell のバージョン。

```powershell
Get-Command -Module SqlServer -CommandType Cmdlet |
SORT -Property Noun |
SELECT Name
```

- ConvertFrom EncodedSqlName
- ConvertTo EncodedSqlName
- Get SqlAgent
- Get-SqlAgentJob
- Get-SqlAgentJobHistory
- Get SqlAgentJobSchedule
- Get SqlAgentJobStep
- Get SqlAgentSchedule
- Remove-SqlAvailabilityDatabase
- Resume-SqlAvailabilityDatabase
- Add-SqlAvailabilityDatabase
- Suspend-SqlAvailabilityDatabase
- New-SqlAvailabilityGroup
- Set-SqlAvailabilityGroup
- Remove-SqlAvailabilityGroup
- Switch-SqlAvailabilityGroup
- Join-SqlAvailabilityGroup
- Revoke-sqlavailabilitygroupcreateanydatabase
- Grant SqlAvailabilityGroupCreateAnyDatabase
- New-SqlAvailabilityGroupListener
- Set-SqlAvailabilityGroupListener
- Add-SqlAvailabilityGroupListenerStaticIp
- Set-SqlAvailabilityReplica
- Remove-SqlAvailabilityReplica
- New-SqlAvailabilityReplica
- セット SqlAvailabilityReplicaRoleToSecondary
- 新しい SqlBackupEncryptionOption
- Get-SqlBackupHistory
- Invoke-sqlcmd
- New-SqlCngColumnMasterKeySettings
- Remove-SqlColumnEncryptionKey
- Get-SqlColumnEncryptionKey
- Remove-SqlColumnEncryptionKeyValue
- Add-SqlColumnEncryptionKeyValue
- Get-SqlColumnMasterKey
- Remove-SqlColumnMasterKey
- New-SqlColumnMasterKey
- Get-SqlCredential
- Set-SqlCredential
- New-SqlCredential
- Remove-SqlCredential
- New-SqlCspColumnMasterKeySettings
- Get-sqldatabase
- Restore-SqlDatabase
- Backup-SqlDatabase
- セット SqlErrorLog
- Get-SqlErrorLog
- 新しい SqlHADREndpoint
- Set-sqlhadrendpoint
- Get SqlInstance
- 追加 SqlLogin
- 削除 SqlLogin
- Get SqlLogin
- Set-sqlsmartadmin
- Get-SqlSmartAdmin
- Read-sqltabledata
- 書き込み SqlTableData
- Read-SqlViewData
- Convert-urntopath

## <a name="see-also"></a>関連項目
- [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)
