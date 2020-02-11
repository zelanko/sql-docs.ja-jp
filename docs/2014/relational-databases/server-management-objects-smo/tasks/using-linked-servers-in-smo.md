---
title: SMO でのリンクサーバーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f62efaa1550ea0b9e68ce4914e4852612d53f48
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72781996"
---
# <a name="using-linked-servers-in-smo"></a>SMO でのリンク サーバーの使用
  リンク サーバーはリモート サーバー上の OLE DB データ ソースを表します。 リモート OLE DB データ ソースは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクトを使用して <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> のインスタンスにリンクされます。  
  
 リモートデータベースサーバーは、OLE DB プロバイダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、の現在のインスタンスにリンクすることができます。 SMO では、リンク サーバーは <xref:Microsoft.SqlServer.Management.Smo.LinkedServer> オブジェクトで表現されます。 
  <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> プロパティは <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> オブジェクトのコレクションを参照します。 これらのオブジェクトには、リンク サーバーとの接続の確立に必要となるログオン資格情報が格納されます。  
  
## <a name="ole-db-providers"></a>OLE DB プロバイダー  
 SMO では、インストールされた OLE DB プロバイダーは <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> オブジェクトのコレクションで表されます。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Visual Basic での OLE DB プロバイダー サーバーへのリンクの作成  
 コード例では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクトを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> OLE DB 異種データ ソースへのリンクを作成する方法を示しています。 製品名として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定することで、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用の正式な OLE DB プロバイダーである [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB プロバイダーを使用して、リンク サーバーのデータへのアクセスが行われます。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Visual C# での OLE DB プロバイダー サーバーへのリンクの作成  
 コード例では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクトを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> OLE DB 異種データ ソースへのリンクを作成する方法を示しています。 製品名として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定することで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用の正式な OLE DB プロバイダーである [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB プロバイダーを使用して、リンク サーバーのデータへのアクセスが行われます。  
  
```csharp
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>PowerShell での OLE DB プロバイダー サーバーへのリンクの作成  
 コード例では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オブジェクトを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer> OLE DB 異種データ ソースへのリンクを作成する方法を示しています。 製品名として [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を指定することで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 用の正式な OLE DB プロバイダーである [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Client OLE DB プロバイダーを使用して、リンク サーバーのデータへのアクセスが行われます。  
  
```powershell
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -ArgumentList $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.
$lsvr.ProductName = "SQL Server"
  
#Create the Database Object  
$lsvr.Create()
```  
