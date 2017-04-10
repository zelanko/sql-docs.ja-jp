---
title: "Integration Services サーバーへのパッケージの配置 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c26ce7f4-7b34-4c9a-8649-ba767d30c827
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Integration Services サーバーへのパッケージの配置
  [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] で導入された増分パッケージ配置機能を使用すると、プロジェクト全体を配置することなく、既存または新規のプロジェクトに 1 つ以上のパッケージを配置できます。  
  
##  <a name="DeployWizard"></a> Integration Services 配置ウィザードを使用してパッケージを配置する  
  
1.  コマンド プロンプトで、**%ProgramFiles%\Microsoft SQL Server\130\DTS\Binn** にある **isdeploymentwizard.exe** を実行します。 64 ビット コンピューターの場合、**%ProgramFiles(x86)%\Microsoft SQL Server\130\DTS\Binn** に 32 ビット バージョンのツールもあります。  
  
2.  **[ソースの選択]** ページで、 **[パッケージ配置モデル]**に切り替えます。 次に、配置対象のパッケージが含まれるフォルダーを選択し、パッケージを構成します。  
  
3.  ウィザードを完了します。 [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel)で説明されている残りの手順を実行します。  
  
##  <a name="SSMS"></a> SQL Server Management Studio を使用してパッケージを配置する  
  
1.  SQL Server Management Studio のオブジェクト エクスプローラーで、**[Integration Services カタログ]**  >  **[SSISDB]** ノードの順に展開します。  
  
2.  **[プロジェクト]** フォルダーを右クリックして、**[プロジェクトの配置]** をクリックします。  
  
3.  **[説明]** ページが表示される場合は、 **[次へ]** をクリックして続行します。  
  
4.  **[ソースの選択]** ページで、 **[パッケージ配置モデル]**に切り替えます。 次に、配置対象のパッケージが含まれるフォルダーを選択し、パッケージを構成します。  
  
5.  ウィザードを完了します。 [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel)で説明されている残りの手順を実行します。  
  
##  <a name="SSDT"></a> SQL Server Data Tools (Visual Studio) を使用してパッケージを配置する  
  
1.  Visual Studio で Integration Services プロジェクトを開き、配置する 1 つ以上のパッケージを選択します。  
  
2.  右クリックして、**[パッケージの配置]** をクリックします。 選択したパッケージ (配置対象のパッケージとして構成済みのもの) が配置ウィザードによって開かれます。  
  
3.  ウィザードを完了します。 [Package Deployment Model](../../integration-services/packages/integration-services-deployment-wizard.md#PackageModel)で説明されている残りの手順を実行します。  
  
##  <a name="StoredProcedure"></a> deploy_packages ストアド プロシージャを使用してパッケージを配置する  
 **[catalog].[deploy_packages]** ストアド プロシージャを使用して、1 つ以上の SSIS パッケージを SSIS カタログに配置できます。 次のコード例では、このストアド プロシージャを使用して SSIS サーバーにパッケージを配置する方法を示します。 詳細については、「[catalog.deploy_packages](../../integration-services/system-stored-procedures/catalog-deploy-packages.md)」を参照してください。  
  
```  
  
private static void Main(string[] args)  
{  
    // Connection string to SSISDB  
    var connectionString = "Data Source=.;Initial Catalog=SSISDB;Integrated Security=True;MultipleActiveResultSets=false";  
  
    using (var sqlConnection = new SqlConnection(connectionString))  
    {  
        sqlConnection.Open();  
  
        var sqlCommand = new SqlCommand  
        {  
            Connection = sqlConnection,  
            CommandType = CommandType.StoredProcedure,  
            CommandText = "[catalog].[deploy_packages]"  
        };  
  
        var packageData = Encoding.UTF8.GetBytes(File.ReadAllText(@"C:\Test\Package.dtsx"));  
  
        // DataTable: name is the package name without extension and package_data is byte array of package.  
        var packageTable = new DataTable();  
        packageTable.Columns.Add("name", typeof(string));  
        packageTable.Columns.Add("package_data", typeof(byte[]));  
        packageTable.Rows.Add("Package", packageData);  
  
        // Set the destination project and folder which is named Folder and Project.  
        sqlCommand.Parameters.Add(new SqlParameter("@folder_name", SqlDbType.NVarChar, ParameterDirection.Input, "Folder", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@project_name", SqlDbType.NVarChar, ParameterDirection.Input, "Project", -1));  
        sqlCommand.Parameters.Add(new SqlParameter("@packages_table", SqlDbType.Structured, ParameterDirection.Input, packageTable, -1));  
  
        var result = sqlCommand.Parameters.Add("RetVal", SqlDbType.Int);  
        result.Direction = ParameterDirection.ReturnValue;  
  
        sqlCommand.ExecuteNonQuery();  
    }  
}  
  
```  
  
##  <a name="MOMApi"></a> 管理オブジェクト モデル API を使用してパッケージを配置する  
 次のコード例では、管理オブジェクト モデル API を使用してパッケージをサーバーに配置する方法を示します。  
  
```  
  
static void Main()  
 {  
     // Before deploying packages, make sure the destination project exists in SSISDB.  
     var connectionString = "Data Source=.;Integrated Security=True;MultipleActiveResultSets=false";  
     var catalogName = "SSISDB";  
     var folderName = "Folder";  
     var projectName = "Project";  
  
     // Get the folder instance.  
     var sqlConnection = new SqlConnection(connectionString);  
     var store = new Microsoft.SqlServer.Management.IntegrationServices.IntegrationServices(sqlConnection);  
     var folder = store.Catalogs[catalogName].Folders[folderName];  
  
     // Key is package name without extension and value is package binaries.  
     var packageDict = new Dictionary<string, string>();  
  
     var packageData = File.ReadAllText(@"C:\Folder\Package.dtsx");  
     packageDict.Add("Package", packageData);  
  
     // Deploy package to the destination project.  
     folder.DeployPackages(projectName, packageDict);  
 }  
  
```  
  
  