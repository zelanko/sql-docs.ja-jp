---
title: SQL Server のインスタンスからの切断 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: fffcb2d7d9ef6f9d8b0f3e13717985f7a8032047
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39555442"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>SQL Server のインスタンスからの切断
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  手動で閉じたり切断[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) オブジェクトは必要ありません。 接続を開いたり閉じたりする操作は、必要に応じて行われます。  
  
## <a name="connection-pooling"></a>接続のプール  
 ときに、 [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect)メソッドが呼び出されると、接続が自動的に解放されません。 [切断](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect)接続プールへの接続を解放するメソッドを明示的に呼び出す必要があります。 また、プールされていない接続を要求することもできます。 これを行う、 [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection)のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>を参照するプロパティ、 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)オブジェクト。  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>RMO の SQL Server のインスタンスからの切断  
 RMO を使ったプログラミングでサーバー接続を閉じる方法は、SMO とは若干異なります。  
  
 によって、RMO オブジェクトのサーバー接続が維持されるため、 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)オブジェクトのインスタンスから切断するときにも、このオブジェクトが使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] RMO を使用してプログラミングする場合。 使用して接続を終了する、 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)オブジェクトを呼び出し、[切断](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect)RMO オブジェクトのメソッド。 接続が閉じられた後は、RMO オブジェクトを使用することはできません。  
  
## <a name="example"></a>例  
提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Visual Basic で SMO オブジェクトを閉じたり切断する処理を行う方法  
 このコード例を設定して、プールされていない接続を要求する方法を示しています、 [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection)のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>オブジェクト プロパティです。  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Visual C# で SMO オブジェクトを閉じたり切断する処理を行う方法  
 このコード例を設定して、プールされていない接続を要求する方法を示しています、 [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection)のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>オブジェクト プロパティです。  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
