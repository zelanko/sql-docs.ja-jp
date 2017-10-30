---
title: "プログラムによるリモート パッケージの実行の読み込みと |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9890f84a983b07534713fe5ec8c547f01e5b2264
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="loading-and-running-a-remote-package-programmatically"></a>プログラムによるリモート パッケージの読み込みと実行
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされていないローカル コンピューターからリモート パッケージを実行するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされているリモート コンピューター上でパッケージが実行されるように、パッケージを起動します。 この操作を行うには、ローカル コンピューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、Web サービス、またはリモート コンポーネントを使用して、リモート コンピューターでパッケージを起動します。 ローカル コンピューターから直接リモート パッケージを起動しようとすると、パッケージがローカル コンピューターに読み込まれ、ローカル コンピューターから実行されます。 ローカル コンピューターに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされていない場合、パッケージは実行されません。  
  
> [!NOTE]  
>  外部でパッケージを実行することはできません[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を持たないクライアント コンピューターで[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、インストールされていると、条件、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ライセンス可能性がありますいないをインストールできます[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]追加のコンピューターにします。 ([!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はサーバー コンポーネントであるため、クライアント コンピューターに再配布できません)。  
  
 また、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされているローカル コンピューターからリモート パッケージを実行することもできます。 詳細については、次を参照してください。[の読み込みとローカル パッケージをプログラムによって実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)です。  
  
##  <a name="top"></a>リモート コンピューターでリモート パッケージの実行  
 上で説明しましたが、リモート サーバーでリモート パッケージを実行する方法は複数あります。  
  
-   [SQL Server エージェントを使用してプログラムを実行するリモート パッケージ](#agent)  
  
-   [Web サービスまたはリモート コンポーネントを使用してプログラムを実行するリモート パッケージ](#service)  
  
 このトピックの読み込み、パッケージの保存に使用されるほとんどすべてのメソッドへの参照が必要、 **Microsoft.SqlServer.ManagedDTS**アセンブリ。 例外を実行するためには、このトピックに示されている ADO.NET アプローチ、 **sp_start_job**ストアド プロシージャへの参照のみを必要とする**System.Data**です。 参照を追加した後、 **Microsoft.SqlServer.ManagedDTS**インポート、新しいプロジェクト内のアセンブリ、<xref:Microsoft.SqlServer.Dts.Runtime>を持つ名前空間、**を使用して**または**Imports**ステートメント。  
  
###  <a name="agent"></a>SQL Server エージェントを使用して、サーバーでリモート パッケージをプログラムで実行するには  
 次のコード例では、プログラムで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して、サーバー上のリモート パッケージを実行する方法を示します。 コード サンプルは、システム ストアド プロシージャを呼び出す**sp_start_job**、起動し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブ。 プロシージャによって開始されるジョブの名前は `RunSSISPackage` で、このジョブはリモート コンピューターに保存されています。 その後、`RunSSISPackage` ジョブにより、リモート コンピューターでパッケージが実行されます。  
  
> [!NOTE]  
>  戻り値、 **sp_start_job**ストアド プロシージャは、ストアド プロシージャが開始できるかどうかを示す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブが正常にします。 この戻り値は、パッケージが成功したか失敗したかを示しません。  
  
 実行されるパッケージのトラブルシューティングについて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブは、Microsoft の記事を参照してください。 [SQL Server エージェント ジョブ ステップから SSIS パッケージを呼び出したときに、SSIS パッケージは実行されません](http://support.microsoft.com/kb/918760)です。  
  
### <a name="sample-code"></a>サンプル コード  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
###  <a name="service"></a>Web サービスまたはリモート コンポーネントを使用してプログラムを実行するリモート パッケージ  
 上記のサーバー上でプログラムによってパッケージを実行するためのソリューションでは、サーバー上にカスタム コードを用意する必要はありません。 ただし、SQL Server エージェントに依存せずにパッケージを実行するソリューションが好ましいこともあります。 次の例では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージをローカルで起動するためにサーバー上で作成できる Web サービスと、この Web サービスをクライアント コンピューターから呼び出すために使用できるテスト アプリケーションを示します。 Web サービスではなくリモート コンポーネントを作成する場合は、リモート コンポーネントではほとんどの変更に同じコード ロジックを使用することができます。 ただし、リモート コンポーネントを使用する場合は、Web サービスよりも広範な設定が必要になることがあります。  
  
> [!IMPORTANT]  
>  認証および承認が既定の設定である場合、Web サービスには一般に SQL Server またはファイル システムにアクセスしてパッケージを読み込み、実行するための十分な権限がありません。 認証と承認の設定を構成して、Web サービスを適切なアクセス許可を割り当てる必要があります、 **web.config**ファイル サービスおよび適切なデータベースとファイル システム アクセス許可を割り当てます。 Web、データベース、およびファイル システムの権限の詳細については、このトピックでは説明しません。  
  
> [!IMPORTANT]  
>  メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.Application>だけをサポートして SSIS パッケージ ストアを作業用のクラス"です。"、localhost、またはサーバーがローカル サーバーの名前。 "(local)" は使用できません。  
  
### <a name="sample-code"></a>サンプル コード  
 次のコード例では、Web サービスを作成およびテストする方法を示します。  
  
#### <a name="creating-the-web-service"></a>Web サービスの作成  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、ファイルや SQL Server から直接読み込んだり、SSIS パッケージ ストアから読み込んだりすることができます。SSIS パッケージ ストアは、SQL Server および特別なファイル システム フォルダー内のパッケージ ストレージを管理します。 このサンプルを使用してすべての利用可能なオプションをサポートする、 **Select Case**または**切り替える**パッケージを起動するための適切な構文を選択し、入力引数を連結する構造体適当に。 LaunchPackage Web サービス メソッドは、クライアント コンピューターで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリへの参照が不要になるように、パッケージの実行結果を <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値ではなく、整数として返します。  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a>プログラムによってサーバー上でパッケージを実行するための Web サービスを作成するには  
  
1.  Visual Studio を開き、任意のプログラミング言語で Web サービス プロジェクトを作成します。 サンプル コードでは、プロジェクトに LaunchSSISPackageService という名前を使用します。  
  
2.  参照を追加**Microsoft.SqlServer.ManagedDTS**を追加し、 **Imports**または**を使用して**ステートメントのコード ファイルを**Microsoft.SqlServer.Dts.Runtime**名前空間。  
  
3.  LaunchPackage Web サービス メソッドのサンプル コードをクラスに貼り付けます  (このサンプルはコード ウィンドウの内容全体を表しています)。  
  
4.  LaunchPackage メソッドの入力引数に既存のパッケージを指し示す一連の有効な値を指定することにより、Web サービスをビルドしてテストします。 たとえば、package1.dtsx がサーバーの C:\My Packages に格納されている場合、sourceType の値として "file"、sourceLocation の値として "C:\My Packages"、packageName の値として "package1" (拡張子なし) を渡します。  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a>Web サービスのテスト  
 次のサンプル コンソール アプリケーションでは、Web サービスを使用してパッケージを実行します。 Web サービスの LaunchPackage メソッドは、クライアント コンピューターで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリへの参照が不要になるように、パッケージの実行結果を <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値ではなく、整数として返します。 このサンプルでは、実行結果を報告するために、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値を反映する値を持つプライベート列挙を作成します。  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a>Web サービスをテストするためのコンソール アプリケーションを作成するには  
  
1.  Visual Studio で任意のプログラミング言語を使用して、新しいコンソール アプリケーションを、Web サービス プロジェクトと同じソリューションに追加します。 サンプル コードでは、プロジェクトに LaunchSSISPackageTest という名前を使用します。  
  
2.  新しいコンソール アプリケーションをソリューションのスタートアップ プロジェクトとして設定します。  
  
3.  Web サービス プロジェクトの Web 参照を追加します。 必要に応じて、Web サービス プロキシ オブジェクトに割り当てた名前に合わせて、サンプル コードの変数宣言を調整します。  
  
4.  Main ルーチンとプライベート列挙のサンプル コードをコードに貼り付けます  (このサンプルはコード ウィンドウの内容全体を表しています)。  
  
5.  LaunchPackage メソッドを呼び出すコード行を編集し、入力引数に既存のパッケージを指し示す一連の有効な値を指定します。 たとえば、package1.dtsx がサーバーの C:\My Packages に格納されている場合、`sourceType` の値として "file"、`sourceLocation` の値として "C:\My Packages"、`packageName` の値として "package1" (拡張子なし) を渡します。  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  
## <a name="external-resources"></a>外部リソース  
  
-   ビデオ、[する方法: SQL Server エージェント (SQL Server ビデオ) を使用して、SSIS パッケージの実行を自動化](http://technet.microsoft.com/sqlserver/ff686764.aspx)technet.microsoft.com の  
  
## <a name="see-also"></a>参照  
 [ローカルおよびリモート実行の相違点を理解します。](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [読み込みと、プログラムによるローカル パッケージの実行](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [ローカル パッケージの出力の読み込み](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  

