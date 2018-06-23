---
title: 'レッスン 3: Web サービスにアクセスする |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3e4c198-ab35-4548-9471-1b4e6b6e5dfd
caps.latest.revision: 43
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f9cff3b2bec832eec9dc6cf8462511db89454eba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179432"
---
# <a name="lesson-3-accessing-the-web-service"></a>レッスン 3 : Web サービスへのアクセス
  レポート サーバー Web サービスへの参照をプロジェクトに追加したら、次は、Web サービスのプロキシ クラスのインスタンスを作成します。 その後、このプロキシ クラスのメソッドを呼び出すことによって、Web サービスのメソッドにアクセスできます。 プロキシ クラスで生成されたコードのアプリケーションでは、これらのメソッドを呼び出す、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]アプリケーションと Web サービス間の通信を処理します。  
  
 Web サービスのプロキシ クラスのインスタンスを作成する最初に、<xref:ReportService2010.ReportingService2010>です。 次に、このプロキシ クラスを使用して Web サービスの <xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドを呼び出します。 この呼び出しを使用して、サンプル レポート Company Sales の名前と記述を取得します。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 上で実行されている Web サービスにアクセスする場合は、"ReportServer" パスに "$SQLExpress" を追加する必要があります。 以下に例を示します。  
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
  
 このチュートリアルのサンプル コードを使用して、<xref:ReportService2010.ReportingService2010.GetProperties%2A>サンプル レポート Company Sales 2012 のプロパティを取得する Web サービスのメソッドです。 <xref:ReportService2010.ReportingService2010.GetProperties%2A>メソッドが 2 つの引数を受け取る: プロパティの情報との配列を取得するレポートの名前**property[]** 値を取得するプロパティの名前を含むオブジェクト。 メソッドの配列を返しますも**property[]** 名前と、プロパティ引数に指定したプロパティの値が含まれているオブジェクト。  
  
> [!NOTE]  
>  場合は、空を指定する**property[]** 配列プロパティ引数には、すべての利用可能なプロパティが返されます。  
  
 上記のサンプル コードでは、<xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドを使用して、サンプル レポート Company Sales 2012 の名前と記述が返されています。 次に、`foreach` ループを使用して、プロパティと値をコンソールに書き込んでいます。  
  
 作成して、レポート サーバー Web サービスのプロキシ クラスの使用に関する詳細については、次を参照してください。 [Web サービス プロキシを作成する](../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)です。  
  
## <a name="see-also"></a>参照  
 [レッスン 4: アプリケーションを実行する&#40;VB VC&#35;&#41;](../../2014/tutorials/lesson-4-running-the-application-vb-vcsharp.md)   
 [Visual Basic または Visual C を使用してレポート サーバー Web サービスにアクセスする&#35; &#40;SSRS チュートリアル&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  