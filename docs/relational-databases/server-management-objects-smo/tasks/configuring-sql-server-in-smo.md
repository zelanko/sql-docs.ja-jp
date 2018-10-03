---
title: SMO での SQL Server の構成 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 51d2fcc8ed9f5e66d93af85483fcd7d10f96e3fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797180"
---
# <a name="configuring-sql-server-in-smo"></a>SMO での SQL Server の構成
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO では、<xref:Microsoft.SqlServer.Management.Smo.Information>オブジェクト、<xref:Microsoft.SqlServer.Management.Smo.Settings>オブジェクト、<xref:Microsoft.SqlServer.Management.Smo.UserOptions>オブジェクト、および<xref:Microsoft.SqlServer.Management.Smo.Configuration>オブジェクトには、のインスタンスの設定および情報が含まれます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、インストールされたインスタンスの動作を記述する複数のプロパティがあります。 これらのプロパティでは、スタートアップ オプション、サーバーの既定、ファイルとディレクトリ、システムとプロセッサの情報、製品とバージョン、接続情報、メモリ オプション、言語と照合順序の選択、および認証モードについて記述します。  
  
## <a name="sql-server-configuration"></a>SQL Server 構成  
 <xref:Microsoft.SqlServer.Management.Smo.Information>オブジェクトのプロパティのインスタンスに関する情報を含む[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]プロセッサやプラットフォームなど。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Settings>オブジェクトのプロパティのインスタンスに関する情報を含む[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 Mail Profile および Server Account に加え、既定のデータベース ファイルおよびディレクトリも変更することができます。 これらのプロパティは、接続が続いている間は保持されます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクト プロパティには、算術、ANSI 規格、およびトランザクションに関連する現在の接続の動作に関する情報が含まれています。  
  
 あるで表される構成オプションのセットも、<xref:Microsoft.SqlServer.Management.Smo.Configuration>オブジェクト。 これには、 **sp_configure** ストアド プロシージャによって変更可能なオプションを表すプロパティのセットが含まれています。 などのオプション**Priority Boost**、 **Recovery Interval**と**Network Packet Size**のインスタンスのパフォーマンスを制御[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 これらのオプションの多くは動的に変更できますが、場合によっては、構成した値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの再起動時に変更されることもあります。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Configuration>オブジェクトすべての構成オプションのプロパティ。 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> オブジェクトを使用すると、グローバル構成設定を変更することができます。 多くのプロパティには、最大値および最小値が設定されており、これらも <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> プロパティとして格納されます。 これらのプロパティが必要な<xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A>メソッドのインスタンスに変更をコミットする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
 すべてのオプションの設定、<xref:Microsoft.SqlServer.Management.Smo.Configuration>オブジェクトは、システム管理者によって変更する必要があります。  
  
## <a name="examples"></a>使用例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Visual Basic での SQL Server 構成オプションの変更  
 このコード例は、Visual Basic .NET で構成オプションを更新する方法を示しています。 また、指定された構成オプションの最大値と最小値についての情報を取得および表示しています。 変更が動的に行われた場合、またはのインスタンスまでに格納されている場合に、プログラムがユーザーに通知する最後に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を再起動します。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display all the configuration options.
Dim p As ConfigProperty
For Each p In srv.Configuration.Properties
    Console.WriteLine(p.DisplayName)
Next
Console.WriteLine("There are " & srv.Configuration.Properties.Count.ToString & " configuration options.")
'Display the maximum and minimum values for ShowAdvancedOptions.
Dim min As Integer
Dim max As Integer
min = srv.Configuration.ShowAdvancedOptions.Minimum
max = srv.Configuration.ShowAdvancedOptions.Maximum
Console.WriteLine("Minimum and Maximum values are " & min & " and " & max & ".")
'Modify the value of ShowAdvancedOptions and run the Alter method.
srv.Configuration.ShowAdvancedOptions.ConfigValue = 0
srv.Configuration.Alter()
'Display when the change takes place according to the IsDynamic property.
If srv.Configuration.ShowAdvancedOptions.IsDynamic = True Then
    Console.WriteLine("Configuration option has been updated.")
Else
    Console.WriteLine("Configuration option will be updated when SQL Server is restarted.")
End If
``` 
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Visual Basic での SQL Server 設定の変更  
 インスタンスに関する情報を表示するコード例[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で<xref:Microsoft.SqlServer.Management.Smo.Information>と<xref:Microsoft.SqlServer.Management.Smo.Settings>で設定を変更および<xref:Microsoft.SqlServer.Management.Smo.Settings>と<xref:Microsoft.SqlServer.Management.Smo.UserOptions>オブジェクトのプロパティ。  
  
 この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。 実行することができます、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>メソッドは、これら個別にします。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display information about the instance of SQL Server in Information and Settings.
Console.WriteLine("OS Version = " & srv.Information.OSVersion)
Console.WriteLine("State = " & srv.Settings.State.ToString)
'Display information specific to the current user in UserOptions.
Console.WriteLine("Quoted Identifier support = " & srv.UserOptions.QuotedIdentifier)
'Modify server settings in Settings.

srv.Settings.LoginMode = ServerLoginMode.Integrated
'Modify settings specific to the current connection in UserOptions.
srv.UserOptions.AbortOnArithmeticErrors = True
'Run the Alter method to make the changes on the instance of SQL Server.
srv.Alter()
```
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Visual C# での SQL Server 設定の変更  
 インスタンスに関する情報を表示するコード例[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で<xref:Microsoft.SqlServer.Management.Smo.Information>と<xref:Microsoft.SqlServer.Management.Smo.Settings>で設定を変更および<xref:Microsoft.SqlServer.Management.Smo.Settings>と<xref:Microsoft.SqlServer.Management.Smo.UserOptions>オブジェクトのプロパティ。  
  
 この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。 実行することができます、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>メソッドは、これら個別にします。  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>PowerShell での SQL Server 設定の変更  
 インスタンスに関する情報を表示するコード例[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で<xref:Microsoft.SqlServer.Management.Smo.Information>と<xref:Microsoft.SqlServer.Management.Smo.Settings>で設定を変更および<xref:Microsoft.SqlServer.Management.Smo.Settings>と<xref:Microsoft.SqlServer.Management.Smo.UserOptions>オブジェクトのプロパティ。  
  
 この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。 実行することができます、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>メソッドは、これら個別にします。  
  
```powershell 
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>PowerShell での SQL Server 構成オプションの変更  
 このコード例は、Visual Basic .NET で構成オプションを更新する方法を示しています。 また、指定された構成オプションの最大値と最小値についての情報を取得および表示しています。 変更が動的に行われた場合、またはのインスタンスまでに格納されている場合に、プログラムがユーザーに通知する最後に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を再起動します。  
  
```powershell 
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  
