---
title: SMO でリンク サーバーの使用 |Microsoft Docs
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
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57c84f885a53fd2b277fbb34c9bfecc178e0fe89
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319922"
---
# <a name="using-linked-servers-in-smo"></a>SMO でのリンク サーバーの使用
  リンク サーバーはリモート サーバー上の OLE DB データ ソースを表します。 インスタンスにリモートの OLE DB データ ソースがリンクされて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>オブジェクト。  
  
 リモート データベース サーバーの現在のインスタンスにリンクできる[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB プロバイダーを使用しています。 SMO では、リンク サーバーがによって表される、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A>プロパティのコレクションを参照する<xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin>オブジェクト。 これらのオブジェクトには、リンク サーバーとの接続の確立に必要となるログオン資格情報が格納されます。  
  
## <a name="ole-db-providers"></a>OLE DB プロバイダー  
 SMO では、インストールされた OLE DB プロバイダーは <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings> オブジェクトのコレクションで表されます。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual Studio .NET で Visual Basic SMO プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)と[Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-basic"></a>Visual Basic での OLE DB プロバイダー サーバーへのリンクの作成  
 コード例へのリンクを作成する方法を示しています、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB、異種データ ソースを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>オブジェクト。 指定して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、製品名としては、リンク サーバーでデータをアクセスを使用して、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB プロバイダー、公式の OLE DB プロバイダーであるため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBLinkedServers1](SMO How to#SMO_VBLinkedServers1)]  -->  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Visual C# での OLE DB プロバイダー サーバーへのリンクの作成  
 コード例へのリンクを作成する方法を示しています、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB、異種データ ソースを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>オブジェクト。 指定して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、製品名としては、リンク サーバーでデータをアクセスを使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB プロバイダー、公式の OLE DB プロバイダーであるため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
```  
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
 コード例へのリンクを作成する方法を示しています、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB、異種データ ソースを使用して、<xref:Microsoft.SqlServer.Management.Smo.LinkedServer>オブジェクト。 指定して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、製品名としては、リンク サーバーでデータをアクセスを使用して、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client OLE DB プロバイダー、公式の OLE DB プロバイダーであるため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
```  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
