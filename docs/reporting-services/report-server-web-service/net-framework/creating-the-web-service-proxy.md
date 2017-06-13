---
title: "Web サービス プロキシの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, proxies
- proxies [Reporting Services]
- XML Web service [Reporting Services], proxies
- Web service [Reporting Services], proxies
- Web references [Reporting Services]
ms.assetid: b1217843-8d3d-49f3-a0d2-d35b0db5b2df
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 067a0d370f8c857423af24b1cd52e6bc93d50a40
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="creating-the-web-service-proxy"></a>Web サービス プロキシの作成
  クライアントと Web サービスは、SOAP メッセージを使用して通信できます。SOAP メッセージは、入力パラメーターと出力パラメーターを XML としてカプセル化します。 プロキシ クラスは、パラメーターを XML 要素にマップした後、ネットワークを介して SOAP メッセージを送信します。 この方法では、プロキシ クラスによって、SOAP レベルで Web サービスと通信する必要がなくなり、SOAP および Web サービスのプロキシをサポートするあらゆる開発環境で Web サービスを呼び出すことができます。  
  
 プロキシ クラスを使用して開発プロジェクトに追加する方法を次の 2 つが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: WSDL ツールで、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]、および Web 参照を追加して[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]です。 ここでは、これらの方法について詳しく説明します。  
  
## <a name="adding-the-proxy-using-the-wsdl-tool"></a>WSDL ツールを使用したプロキシの追加  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK には、Web サービス記述言語ツール (Wsdl.exe) が含まれています。これにより、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 開発環境で使用する Web サービス プロキシを生成できます。 Web サービスをサポートする言語でクライアント プロキシを作成する最も一般的な方法 (現在は c# と[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) は WSDL ツールを使用します。  
  
 **Wsdl.exe を使用して、プロジェクトにプロキシ クラスを追加するには**  
  
1.  コマンド プロンプトから、Wsdl.exe を使用してプロキシ クラスを作成します。最低限レポート サーバー Web サービスへの URL を指定します。  
  
     たとえば、次のコマンド プロンプト ステートメントは、レポート サーバー Web サービスの管理用エンドポイントの URL を指定します。  
  
    ```  
    wsdl /language:CS /n:"Microsoft.SqlServer.ReportingServices2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     WSDL ツールは、プロキシ生成用のコマンド プロンプト引数の数値を受け付けます。 前の例は C# 言語、プロキシに使用する推奨名前空間 (Web サービス エンドポイントを複数使用する場合に名前の衝突を避けるため) を指定し、ReportingService2010.cs という名前の C# ファイルを生成します。 この例で [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] を指定した場合は、ReportingService2010.vb という名前のプロキシ ファイルが生成されます。 このファイルは、コマンド実行元のディレクトリに作成されます。  
  
2.  プロキシ クラスをアセンブリ ファイル (拡張子 .dll) にコンパイルし、それをプロジェクトで参照するか、またはプロキシ クラスをプロジェクト アイテムとして追加します。  
  
    > [!NOTE]  
    >  プロキシ クラスをプロジェクトに手動で追加する場合は、System.Web.Services.dll への参照を追加する必要があります。 Visual Studio .NET で Web 参照を使用してプロキシを追加する場合は、参照が自動的に作成されます。 詳細については、この後の「Visual Studio で Web 参照を使用するプロキシの追加」を参照してください。  
  
     プロキシ クラスをアイテムとしてプロジェクトに追加した後、関連付けられたファイルがソリューション エクスプローラーに表示されます。  
  
3.  プログラムによってサービスを呼び出すには、プロキシ クラスのインスタンスを作成します。  
  
     次のコード例は、プロジェクトに <xref:ReportService2010.ReportingService2010> プロキシ クラスのインスタンスを作成する場合の構文を示しています。  
  
```vb  
Dim service As New ReportingService2010()  
```  
  
```csharp  
ReportingService2010 service = new ReportingService2010();  
  
```  
  
 完全な構文を含む Wsdl.exe ツールの詳細については、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントの「Web サービス記述言語ツール」を参照してください。 Web サービス プロキシの詳しい説明は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK ドキュメントの「XML Web サービス プロキシの作成」を参照してください。  
  
## <a name="adding-the-proxy-using-a-web-reference-in-visual-studio"></a>Visual Studio で Web 参照を使用するプロキシの追加  
 Web 参照によって、プロジェクトで 1 つ以上の Web サービスを使用できます。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] では、ユーザーが次の簡単な手順に従うことによって、Web サービスの参照をプロジェクトに追加できます。  
  
 **プロジェクトに Web 参照を追加するには**  
  
1.  **ソリューション エクスプ ローラー**、Web サービスを使用するプロジェクトを選択します。  
  
2.  **プロジェクト** メニューのをクリックして**Web 参照の追加**です。  
  
     **Web 参照の追加** ダイアログ ボックスが表示されます。  
  
3.  **URL**フィールドに、レポート サーバー Web サービスへの完全なパスを入力します。  
  
     レポート サーバー Web サービスのレポート実行エンドポイントの単純な URL は、次のようになります。  
  
    ```  
    http://<Server Name>/reportserver/reportexecution2005.asmx  
    ```  
  
     URL には、レポート サーバー Web サービスを配置するドメイン、Web サービスを格納するフォルダー名、および Web サービスの検出ファイル名が含まれます。 各種 URL 要素の詳細については、次を参照してください。 [SOAP API にアクセスする](../../../reporting-services/report-server-web-service/accessing-the-soap-api.md)です。  
  
     Web サービスによって提供されるメソッドとプロパティの説明が、左側のブラウザー ペインに表示されます。  
  
    > [!NOTE]  
    >  レポート サーバー Web サービスに関連付けられているアイテムに関する詳細については、次を参照してください。[レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)です。  
  
4.  プロジェクトでレポート サーバー Web サービスを使用できること、およびレポート サーバーにアクセスするための適切な権限を持っていることを確認します。  
  
5.  **Web 参照名**フィールドに、使用する名前を入力して、レポート サーバー Web サービスをプログラムでアクセスするコードでします。  
  
6.  選択、**参照の追加**クリックすると、アプリケーション、Web サービスに参照を作成します。  
  
     新しい参照は、**ソリューション エクスプ ローラー**アクティブ プロジェクトの [Web 参照] ノードの下に指定した名前、 **Web 参照名**フィールドです。  
  
7.  **ソリューション エクスプ ローラー**プロジェクト内のアイテムに使用できる Web 参照クラスの名前空間をメモに Web 参照フォルダーを展開します。  
  
     プロジェクトに Web 参照を追加すると、関連付けられたファイルがの Web 参照フォルダー内のフォルダーに表示されます。**ソリューション エクスプ ローラー**です。  
  
 Web 参照を追加した後に、次の構文を使用してプロキシ クラスのインスタンスを作成します。  
  
```vb  
Dim rs As New myNamespace.myReferenceName.ReportExecutionService()  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
```  
  
```csharp  
myNamespace.myReferenceName.ReportExecutionService rs = new myNamespace.myReferenceName.ReportExecutionService();  
rs.Url = "http://<Server Name>/reportserver/reportexecution2005.asmx?wsdl"  
rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
  
```  
  
 追加することも、**を使用して**(**インポート**で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ディレクティブをレポート サーバー Web サービス参照にします。 このディレクティブを使用すると、型を名前空間で完全修飾する必要がありません。 このためには、次のコードをファイルに追加します。  
  
```vb  
Import myNamespace.myReferenceName  
```  
  
```csharp  
using myNamespace.myReferenceName;  
```  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
