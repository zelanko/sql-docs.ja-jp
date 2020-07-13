---
title: 'レッスン 3: Web サービスへのアクセス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 09671f8880f9f7745359961d9c6c126a893d26a7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62653785"
---
# <a name="lesson-3-accessing-the-web-service"></a>レッスン 3 : Web サービスへのアクセス
  レポート サーバー Web サービスへの参照をプロジェクトに追加したら、次は、Web サービスのプロキシ クラスのインスタンスを作成します。 その後、このプロキシ クラスのメソッドを呼び出すことによって、Web サービスのメソッドにアクセスできます。 アプリケーションから Web サービスのメソッドが呼び出されると、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって生成されたプロキシ クラスのコードにより、アプリケーションと Web サービス間の通信が処理されます。  
  
 まず、Web サービスのプロキシ クラス <xref:ReportService2010.ReportingService2010> のインスタンスを作成します。 次に、このプロキシ クラスを使用して Web サービスの <xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドを呼び出します。 この呼び出しを使用して、サンプル レポート Company Sales の名前と記述を取得します。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 上で実行されている Web サービスにアクセスする場合は、"ReportServer" パスに "$SQLExpress" を追加する必要があります。 次に例を示します。  
>   
>  `http://<Server Name>/reportserver$sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-access-the-web-service"></a>Web サービスにアクセスするには  
  
1.  まず、コード ファイルに `using` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は `Imports`) ディレクティブを追加することで、Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) ファイルに名前空間を追加する必要があります。 このディレクティブを使用すると、型を名前空間で完全修飾する必要がありません。  
  
2.  この操作を行うには、次のコードをコード ファイルの先頭に追加します。  
  
    ```vb  
    Imports System  
    Imports GetPropertiesSample.ReportService2010  
    ```  
  
    ```csharp  
    using System;  
    using GetPropertiesSample.ReportService2010;  
    ```  
  
3.  コード ファイルに名前空間ディレクティブを入力したら、コンソール アプリケーションの Main メソッドに次のコードを入力します。 Web サービス インスタンスの **Url** プロパティを設定するときには、必ずサーバーの名前を変更してください。  
  
    ```vb  
    Sub Main()  
       Dim rs As New ReportingService2010  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx"  
  
       Dim name As New [Property]  
       name.Name = "Name"  
  
       Dim description As New [Property]  
       description.Name = "Description"  
  
       Dim properties(1) As [Property]  
       properties(0) = name  
       properties(1) = description  
  
       Try  
          Dim returnProperties As [Property]() = rs.GetProperties( _  
             "/AdventureWorks 2012 Sample Reports/Company Sales 2012", properties)  
  
          Dim p As [Property]  
          For Each p In returnProperties  
              Console.WriteLine((p.Name + ": " + p.Value))  
          Next p  
  
       Catch e As Exception  
          Console.WriteLine(e.Message)  
       End Try  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
       ReportingService2010 rs = new ReportingService2010();  
       rs.Credentials = System.Net.CredentialCache.DefaultCredentials;  
       rs.Url = "http://<Server Name>/reportserver/reportservice2010.asmx";  
  
       Property name = new Property();  
       name.Name = "Name";  
  
       Property description = new Property();  
       description.Name = "Description";  
  
       Property[] properties = new Property[2];  
       properties[0] = name;  
       properties[1] = description;  
  
       try  
       {  
          Property[] returnProperties = rs.GetProperties(  
          "/AdventureWorks 2012 Sample Reports/Company Sales 2012",properties);  
  
          foreach (Property p in returnProperties)  
          {  
             Console.WriteLine(p.Name + ": " + p.Value);  
          }  
       }  
  
       catch (Exception e)  
       {  
          Console.WriteLine(e.Message);  
       }  
    }  
    ```  
  
4.  ソリューションを保存します。  
  
 このチュートリアルのサンプル コードでは、Web サービスの <xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドを使用して、サンプル レポート Company Sales 2012 のプロパティを取得しています。 メソッド<xref:ReportService2010.ReportingService2010.GetProperties%2A>は、プロパティ情報を取得するレポートの名前と、値を取得するプロパティの名前を格納する**property []** オブジェクトの配列の2つの引数を受け取ります。 メソッドは、properties 引数で指定されたプロパティの名前と値を含む**Property []** オブジェクトの配列も返します。  
  
> [!NOTE]  
>  Properties 引数に空の**Property []** 配列を指定すると、使用可能なすべてのプロパティが返されます。  
  
 上記のサンプル コードでは、<xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドを使用して、サンプル レポート Company Sales 2012 の名前と記述が返されています。 次に、`foreach` ループを使用して、プロパティと値をコンソールに書き込んでいます。  
  
 レポート サーバー Web サービスのプロキシ クラスの作成と使用の詳細については、「 [Creating the Web Service Proxy](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レッスン 4: アプリケーションの実行 &#40;VB-VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Visual Basic または Visual C&#35; &#40;SSRS チュートリアルを使用したレポートサーバー Web サービスへのアクセス&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
