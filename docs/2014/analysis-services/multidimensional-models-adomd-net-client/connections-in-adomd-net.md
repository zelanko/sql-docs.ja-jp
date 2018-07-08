---
title: ADOMD.NET での接続を確立する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- opening connections
- closing connections
- connections [ADOMD.NET]
- ADOMD.NET, connections
ms.assetid: 7b9610f5-6641-42cc-af4e-bd35771913d1
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d7bf4529df77545cf2d0acf69af5d0b570ef750
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165303"
---
# <a name="establishing-connections-in-adomdnet"></a>ADOMD.NET での接続の確立
  ADOMD.NET では使用して、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトなど、分析データ ソース接続を開く[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース。 接続が不要になったときは、その接続を明示的に閉じる必要があります。  
  
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
 接続文字列を指定したら、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> メソッドを使用して接続を開く必要があります。 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを開くときに、接続に対してさまざまなレベルのセキュリティを設定できます。 接続に対して使用されるセキュリティ レベルは、`ProtectionLevel` 接続文字列の設定値によって異なります。 ADOMD.NET でのセキュリティ保護された接続を開く方法の詳細については、次を参照してください。 [ADOMD.NET でのセキュリティで保護された接続を確立する](connections-in-adomd-net-establishing-secure-connections.md)します。  
  
## <a name="working-with-a-connection"></a>接続の操作  
 開いた各接続には、ステートフルな操作をサポートするセッションが割り当てられます。 1 つのセッションを、開いている複数の接続で共有できます。 セッションを共有すると、複数のクライアントで同じコンテキストを共有できます。 詳細については、次を参照してください。[接続とセッションを ADOMD.NET での操作](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md)します。  
  
 開いた接続を使用して、メタデータとデータを取得し、コマンドを実行できます。 詳細については、次を参照してください[分析データ ソースからメタデータを取得する](retrieving-metadata-from-an-analytical-data-source.md)、[分析データ ソースからのデータの取得](retrieving-data-from-an-analytical-data-source.md)、および[を実行するコマンドに対して、分析データ。ソース](executing-commands-against-an-analytical-data-source.md)します。  
  
 接続が開いているときは、READ COMMITTED トランザクション内からデータやメタデータを取得し、コマンドを実行することができます。このトランザクションでは、ダーティ リードを回避するため、データの読み込み中は共有ロックが保持されます。 ただし、その場合でも、トランザクションが終了する前にデータが変更され、反復不能読み取りやファントム データとなる場合があります。 詳細については、次を参照してください。 [ADOMD.NET でトランザクションの実行](../../relational-databases/native-client-ole-db-transactions/transactions.md)します。  
  
## <a name="closing-a-connection"></a>接続を閉じる  
 接続が不要になったらすぐに、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを明示的に閉じることをお勧めします。 接続を明示的に閉じるには、`Close` オブジェクトの `Dispose` および <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> メソッドを使用します。  
  
 接続を明示的に閉じず、スコープから除外しただけの場合、サーバー リソースが即座に解放されず、同時実行性の高い [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] クライアント アプリケーションが接続を効率的に開けない可能性があります。 接続を明示的に閉じない場合、その接続をどのように作成したかによっては、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトで使用するセッションがアクティブのままになることもあります。  
  
 セッションの詳細については、次を参照してください。[接続とセッションを ADOMD.NET での操作](../multidimensional-models-adomd-net-client/connections-in-adomd-net-working-with-connections-and-sessions.md)します。  
  
> [!IMPORTANT]  
>  実装したクラスの `Finalize` メソッド内で <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクト、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> オブジェクト、またはその他のマネージド オブジェクトの `Close` メソッドまたは `Dispose` メソッドを呼び出さないでください。 ファイナライザーでは、実装したクラスが直接所有しているアンマネージ リソースのみ解放してください。 実装したクラスがアンマネージ リソースを所有していない場合、`Finalize` メソッドをクラス定義に含めないでください。  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET クライアント プログラミング](adomd-net-client-programming.md)  
  
  
