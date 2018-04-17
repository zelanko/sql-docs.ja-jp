---
title: ユーザー、ロール、およびログインの管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- logins [SMO]
- roles [SMO]
- users [SMO]
ms.assetid: 74e411fa-74ed-49ec-ab58-68c250f2280e
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: bf373c1fb741dc21686340e898ce994d9b0b8cc4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="managing-users-roles-and-logins"></a>ユーザー、ロール、およびログインの管理
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  SMO では、<xref:Microsoft.SqlServer.Management.Smo.Login> オブジェクトでログインが表現されます。 ログオンが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に存在する場合、サーバー ロールに追加することができます。 サーバーの役割がによって表される、<xref:Microsoft.SqlServer.Management.Smo.ServerRole>オブジェクト。 データベース ロールは <xref:Microsoft.SqlServer.Management.Smo.DatabaseRole> オブジェクトで表現され、アプリケーション ロールは <xref:Microsoft.SqlServer.Management.Smo.ApplicationRole> オブジェクトで表現されます。  
  
 プロパティとして、サーバー レベルに関連付けられている権限が表示されている、<xref:Microsoft.SqlServer.Management.Smo.ServerPermission>オブジェクト。 サーバー レベル権限は、個々のログオン アカウントに対して、許可、拒否、取り消しを行うことができます。  
  
 各<xref:Microsoft.SqlServer.Management.Smo.Database>オブジェクトには、<xref:Microsoft.SqlServer.Management.Smo.UserCollection>データベースですべてのユーザーを指定するオブジェクト。 各ユーザーはログオンに関連付けられています。 1 つのログオンを 2 つ以上のデータベース内のユーザーに関連付けることもできます。 <xref:Microsoft.SqlServer.Management.Smo.Login>オブジェクトの<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A>メソッドは、ログオンに関連付けられているすべてのデータベースのすべてのユーザーの一覧を使用することができます。 または、<xref:Microsoft.SqlServer.Management.Smo.User> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> プロパティで、ユーザーに関連付けられたログオンを指定します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースでは、ユーザーが特定のタスクを実行することのできるデータベース レベルの権限のセットを指定するロールもあります。 サーバー ロールと異なり、データベース ロールは固定されていません。 データベース ロールは、作成、変更、および削除を行うことができます。 権限およびユーザーは、データベースに割り当てて、一括管理することができます。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C を作成する&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="enumerating-logins-and-associated-users-in-visual-c"></a>Visual C# でのログインおよび関連付けられたユーザーの列挙  
 データベース内の各ユーザーは、ログオンに関連付けられています。 ログオンは 2 つ以上のデータベース内のユーザーに関連付けることもできます。 コード例では、<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> メソッドを呼び出して、ログオンに関連付けられているすべてのデータベース ユーザーをリストする方法を示します。 例では、ログオンおよびユーザーの作成、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベースを列挙するマッピング情報があるかどうかを確認します。  
  
```csharp  
{   
Server srv = new Server();   
//Iterate through each database and display.   
  
foreach ( Database db in srv.Databases) {   
   Console.WriteLine("========");   
   Console.WriteLine("Login Mappings for the database: " + db.Name);   
   Console.WriteLine(" ");   
   //Run the EnumLoginMappings method and return details of database user-login mappings to a DataTable object variable.   
   DataTable d;  
   d = db.EnumLoginMappings();   
   //Display the mapping information.   
   foreach (DataRow r in d.Rows) {   
      foreach (DataColumn c in r.Table.Columns) {   
         Console.WriteLine(c.ColumnName + " = " + r[c]);   
      }   
      Console.WriteLine(" ");   
   }   
}   
}  
```  
  
## <a name="enumerating-logins-and-associated-users-in-powershell"></a>PowerShell でのログインおよび関連付けられたユーザーの列挙  
 データベース内の各ユーザーは、ログオンに関連付けられています。 ログオンは 2 つ以上のデータベース内のユーザーに関連付けることもできます。 コード例では、<xref:Microsoft.SqlServer.Management.Smo.Login.EnumDatabaseMappings%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Login> メソッドを呼び出して、ログオンに関連付けられているすべてのデータベース ユーザーをリストする方法を示します。 例では、ログオンおよびユーザーの作成、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]データベースを列挙するマッピング情報があるかどうかを確認します。  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\Default\Databases  
  
#Iterate through all databases  
 foreach ($db in Get-ChildItem)  
 {  
 "====="  
 "Login Mappings for the database: "+ $db.Name  
  
 #get the datatable containing the mapping from the smo database oject  
 $dt = $db.EnumLoginMappings()  
  
 #display the results  
 foreach($row in $dt.Rows)  
     {  
        foreach($col in $row.Table.Columns)  
      {  
        $col.ColumnName + "=" + $row[$col]  
       }  
  
     }  
 }  
```  
  
## <a name="managing-roles-and-users"></a>ロールとユーザーの管理  
 このサンプルでは、ロールおよびユーザーの管理方法を示します。 このサンプルを実行するには、次のアセンブリを参照する必要があります。  
  
-   Microsoft.SqlServer.Smo.dll  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
-   Microsoft.SqlServer.ConnectionInfo.dll  
  
-   Microsoft.SqlServer.SqlEnum.dll  
  
```csharp  
using Microsoft.SqlServer.Management.Smo;  
using System;  
  
public class A {  
   public static void Main() {  
      Server svr = new Server();  
      Database db = new Database(svr, "TESTDB");  
      db.Create();  
  
      // Creating Logins  
      Login login = new Login(svr, "Login1");  
      login.LoginType = LoginType.SqlLogin;  
      login.Create("password@1");  
  
      Login login2 = new Login(svr, "Login2");  
      login2.LoginType = LoginType.SqlLogin;  
      login2.Create("password@1");  
  
      // Creating Users in the database for the logins created  
      User user1 = new User(db, "User1");  
      user1.Login = "Login1";  
      user1.Create();  
  
      User user2 = new User(db, "User2");  
      user2.Login = "Login2";  
      user2.Create();  
  
      // Creating database permission Sets  
      DatabasePermissionSet dbPermSet = new DatabasePermissionSet(DatabasePermission.AlterAnySchema);  
      dbPermSet.Add(DatabasePermission.AlterAnyUser);  
  
      DatabasePermissionSet dbPermSet2 = new DatabasePermissionSet(DatabasePermission.CreateType);  
      dbPermSet2.Add(DatabasePermission.CreateSchema);  
      dbPermSet2.Add(DatabasePermission.CreateTable);  
  
      // Creating Database roles  
      DatabaseRole role1 = new DatabaseRole(db, "Role1");  
      role1.Create();  
  
      DatabaseRole role2 = new DatabaseRole(db, "Role2");  
      role2.Create();  
  
      // Granting Database Permission Sets to Roles  
      db.Grant(dbPermSet, role1.Name);  
      db.Grant(dbPermSet2, role2.Name);  
  
      // Adding members (Users / Roles) to Role  
      role1.AddMember("User1");  
  
      role2.AddMember("User2");  
  
      // Role1 becomes a member of Role2  
      role2.AddMember("Role1");  
  
      // Enumerating through explicit permissions granted to Role1  
      // enumerates all database permissions for the Grantee  
      DatabasePermissionInfo[] dbPermsRole1 = db.EnumDatabasePermissions("Role1");     
      foreach (DatabasePermissionInfo dbp in dbPermsRole1) {  
         Console.WriteLine(dbp.Grantee + " has " + dbp.PermissionType.ToString() + " permission.");  
      }  
      Console.WriteLine(" ");  
   }  
}  
```
  
  
