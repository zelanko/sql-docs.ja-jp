---
title: エンドポイントの実装 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17e154743d221cfd4a2070c56634c6364a910afb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081641"
---
# <a name="implementing-endpoints"></a>エンドポイントの実装
  エンドポイントは、要求をネイティブにリッスンできるサービスです。 SMO を使用してさまざまな種類のエンドポイントをサポートする、<xref:Microsoft.SqlServer.Management.Smo.Endpoint>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> オブジェクトのインスタンスを作成し、そのプロパティを設定することで、特定のプロトコルを必要とする特定の種類のペイロードを処理するためのエンドポイント サービスを作成できます。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Endpoint>オブジェクトは、上の次のペイロードの種類を指定するために使用できます。  
  
-   データベース ミラーリング  
  
-   SOAP (SOAP エンドポイントは、[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] および以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされます)  
  
-   Service Broker  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 また、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> プロパティを使用して、サポートされている次の 2 つのプロトコルを指定することができます。  
  
-   HTTP プロトコル  
  
-   TCP プロトコル  
  
 ペイロードの種類を指定すると、実際のペイロード設定できるを使用して、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A>オブジェクト プロパティです。 <xref:Microsoft.SqlServer.Management.Smo.Payload> オブジェクト プロパティは、プロパティを変更できる、指定された種類のペイロード オブジェクトへの参照を提供します。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> オブジェクトに対して、ミラーリング ロール、および暗号化が有効であるかどうかを指定する必要があります。 <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload>オブジェクトには、メッセージの転送、許可される接続の最大数と、認証モードに関する情報が必要です。 <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> オブジェクトでは、さまざまなプロパティの設定が必要です。これには、クライアントが使用できる SOAP ペイロード メソッド (ストアド プロシージャおよびユーザー定義関数) を指定する、<xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> オブジェクト プロパティなどがあります。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> オブジェクト プロパティを使用すると、<xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> プロパティで指定された型のプロトコル オブジェクトを参照して、実際のプロトコルを設定することができます。 <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> オブジェクトには、制限された IP アドレス、ポート、Web サイト、および認証情報のリストが必要です。 <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol>オブジェクトでは、制限された IP アドレスとポート情報の一覧も必要です。  
  
 エンドポイントを作成して定義を完了したら、データベース ユーザー、グループ、ロール、およびログオンに対して、アクセスの許可、取り消し、および拒否を行うことができます。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual Studio .NET で Visual Basic SMO プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)と[Visual C の作成&#35;Visual Studio .NET での SMO プロジェクト](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)します。  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a>Visual Basic でのデータベース ミラーリング エンドポイント サービスの作成  
 コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。 これは、データベース ミラーを作成する前に必要な操作です。 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a>Visual C# でのデータベース ミラーリング エンドポイント サービスの作成  
 コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。 これは、データベース ミラーを作成する前に必要な操作です。 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。  
  
```  
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a>PowerShell でのデータベース ミラーリング エンドポイント サービスの作成  
 コード例では、SMO でデータベース ミラーリング エンドポイントを作成する方法を示します。 これは、データベース ミラーを作成する前に必要な操作です。 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Database> プロパティおよびその他のプロパティを使用して、データベース ミラーを作成します。  
  
```  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a>関連項目  
 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
