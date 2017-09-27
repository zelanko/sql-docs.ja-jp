---
title: "PowerShell で、SSIS パッケージを実行 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: d392ac49442ef0f04961908fff7acf553fa1aa57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-powershell"></a>PowerShell での SSIS パッケージを実行します。
このクイック スタート チュートリアルでは、PowerShell スクリプトを使用してデータベース サーバーに接続し、SSIS パッケージを実行する方法を示します。

## <a name="powershell-script"></a>PowerShell スクリプト
変数の場合、次のスクリプトの上部にある適切な値を指定し、SSIS パッケージを実行するスクリプトを実行します。

> [!NOTE]
> 次の例では、Windows 認証を使用します。 SQL Server 認証を使用するのには、置換、`Integrated Security=SSPI;`引数と`User ID=<user name>;Password=<password>;`です。

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectName = "Integration Services Project1"
$PackageName = "Package.dtsx"

# Load the IntegrationServices assembly
$loadStatus = [System.Reflection.Assembly]::Load("Microsoft.SQLServer.Management.IntegrationServices, "+
    "Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91, processorArchitecture=MSIL")

# Create a connection to the server
$sqlConnectionString = `
    "Data Source=" + $TargetServerName + ";Initial Catalog=master;Integrated Security=SSPI;"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $SSISNamespace".IntegrationServices" $sqlConnection

# Get the Integration Services catalog
$catalog = $integrationServices.Catalogs["SSISDB"]

# Get the folder
$folder = $catalog.Folders[$TargetFolderName]

# Get the project
$project = $folder.Projects[$ProjectName]

# Get the package
$package = $project.Packages[$PackageName]

Write-Host "Running " $PackageName "..."

$result = $package.Execute("false", $null)

Write-Host "Done."
```

## <a name="next-steps"></a>次の手順
- パッケージを実行するには、その他の方法を検討してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 

