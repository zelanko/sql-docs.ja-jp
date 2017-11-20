---
title: ".NET コード (c#) で、SSIS プロジェクトを実行 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: 65a8db27af80e5cd7001e9a8777dde3c59e9c55e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-with-c-code-in-a-net-app"></a>.NET アプリでの c# コードで、SSIS パッケージを実行します。
このクイック スタート チュートリアルでは、C# の場合、データベース サーバーに接続し、SSIS パッケージを実行するコードを記述する方法を示します。

Visual Studio、Visual Studio コード、または任意の別のツールを使用して、c# アプリケーションを作成することができます。

## <a name="prerequisites"></a>前提条件

開始する前に Visual Studio があるか、Visual Studio のコードがインストールされていることを確認します。 Visual Studio または無料の Visual Studio Code の無料の Community edition をダウンロード[Visual Studio のダウンロード](https://www.visualstudio.com/downloads/)です。

> [!NOTE]
> Azure SQL データベース サーバーは、ポート 1433 でリッスンします。 企業のファイアウォール内での Azure SQL データベース サーバーに接続しようとしている場合、このポートが正常に接続するための企業ファイアウォールで開いていなければなりません。

## <a name="get-the-connection-info-if-deployed-to-sql-database"></a>SQL データベースに展開する場合は、接続情報を取得します。

Azure SQL Database に、パッケージを展開している場合は、SSIS カタログ データベース (SSISDB) に接続する必要があります。 接続情報を取得します。 次の手順の完全修飾サーバー名とログイン情報を必要とします。

1. [Azure ポータル](https://portal.azure.com/)にログインします。
2. 選択**SQL データベース**、左側メニューをクリックして、SSISDB データベースから、 **SQL データベース**ページ。 
3. **概要**データベースのページで、完全修飾サーバー名を確認します。 呼び出すこと、**をコピーする をクリックします。**オプション、サーバー名をポイントします。 
4. Azure SQL データベース サーバーのログイン情報を忘れた場合は、サーバーの管理者名を表示する SQL データベース サーバー ページに移動します。 必要な場合は、パスワードをリセットすることができます。
5. をクリックして**データベース接続文字列の表示**です。
6. 完全な確認**ADO.NET**接続文字列。 サンプル コードを使用して、`SqlConnectionStringBuilder`を提供する個々 のパラメーター値を持つ場合は、この接続文字列を再作成します。

## <a name="create-a-new-visual-studio-project"></a>新しい Visual Studio プロジェクトを作成します。

1. Visual Studio で、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。 
2. **新しいプロジェクト**ダイアログ ボックスで、展開と**Visual c#**です。
3. 選択**コンソール アプリ**入力と*run_ssis_project*プロジェクト名のです。
4. をクリックして**OK**を作成し、Visual Studio で新しいプロジェクトを開きます。

## <a name="add-references"></a>参照を追加します。
1. ソリューション エクスプ ローラーで右クリックし、**参照**フォルダーと選択**参照の追加**です。 **参照マネージャー**  ダイアログ ボックスが表示されます。
2. **参照マネージャー**  ダイアログ ボックスで、展開**アセンブリ**選択と**拡張**です。
3. 次の 2 つの参照を追加するを選択します。
    -   Microsoft.SqlServer.Management.Sdk.Sfc
    -   Microsoft.SqlServer.Smo
4. クリックして、**参照**への参照を追加するにはボタン**Microsoft.SqlServer.Management.IntegrationServices**です。 (このアセンブリはグローバル アセンブリ キャッシュ (GAC) にのみインストールされます)。**を参照するファイルの選択** ダイアログ ボックスが表示されます。
5. **を参照するファイルの選択** ダイアログ ボックスで、アセンブリを含む GAC フォルダーに移動します。 このフォルダーは、通常`C:\Windows\assembly\GAC_MSIL\Microsoft.SqlServer.Management.IntegrationServices\14.0.0.0__89845dcd8080cc91`です。
6. フォルダーでアセンブリ (.dll ファイル) を選択し**追加**です。
7. をクリックして**OK**を閉じる、**参照マネージャー**  ダイアログ ボックスし、次の 3 つの参照を追加します。 参照があることを確認するには、確認、**参照**ソリューション エクスプ ローラーの一覧です。

## <a name="add-the-c-code"></a>C# のコードを追加します。 
1. 開いている**Program.cs**です。

2. 内容を置き換える**Program.cs**を次のコード。 サーバー、データベース、ユーザー、およびパスワードの適切な値を追加します。

> [!NOTE]
> 次の例では、Windows 認証を使用します。 SQL Server 認証を使用するのには、置換、`Integrated Security=SSPI;`引数と`User ID=<user name>;Password=<password>;`です。


```csharp
using Microsoft.SqlServer.Management.IntegrationServices;
using System.Data.SqlClient;

namespace run_ssis_package
{
    class Program
    {
        static void Main(string[] args)
        {
            // Variables
            string targetServerName = "localhost";
            string folderName = "Project1Folder";
            string projectName = "Integration Services Project1";
            string packageName = "Package.dtsx";

            // Create a connection to the server
            string sqlConnectionString = "Data Source=" + targetServerName +
                ";Initial Catalog=master;Integrated Security=SSPI;";
            SqlConnection sqlConnection = new SqlConnection(sqlConnectionString);

            // Create the Integration Services object
            IntegrationServices integrationServices = new IntegrationServices(sqlConnection);

            // Get the Integration Services catalog
            Catalog catalog = integrationServices.Catalogs["SSISDB"];

            // Get the folder
            CatalogFolder folder = catalog.Folders[folderName];

            // Get the project
            ProjectInfo project = folder.Projects[projectName];

            // Get the package
            PackageInfo package = project.Packages[packageName];

            // Run the package
            package.Execute(false, null);

        }
    }
}
```

## <a name="run-the-code"></a>コードを実行します。

1. 実行するには、アプリケーション キーを押して**f5 キーを押して**です。
2. パッケージが期待どおりに実行されたことを確認し、アプリケーション ウィンドウを閉じます。

## <a name="next-steps"></a>次の手順
- パッケージを実行するには、その他の方法を検討してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)

