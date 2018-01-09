---
title: "接続とセッションを ADOMD.NET での操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- sessions [ADOMD.NET]
- connections [ADOMD.NET]
ms.assetid: 72b43c06-f3e4-42c3-a696-4a3419c3b884
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46135ecf59b66a3e742d3241489e1967152ad952
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="connections-in-adomdnet---working-with-connections-and-sessions"></a>ADOMD.NET で接続とセッションの操作での接続
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Xml for Analysis (XMLA) では、セッションは、分析データにアクセス中に、ステートフルな操作のサポートを提供します。 セッションは、分析データ ソースに対して実行するコマンドおよびトランザクションのスコープとコンテキストを決定します。 セッションを管理するために使用する XMLA 要素は[BeginSession](../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)、[セッション](../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)、および[EndSession](../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)です。  
  
 ADOMD.NET はこれらの XMLA セッション要素を使用して、セッションを開始し、クエリの実行やデータの取得を行い、セッションを閉じます。  
  
## <a name="starting-a-session"></a>セッションの開始  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> オブジェクトの <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> プロパティには、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトに関連付けられたアクティブなセッションの ID が格納されています。 このプロパティを正しく使用することで、クライアントとサーバー両方のステートフル性をアプリケーションで効率的に制御することができます。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> メソッドを呼び出す際、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> プロパティに有効なセッション ID が設定されていないと、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトはプロバイダーに新しいセッション ID を要求します。 ADOMD.NET、XMLA を送信することによって、セッションを開始する**BeginSession**ヘッダーをプロバイダー。 セッションの開始に成功すると、ADOMD.NET は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> プロパティの値を、新たに作成したセッションのセッション ID に設定します。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> メソッドを呼び出す際、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> プロパティに有効なセッション ID が設定されている場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトは指定されたセッションに接続しようとします。  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトが指定されたセッションに接続できない場合、またはプロバイダーがセッションをサポートしない場合は、例外がスローされます。  
  
> [!NOTE]  
>  ADOMD.NET でセッションを作成した後、複数の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトをその単一のアクティブなセッションに接続することも、単一の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトをそのセッションから接続解除して別のセッションに再接続することもできます。  
  
## <a name="working-in-a-session"></a>セッションでの作業  
 ADOMD.NET 接続した後、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト有効なセッションを ADOMD.NET には、XMLA は送信**セッション**ヘッダーのデータまたはメタデータがアプリケーションによって行われたすべての要求を使用してプロバイダーをします。 すべての要求のセッション ID が、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A> プロパティの値に設定されます。  
  
 セッションが有効な状態で維持されるかどうかは、セッション ID で保証されるわけではありせん。 セッションが期限切れになった場合 (たとえば、タイムアウトが発生するか、接続が失われた場合)、プロバイダーはそのセッションの処理を終了してロールバックすることを選択できます。 その場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトが行うそれ以降のすべてのメソッド呼び出しは例外をスローします。 セッションが期限切れになったときではなく、次の要求がプロバイダーに送信されるときのみ例外がスローされるため、アプリケーションは、プロバイダーからデータまたはメタデータを取得するときにはいつでもこれらの例外を処理できる必要があります。  
  
## <a name="closing-a-session"></a>セッションの終了  
 場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A>の値を指定せずにメソッドが呼び出されて、 *endSession*パラメーター、または、 *endSession*パラメーターが true の場合、両方への接続、セッションとセッションに設定関連付けられている、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトが閉じられました。 ADOMD.NET、XMLA の送信セッションを閉じる、 **EndSession**セッション ID を使用して、プロバイダーにヘッダーの値に設定、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.SessionID%2A>プロパティです。  
  
 場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Close%2A>メソッドが呼び出された、 *endSession*パラメーターを False に設定に関連付けられているセッション、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトがアクティブなは残りますが、セッションへの接続が閉じられます。  
  
## <a name="example-of-managing-a-session"></a>セッション管理の例  
 次の例では、接続を開いてセッションを作成し、セッションを ADOMD.NET で開いた状態で接続を閉じます。  
  
```vb  
Public Function CreateSession(ByVal connectionString As String) As String  
    Dim strSessionID As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' First, try to connect to the specified data source.  
        ' If the connection string is not valid, or if the specified  
        ' provider does not support sessions, an exception is thrown.  
        objConnection.ConnectionString = connectionString  
        objConnection.Open()  
  
        ' Now that the connection is open, retrieve the new  
        ' active session ID.  
        strSessionID = objConnection.SessionID  
        ' Close the connection, but leave the session open.  
        objConnection.Close(False)  
        Return strSessionID  
  
    Finally  
        objConnection = Nothing  
    End Try  
End Function  
```  
  
```csharp  
static string CreateSession(string connectionString)  
{  
    string strSessionID = "";  
    AdomdConnection objConnection = new AdomdConnection();  
    try  
    {  
        /*First, try to connect to the specified data source.  
          If the connection string is not valid, or if the specified  
          provider does not support sessions, an exception is thrown. */  
        objConnection.ConnectionString = connectionString;  
        objConnection.Open();  
  
        // Now that the connection is open, retrieve the new  
        // active session ID.  
        strSessionID = objConnection.SessionID;  
        // Close the connection, but leave the session open.  
        objConnection.Close(false);  
        return strSessionID;  
    }  
    finally  
    {  
        objConnection = null;  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET で接続を確立します。](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)  
  
  
