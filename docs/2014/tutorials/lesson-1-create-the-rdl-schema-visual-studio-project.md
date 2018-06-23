---
title: 'レッスン 1: RDL スキーマ Visual Studio プロジェクトの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f420509c-51aa-4170-8c25-64c2954f4bb9
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b6c502205f669c48efe1f939ba88e5352205f4de
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176083"
---
# <a name="lesson-1-create-the-rdl-schema-visual-studio-project"></a>レッスン 1 : RDL スキーマ Visual Studio プロジェクトの作成
  このチュートリアルでは、簡単なコンソール アプリケーションを作成します。 このチュートリアルで開発している前提としています[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]です。  
  
> [!NOTE]  
>  [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services で実行されているレポート サーバー Web サービスにアクセスする場合は、"_SQLExpress" を "ReportServer" パスに追加する必要があります。 以下に例を示します。  
>   
>  `http://myserver/reportserver_sqlexpress/reportservice2010.asmx"`  
  
### <a name="to-create-the-web-service-proxy"></a>Web サービス プロキシを作成するには  
  
1.  **開始**メニューの [**すべてのプログラム**、し、Microsoft Visual Studio]、 **Visual Studio Tools**、し**Visual Studio 2010 コマンド プロンプト**.  
  
2.  C#: を使用している場合は、コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    wsdl /language:CS /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     Visual Basic を使用している場合は、次のコマンドを実行します。  
  
    ```  
    wsdl /language:VB /n:"ReportService2010" http://<Server Name>/reportserver/reportservice2010.asmx?wsdl  
    ```  
  
     このコマンドは .cs ファイルまたは .vb ファイルを生成します。 このファイルをアプリケーションに追加します。  
  
### <a name="to-create-a-console-application"></a>コンソール アプリケーションを作成するには  
  
1.  **ファイル** メニューのをポイント**新規**、クリックして**プロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  左側のウィンドウで **インストールされたテンプレート**、いずれかをクリックして**Visual Basic**または**Visual c#** ノードを展開し、展開された一覧からプロジェクトのカテゴリの種類を選択します。  
  
3.  選択、**コンソール アプリケーション**プロジェクトの種類。  
  
4.  **名前**ボックスで、プロジェクトの名前を入力します。 名前を入力します`SampleRDLSchema`です。  
  
5.  **場所**ボックスで、プロジェクトを保存またはをクリックする場所のパスを入力**参照**フォルダーに移動します。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] ソリューション エクスプ ローラーでプロジェクトの折りたたまれたビューが表示されます。  
  
7.  **[プロジェクト]** メニューの **[既存項目の追加]** をクリックします。  
  
8.  .Cs または .vb ファイルを生成するための場所に移動し、ファイルを選択し、をクリックして**追加**です。  
  
     また、Web 参照が動作するように、<xref:System.Web.Services> 名前空間への参照を追加する必要があります。  
  
9. [プロジェクト] メニューをクリックして**参照の追加**です。  
  
     **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、 **System.Web.Services**をクリックし、 **ok**です。  
  
     レポート サーバー Web サービスに接続する方法の詳細については、次を参照してください。 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)です。  
  
10. ソリューション エクスプ ローラーでプロジェクト ノードを展開します。 プロジェクトには、Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) という既定の名前のコード ファイルが追加されていることがわかります。  
  
11. Program.cs ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] の場合は Module1.vb) ファイルを開き、次のコードに置き換えます。  
  
     次のコードは、読み込み、変更、保存の機能を実装するときに使用するメソッドの一部です。  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using ReportService2010;  
  
    namespace SampleRDLSchema  
    {  
        class ReportUpdater  
        {  
            ReportingService2010 _reportService;  
  
            static void Main(string[] args)  
            {  
                ReportUpdater reportUpdater = new ReportUpdater();  
                reportUpdater.UpdateReport();  
            }  
  
            private void UpdateReport()  
            {  
                try  
                {  
                    // Set up the Report Service connection  
                    _reportService = new ReportingService2010();  
                    _reportService.Credentials =  
                        System.Net.CredentialCache.DefaultCredentials;  
                    _reportService.Url =  
                       "http://<Server Name>/reportserver/" +  
                                       "reportservice2010.asmx";  
  
                    // Call the methods to update a report definition  
                    LoadReportDefinition();  
                    UpdateReportDefinition();  
                    PublishReportDefinition();  
                }  
                catch (Exception ex)  
                {  
                    System.Console.WriteLine(ex.Message);  
                }  
            }  
  
            private void LoadReportDefinition()  
            {  
                //Lesson 3: Load a report definition from the report   
                //          catalog  
            }  
  
            private void UpdateReportDefinition()  
            {  
                //Lesson 4: Update the report definition using the    
                //          classes generated from the RDL Schema  
            }  
  
            private void PublishReportDefinition()  
            {  
                //Lesson 5: Publish the updated report definition back   
                //          to the report catalog  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports ReportService2010  
  
    Namespace SampleRDLSchema  
  
        Module ReportUpdater  
  
            Private m_reportService As ReportingService2010  
  
            Public Sub Main(ByVal args As String())  
  
                Try  
                    'Set up the Report Service connection  
                    m_reportService = New ReportingService2010  
                    m_reportService.Credentials = _  
                        System.Net.CredentialCache.DefaultCredentials  
                    m_reportService.Url = _  
                        "http:// <Server Name>/reportserver/" & _  
                               "reportservice2010.asmx"  
  
                    'Call the methods to update a report definition  
                    LoadReportDefinition()  
                    UpdateReportDefinition()  
                    PublishReportDefinition()  
                Catch ex As Exception  
                    System.Console.WriteLine(ex.Message)  
                End Try  
  
            End Sub  
  
            Private Sub LoadReportDefinition()  
                'Lesson 3: Load a report definition from the report   
                '          catalog  
            End Sub  
  
            Private Sub UpdateReportDefinition()  
                'Lesson 4: Update the report definition using the   
                '          classes generated from the RDL Schema  
            End Sub  
  
            Private Sub PublishReportDefinition()  
                'Lesson 5: Publish the updated report definition back   
                '          to the report catalog  
            End Sub  
  
        End Module  
  
    End Namespace   
    ```  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、XML スキーマ定義ツール (Xsd.exe) を使用して RDL スキーマからクラスを生成し、プロジェクトに組み込みます。 参照してください[レッスン 2: xsd ツールを使用して、RDL スキーマからクラスを生成する](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)です。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用してレポートの更新&#40;SSRS チュートリアル&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  