---
title: "ADOMD.NET で接続を確立する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c7c3555be8e304add34cba3a8dd9f0bac4264216
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="connections-in-adomdnet"></a>ADOMD.NET での接続
  ADOMD.NET では、使用する、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトなど、分析データ ソースとの接続を開くを[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 接続が不要になったときは、その接続を明示的に閉じる必要があります。  
  
## <a name="opening-a-connection"></a>接続を開く  
 ADOMD.NET で接続を開くには、まず、有効な分析データ ソースおよびデータベースの接続文字列を指定します。 その後、そのデータ ソースへの接続を明示的に開く必要があります。  
  
### <a name="specifying-a-multidimensional-data-source"></a>多次元データ ソースの指定  
 分析データ ソースおよびデータベースを指定するには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> プロパティを設定します。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> プロパティに対して指定する接続文字列は、OLE DB 準拠の文字列です。 ADOMD.NET は、指定された接続文字列を使用して、サーバーへの接続方法を決定します。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> プロパティは、既存の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトに対して設定するか、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトのインスタンスの作成中に設定できます。 ADOMD 接続を作成する際に <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> プロパティを設定するコードの例を次に示します。  
  
```vb  
Dim advwrksConnection As New AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS")  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString)  
```  
  
```csharp  
AdomdConnection advwrksConnection = new AdomdConnection("Data Source=localhost;Catalog=AdventureWorksAS");  
System.Diagnostics.Debug.Writeline(advwrksConnection.ConnectionString);  
```  
  
### <a name="opening-a-connection-to-the-data-source"></a>データ ソースへの接続を開く  
 接続文字列を指定したら、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> メソッドを使用して接続を開く必要があります。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを開くときに、接続に対してさまざまなレベルのセキュリティを設定できます。 接続に使用されるセキュリティ レベルの値によって異なります、 **ProtectionLevel**接続文字列を設定します。 ADOMD.NET でセキュリティ保護された接続を開く方法の詳細については、次を参照してください。 [ADOMD.NET でのセキュリティで保護された接続を確立する](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-establishing-secure-connections.md)です。  
  
## <a name="working-with-a-connection"></a>接続の操作  
 開いた各接続には、ステートフルな操作をサポートするセッションが割り当てられます。 1 つのセッションを、開いている複数の接続で共有できます。 セッションを共有すると、複数のクライアントで同じコンテキストを共有できます。 詳細については、次を参照してください。[接続とセッションを ADOMD.NET での操作](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md)です。  
  
 開いた接続を使用して、メタデータとデータを取得し、コマンドを実行できます。 詳細については、次を参照してください[分析データ ソースからメタデータを取得する](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)、[分析データ ソースからのデータの取得](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-from-an-analytical-data-source.md)、および[を実行するコマンドに対して、分析データ。ソース](../../analysis-services/multidimensional-models-adomd-net-client/executing-commands-against-an-analytical-data-source.md)です。  
  
 接続が開いているときは、READ COMMITTED トランザクション内からデータやメタデータを取得し、コマンドを実行することができます。このトランザクションでは、ダーティ リードを回避するため、データの読み込み中は共有ロックが保持されます。 ただし、その場合でも、トランザクションが終了する前にデータが変更され、反復不能読み取りやファントム データとなる場合があります。 詳細については、次を参照してください。 [ADOMD.NET でのトランザクションの実行](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-performing-transactions.md)です。  
  
## <a name="closing-a-connection"></a>接続を閉じる  
 接続が不要になったらすぐに、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを明示的に閉じることをお勧めします。 使用する接続を明示的に閉じる、**閉じる**と**Dispose**のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト。  
  
 接続を明示的に閉じず、スコープから除外しただけの場合、サーバー リソースが即座に解放されず、同時実行性の高い [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クライアント アプリケーションが接続を効率的に開けない可能性があります。 接続を明示的に閉じない場合、その接続をどのように作成したかによっては、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトで使用するセッションがアクティブのままになることもあります。  
  
 セッションの詳細については、次を参照してください。[接続とセッションを ADOMD.NET での操作](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md)です。  
  
> [!IMPORTANT]  
>  **Finalize**クラスを実装するいずれかのメソッドを呼び出さないでください、**閉じる**または**Dispose**のメソッド、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>オブジェクト、またはその他のマネージ オブジェクトです。 ファイナライザーでは、実装したクラスが直接所有しているアンマネージ リソースのみ解放してください。 実装したクラスがアンマネージ リソースを所有していない場合は含まれません、 **Finalize**クラス定義内のメソッドです。  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
