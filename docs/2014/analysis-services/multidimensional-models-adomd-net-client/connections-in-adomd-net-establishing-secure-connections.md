---
title: ADOMD.NET でのセキュリティで保護された接続を確立する |Microsoft ドキュメント
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
- connections [ADOMD.NET]
- security [ADOMD.NET]
ms.assetid: b084d447-1456-45a4-8e0e-746c07d7d6fd
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dd860308d9e4e7f7ed17072572594d6b8aaeeb70
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074966"
---
# <a name="establishing-secure-connections-in-adomdnet"></a>ADOMD.NET でのセキュリティ保護された接続の確立
  ADOMD.NET で接続を使用する場合、その接続に適用されるセキュリティ手段は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Open%2A> の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> メソッドを呼び出すときに使用する接続文字列の `ProtectionLevel` プロパティの値によって異なります。  
  
 `ProtectionLevel` プロパティには、"認証なし"、"認証済み"、"署名済み"、"暗号化" の 4 つのセキュリティ レベルがあります。 これらの各セキュリティ レベルについて、次の表で説明します。  
  
> [!NOTE]  
>  データベース接続のプール機能を使用する場合、データベースでセキュリティを管理することはできません。 これは、データベース接続のプールでは、接続文字列をプール接続と同じにする必要があるからです。 したがって、どこか他の場所でセキュリティを管理する必要があります。  
  
|セキュリティ レベル|ProtectionLevel の値|  
|--------------------|---------------------------|  
|*未認証の接続*<br /> 未認証の接続では一切の認証が行われません。 この種の接続は広く利用されていますが、安全性が最も低い接続形態です。|`None`|  
|*認証された接続*<br /> 認証された接続では、接続を要求しているユーザーの本人性を確認します。ただし、その後の通信はセキュリティで保護されません。 この種の接続は、分析データ ソースに接続しようとしているユーザーまたはアプリケーションの身元を検証できるという点で便利です。|`Connect`|  
|*署名された接続*<br /> 署名された接続は、接続を要求しているユーザーを認証し、転送データが変更されていないことを確認します。 この種の接続は、転送されたデータの信頼性を検証する必要がある場合に役立ちます。 ただし、署名された接続で防止できるのは、データ パケットの内容の不正な変更です。 転送中、データ パケットの内容が傍受される危険性は残っています。 **注:** 署名された接続は、XML for Analysis プロバイダーによって提供されるでのみサポートされて[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。|`Pkt Integrity` または `PktIntegrity`|  
|*暗号化された接続*<br /> 暗号化された接続は、ADOMD.NET によって使用される既定の接続の種類です。 この種の接続は、接続を要求しているユーザーを認証したうえで、転送データの暗号化も行います。 暗号化された接続は、ADOMD.NET で作成できる接続形式の中でセキュリティ保護のレベルが最も高い形式です。 データ パケットの内容は表示または変更できず、転送中のデータが保護されます。 **注:** 、暗号化された接続は、XML for Analysis プロバイダーによって提供されるでのみサポートされて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。|`Pkt Privacy` または `PktPrivacy`|  
  
 ただし、接続の種類によっては、使用できないセキュリティ レベルもあります。  
  
-   TCP 接続では、これら 4 つのうち、どのセキュリティ レベルでも使用できます。 実際、TCP 接続を Windows 統合セキュリティと共に使用すると、最も安全な方法で分析データ ソースに接続できます。  
  
-   HTTP 接続で、認証された接続のみ使用できます。 したがって、`ProtectionLevel` プロパティは `Connect` に設定する必要があります。  
  
-   HTTPS 接続では、暗号化された接続のみ使用できます。 したがって、`ProtectionLevel` プロパティは `Pkt Privacy` または `PktPrivacy` に設定する必要があります。  
  
## <a name="securing-tcp-connections"></a>TCP 接続のセキュリティ保護  
 TCP 接続の場合、`ProtectionLevel` プロパティは、次の表に示すように、4 つのすべてのセキュリティ レベルをサポートします。  
  
|ProtectionLevel の値|TCP 接続で使用するか|[結果]|  
|---------------------------|------------------------------|-------------|  
|`None`|はい|未認証の接続が適用されます。<br /><br /> プロバイダーに対して TCP ストリームが要求されます。ただし、ストリームを要求しているユーザーに対しては、どのような形態の認証も実行されません。|  
|`Connect`|はい|認証された接続が適用されます。<br /><br /> TCP ストリームが、プロバイダーから要求され、ストリームを要求しているユーザーのセキュリティ コンテキストがサーバーに対して認証。<br /><br /> -認証が成功した場合、その他の処理は行われません。<br />-認証に失敗した場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトが、多次元データ ソースから切断され、例外がスローされます。<br /><br /> 認証が成功または失敗した後に、接続の認証に使用されたセキュリティ コンテキストは破棄されます。|  
|`Pkt Integrity` または `PktIntegrity`|はい|署名された接続が適用されます。<br /><br /> TCP ストリームが、プロバイダーから要求され、ストリームを要求しているユーザーのセキュリティ コンテキストがサーバーに対して認証。<br /><br /> -認証が成功した場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト既存の TCP ストリームを閉じ、すべての要求を処理する署名された TCP ストリームを開きます。 データまたはメタデータに対する各要求は、接続を開くために使用されたセキュリティ コンテキストを使用して認証されます。 また、各パケットは、TCP パケットのペイロードが変更されていないことを確認するためにデジタル署名されています。<br />-認証に失敗した場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトが、多次元データ ソースから切断され、例外がスローされます。|  
|`Pkt Privacy` または `PktPrivacy`|はい|暗号化された接続が適用されます。 **注:** 設定しない、暗号化された接続を指定することも、`ProtectionLevel`接続文字列プロパティです。 <br /><br /> プロバイダーに対して TCP ストリームが要求されます。さらに、ストリームを要求しているユーザーのセキュリティ コンテキストがサーバーに対して認証されます。<br /><br /> -認証が成功した場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクト既存の TCP ストリームを閉じ、すべての要求を処理する、暗号化された TCP ストリームを開きます。 データまたはメタデータに対する各要求は、接続を開くために使用されたセキュリティ コンテキストを使用して認証されます。 また、各 TCP パケットのペイロードは、プロバイダーおよび多次元データ ソースの両方でサポートされている最も高度な暗号化方法を使用して暗号化されます。<br />-認証に失敗した場合、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>オブジェクトが、多次元データ ソースから切断され、例外がスローされます。|  
  
### <a name="using-windows-integrated-security-for-the-connection"></a>接続での Windows 統合セキュリティの使用  
 Windows 統合セキュリティは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスへの接続の確立およびセキュリティ保護を行うための最も安全な方法です。 Windows 統合セキュリティでは、認証プロセス中にユーザー名やパスワードなどのセキュリティ資格情報が公開されません。代わりに、現在実行しているプロセスのセキュリティ ID を使用して本人性を検証します。 多くのクライアント アプリケーションの場合、このセキュリティ ID は現在ログオンしているユーザーの ID を表します。  
  
 Windows 統合セキュリティを使用するには、接続文字列を次のように設定する必要があります。  
  
-   `Integrated Security` プロパティの場合、このプロパティを設定しないか、あるいは `SSPI` に設定します。  
  
    > [!NOTE]  
    >  Windows 統合セキュリティは TCP 接続でのみ使用できます。HTTP 接続は、`Basic` プロパティの `Integrated Security` 設定を使用する必要があります。  
  
-   `ProtectionLevel` プロパティの場合、このプロパティを、`Connect`、`Pkt Integrity` または `Pkt Privacy` に設定します。  
  
## <a name="securing-http-connections"></a>HTTP 接続のセキュリティ保護  
 HTTPS および SSL (Secure Sockets Layer) を使用して、分析データ ソースで HTTP 通信の外部的なセキュリティ保護を行うことができます。  
  
 XMLA プロバイダーはセキュリティ保護された HTTP のみ使用するため、ADOMD.NET での HTTP 接続は、次の表に示すように署名された接続にする必要があります。  
  
|ProtectionLevel の値|HTTP または HTTPS で使用するか|  
|---------------------------|----------------------------|  
|`None`|いいえ|  
|`Connect`|HTTP|  
|`Pkt Integrity` または `PktIntegrity`|いいえ|  
|`Pkt Privacy` または `PktPrivacy`|HTTPS|  
  
### <a name="opening-a-secure-http-connection"></a>セキュリティ保護された HTTP 接続を開く  
 ADOMD.NET を使用して `AdventureWorksAS` のサンプル [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースへの HTTP 接続を開く例を次に示します。  
  
```vb  
Public Function GetAWEncryptedConnection( _  
    Optional ByVal serverName As String = "https:\\localhost\isapy\msmdpump.dll") _  
    As AdomdConnection  
  
    Dim strConnectionString As String = ""  
    Dim objConnection As New AdomdConnection  
  
    Try  
        ' To establish an encrypted connection, set the   
        ' ProtectionLevel setting to PktPrivacy.  
        strConnectionString = "DataSource=" & serverName & ";" & _  
            "Catalog=AdventureWorksAS;" & _  
            "ProtectionLevel=PktPrivacy;"  
  
        ' Note that username and password are not supplied here.  
        ' The current security context is used for authentication  
        ' purposes.  
  
        objConnection.ConnectionString = strConnectionString  
        objConnection.Open()  
    Catch ex As Exception  
        objConnection = Nothing  
        Throw ex  
    Finally  
        ' Return the encrypted connection.  
        GetAWEncryptedConnection = objConnection  
    End Try  
End Function  
  
```  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET での接続の確立](connections-in-adomd-net.md)  
  
  