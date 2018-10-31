---
title: PowerShell Desired State Configuration での SQL Server をインストールする | Microsoft Docs
description: PowerShell Desired State Configuration (DSC) を使用して SQL Server をインストールする方法について説明します。
ms.custom: ''
ms.date: 10/26/2018
ms.devlang: PowerShell
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
author: randomnote1
ms.author: dareist
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 16d425d8eb66a950f432fa3ef9c68a8e68a78d22
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148480"
---
# <a name="install-sql-server-with-powershell-desired-state-configuration"></a>PowerShell Desired State Configuration での SQL Server をインストールする

SQL Server のインストールのインターフェイスで何回クリックしましたか。見直すこともなく、同じような古いボタンをクリックし、同じ古い情報を入力するだけでしたか?  その後、インストールが完了し、"sysadmin ロールで DBA グループを指定するのを忘れていた" ことに気付きます。 ここで、シングル ユーザー モードに入り、適切なユーザーまたはグループを追加し、マルチ ユーザー モードに SQL バックアップを導入し、テストを行うことに貴重な時間を費やす必要があります。 さらに悪いことは、インストール全体への信頼が揺らぐことです。 "他に何か忘れていないか?"  私はこの状況に何度も陥ったことがあります。

[PowerShell Desired State Configuration (DSC)](https://docs.microsoft.com/powershell/dsc/overview) に入ります。 DSC を使用すると、数百、数千のサーバーで再利用できる 1 つの構成テンプレートをビルドできます。 ビルドに応じて、設定パラメーターを少し微調整する場合がありますが、すべての標準設定をそのまま保持できるため、大きな問題ではありません。 これのすばらしいことは、子供を世話するために眠れない夜を過ごした後、重要なパラメーターを入力するのを忘れる可能性を排除できるということです。

この記事では、SqlServerDsc DSC リソースを使用して、Windows Server 2016 上の SQL Server 2017 のスタンドアロン インスタンスの初期設定を参照します。 DSC がどのように動作するかを調べないときは、いくつかの DSC の予備知識があると役立ちます。

このチュートリアルには、次のアイテムが必須です。

- Windows Server 2016 を実行しているマシン
- SQL Server 2017 のインストール メディア
- SqlServerDsc DSC リソース (バージョン 10.0.0.0 が、記載時の現在のリリースです)

## <a name="prerequisites"></a>Prerequisites

ほとんどの場合、DSC を使用して前提条件が処理されます。 しかし、このデモの目的のため、ここでは前提条件を手動で処理します。

## <a name="install-the-sqlserverdsc-dsc-resource"></a>SqlServerDsc DSC リソースのインストール

[SqlServerDsc](https://www.powershellgallery.com/packages/SqlServerDsc) DSC リソースは、[Install-Module](https://docs.microsoft.com/powershell/module/powershellget/Install-Module?view=powershell-5.1) コマンドレットを使用して [PowerShell Gallery](https://www.powershellgallery.com/) からダウンロードできます。 _注: このモジュールをインストールするには、PowerShell が "管理者として" 実行されていることを確認します。_

```PowerShell
Install-Module -Name SqlServerDsc
```

SQL Server 2017 インストール メディアを取得し、SQL Server 2017 インストール メディアをサーバーにダウンロードします。 自分の Visual Studio サブスクリプションから SQL Server 2017 Enterprise をダウンロードして、ISO を "C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso" にコピーしました。

ここで、ISO はディレクトリに抽出される必要があります。

```PowerShell
New-Item -Path C:\SQL2017 -ItemType Directory
$mountResult = Mount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso' -PassThru
$volumeInfo = $mountResult | Get-Volume
$driveInfo = Get-PSDrive -Name $volumeInfo.DriveLetter
Copy-Item -Path ( Join-Path -Path $driveInfo.Root -ChildPath '*' ) -Destination C:\SQL2017\ -Recurse
Dismount-DiskImage -ImagePath 'C:\en_sql_server_2017_enterprise_x64_dvd_11293666.iso'
```

## <a name="create-the-configuration"></a>構成の作成

### <a name="configuration"></a>構成

[Managed Object Format (MOF)](https://docs.microsoft.com/windows/desktop/WmiSdk/managed-object-format--mof-) ドキュメントを生成するために呼び出される構成関数を作成します。

```PowerShell
Configuration SQLInstall
{...}
```

### <a name="modules"></a>モジュール

モジュールを現在のセッションにインポートします。 これらのモジュールでは、構成ドキュメントに MOF ドキュメントを作成する方法を指示し、DSC エンジンに MOF ドキュメントをサーバーに適用する方法を指示します。

```PowerShell
Import-DscResource -ModuleName SqlServerDsc
```

### <a name="resources"></a>リソース

#### <a name="net-framework"></a>.NET Framework

SQL Server は .NET Framework に依存するため、SQL Server をインストールする前に、.NET Framework がインストールされていることを確認する必要があります。 Net-Framework-45-Core の Windows 機能をインストールするには、WindowsFeature リソースを使用します。

```PowerShell
WindowsFeature 'NetFramework45'
{
     Name = 'Net-Framework-45-Core'
     Ensure = 'Present'
}
```

#### <a name="sqlsetup"></a>SqlSetup

DSC に SQL Server をインストールする方法を指示するために、SqlSetup リソースが使用されます。 基本的なインストールに必要なパラメーターは次のとおりです。

- **InstanceName**: インスタンスの名前です。 既定のインスタンスに MSSQLSERVER を使用します。
- **Features**: インストールする機能です。 この例では、SQLEngine 機能をインストールするだけです。
- **SourcePath**: SQL インストール メディアへのパスです。 この例では、SQL インストール メディアを "C:\SQL2017" に格納しました。 サーバー上で使用される領域を最小限に抑えるために、ネットワーク共有を使用できます。
- **SQLSysAdminAccounts**: sysadmin ロールのメンバーになるユーザーまたはグループです。 この例では、ローカルの Administrators グループに sysadmin アクセス権を付与します。 _注: 高度なセキュリティの環境では、この構成はお勧めできません。_

SqlSetup で利用できるパラメーターの完全な一覧と説明は、[SqlServerDsc GitHub リポジトリ](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlsetup)で入手できます。

SqlSetup リソースは、SQL のみをインストールし、適用される設定を保持しないため、不規則です。 たとえば、SQLSysAdminAccounts がインストール時に指定されている場合、管理者は sysadmin ロールに対するログインを追加または削除することができ、SqlSetup リソースには関係ありません。 DSC で sysadmin ロールのメンバーシップを適用する必要がある場合、[SqlServerRole](https://github.com/PowerShell/SqlServerDsc/tree/master#sqlserverrole) リソースを使用する必要があります。

#### <a name="complete-configuration"></a>完全な構成

```PowerShell
Configuration SQLInstall
{
     Import-DscResource -ModuleName SqlServerDsc

     node localhost
     {
          WindowsFeature 'NetFramework45'
          {
               Name   = 'NET-Framework-45-Core'
               Ensure = 'Present'
          }

          SqlSetup 'InstallDefaultInstance'
          {
               InstanceName        = 'MSSQLSERVER'
               Features            = 'SQLENGINE'
               SourcePath          = 'C:\SQL2017'
               SQLSysAdminAccounts = @('Administrators')
               DependsOn           = '[WindowsFeature]NetFramework45'
          }
     }
}
```

## <a name="build-and-deploy"></a>ビルドと配置

### <a name="compile-the-configuration"></a>構成のコンパイル

構成スクリプトのドット ソース

```PowerShell
. .\SQLInstallConfiguration.ps1
```

構成関数の実行

```PowerShell
SQLInstall
```

ディレクトリは "SQLInstall" と呼ばれる作業ディレクトリで作成され、"localhost.mof" と呼ばれるファイルが含まれます。 MOF のコンテンツを実行すると、コンパイルされた DSC 構成が表示されます。

### <a name="deploy-the-configuration"></a>構成の配置

SQL Server の DSC 配置を開始するには、Start-DscConfiguration コマンドレットを呼び出します。 コマンドレットに指定するパラメーターは次のとおりです。

- **Path**: 配置する MOF ドキュメントを含むフォルダーへのパスです。 (例: "C:\SQLInstall")
- **Wait**: 構成ジョブが完了するまで待機します。
- **Force**: 任意の既存の DSC 構成をオーバーライドします。
- **Verbose**: 詳細の出力を表示します。 トラブルシューティングに役立てるために、最初に構成をプッシュするときに便利です。

```PowerShell
Start-DscConfiguration -Path C:\SQLInstall -Wait -Force -Verbose
```

構成が適用されると、詳細の出力には発生している内容が表示され、何かが起こっているという穏やかな感覚になります。 エラー (赤いテキスト) がスローされない限り、画面上に "操作 'Invoke CimMethod' が完了しました。"  と表示された場合、SQL はインストールされています。

## <a name="validate-installation"></a>インストールの検証

### <a name="dsc"></a>DSC

[Test-DscConfiguration](https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration) コマンドレットを使用して、サーバーの現在の状態 (この場合は SQL のインストール) が目的の状態を満たしているかどうかを判断できます。 Test-DscConfiguration の結果は "True" になります。

```PowerShell
PS C:\> Test-DscConfiguration
True
```

### <a name="services"></a>サービス

サービスのリストには SQL Server サービスが返されます

```PowerShell
PS C:\> Get-Service -Name *SQL*
Status  Name           DisplayName
------  ----           -----------
Running MSSQLSERVER    SQL Server (MSSQLSERVER)
Stopped SQLBrowser     SQL Server Browser
Running SQLSERVERAGENT SQL Server Agent (MSSQLSERVER)
Running SQLTELEMETRY   SQL Server CEIP service (MSSQLSERVER)
Running SQLWriter      SQL Server VSS Writer
```

### <a name="sql-server"></a>SQL Server

```PowerShell
PS C:\> & sqlcmd -S $env:COMPUTERNAME
1> SELECT @@SERVERNAME
2> GO
1> quit
```

## <a name="see-also"></a>参照

[Windows PowerShell Desired State Configuration の概要](https://docs.microsoft.com/powershell/dsc/overview)

[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)

[構成ファイルを使用した SQL Server のインストール](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)
