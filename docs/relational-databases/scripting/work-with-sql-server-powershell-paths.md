---
title: "SQL Server PowerShell パスの操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# SQL Server PowerShell パスの操作
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロバイダーのパスでノードに移動した後、ノードに関連付けられている [!INCLUDE[ssDE](../../includes/ssde-md.md)] 管理オブジェクトのメソッドとプロパティを使用して、作業を実行したり、情報を取得したりできます。  
  
1.  [はじめに](#BeforeYouBegin)  
  
2.  **パス ノードに関する作業:**  [メソッドとプロパティの一覧表示](#ListPropMeth)、 [メソッドとプロパティの使用](#UsePropMeth)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロバイダーのパスでノードに移動した後、2 種類の操作を実行できます。  
  
-   **Rename-Item** など、ノードを操作する Windows PowerShell コマンドレットを実行できます。  
  
-   関連付けられた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト モデル (SMO など) のメソッドを呼び出すことができます。 たとえば、パスで <xref:Microsoft.SqlServer.Management.Smo.Database> ノードに移動すると、 クラスのメソッドとプロパティを使用できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロバイダーは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスのオブジェクトを管理するために使用されます。 データベース内のデータの処理には使用されません。 テーブルまたはビューに移動した場合に、プロバイダーを使用してデータの選択、挿入、更新、または削除を行うことはできません。 テーブルおよびビューのデータを Windows PowerShell 環境からクエリまたは変更するには、**Invoke-Sqlcmd** コマンドレットを使用します。 詳細については、「[Invoke-Sqlcmd コマンドレット](../../powershell/invoke-sqlcmd-cmdlet.md)」を参照してください。  
  
##  <a name="ListPropMeth"></a> メソッドとプロパティの一覧表示  
 **メソッドとプロパティの一覧表示**  
  
 特定のオブジェクトまたはオブジェクト クラスで使用できるメソッドとプロパティを表示するには、**Get-Member** コマンドレットを使用します。  
  
### 例: メソッドとプロパティの一覧表示  
 次の例では、Windows PowerShell 変数に SMO <xref:Microsoft.SqlServer.Management.Smo.Database> クラスを設定し、メソッドとプロパティを一覧表示します。  
  
```  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member –Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 また、**Get-Member** を使用して、Windows PowerShell パスの終了ノードに関連付けられているメソッドとプロパティを一覧表示することもできます。  
  
 次の例では、SQLSERVER: パスで Databases ノードに移動し、コレクションのプロパティを一覧表示します。  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 次の例では、SQLSERVER: パスで AdventureWorks2012 ノードに移動し、オブジェクトのプロパティを一覧表示します。  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="UsePropMeth"></a> メソッドとプロパティの使用  
 **SMO メソッドとプロパティの使用**  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロバイダー パスからオブジェクトの操作を実行するには、SMO メソッドとプロパティを使用します。  
  
### 例: メソッドとプロパティの使用  
 次の例では、SMO の **Schema** プロパティを使用して、AdventureWorks2012 の Sales スキーマからテーブルの一覧を取得します。  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | where {$_.Schema -eq "Sales"}  
```  
  
 次の例では、SMO の **Script** メソッドを使用して、AdventureWorks2012 でビューを再作成するために必要な **CREATE VIEW** ステートメントを含むスクリプトを生成します。  
  
```  
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 次の例では、SMO の **Create** メソッドを使用してデータベースを作成し、 **State** プロパティを使用してデータベースが存在するかどうかを確認します。  
  
```  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## 参照  
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell パスの移動](../../relational-databases/scripting/navigate-sql-server-powershell-paths.md)   
 [URN から SQL Server プロバイダー パスへの変換](../../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  