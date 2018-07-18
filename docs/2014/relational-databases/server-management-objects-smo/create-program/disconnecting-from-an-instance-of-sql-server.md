---
title: SQL Server のインスタンスからの切断 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a232aefef8293ef84b99dce5aa3864e9702dab1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225262"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>SQL Server のインスタンスからの切断
  手動で閉じたり切断[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理オブジェクト (SMO) オブジェクトは必要ありません。 接続を開いたり閉じたりする操作は、必要に応じて行われます。  
  
## <a name="connection-pooling"></a>接続のプール  
 ときに、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A>メソッドが呼び出されると、接続が自動的に解放されません。 接続プールに接続を解放するには、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> メソッドを明示的に呼び出す必要があります。 また、プールされていない接続を要求することもできます。 これを行うには、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> オブジェクトを参照する <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> プロパティの <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティを設定します。  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>RMO の SQL Server のインスタンスからの切断  
 RMO を使ったプログラミングでサーバー接続を閉じる方法は、SMO とは若干異なります。  
  
 によって、RMO オブジェクトのサーバー接続が維持されるため、<xref:Microsoft.SqlServer.Management.Common.ServerConnection>オブジェクトのインスタンスから切断するときにも、このオブジェクトが使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] RMO を使用してプログラミングする場合。 使用して接続を終了する、<xref:Microsoft.SqlServer.Management.Common.ServerConnection>オブジェクトを呼び出し、 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> RMO オブジェクトのメソッド。 接続が閉じられた後は、RMO オブジェクトを使用することはできません。  
  
## <a name="example"></a>例  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Visual Basic で SMO オブジェクトを閉じたり切断する処理を行う方法  
 このコード例を設定して、プールされていない接続を要求する方法を示しています、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>オブジェクト プロパティです。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Visual C# で SMO オブジェクトを閉じたり切断する処理を行う方法  
 このコード例を設定して、プールされていない接続を要求する方法を示しています、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A>オブジェクト プロパティです。  
  
```  
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
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
