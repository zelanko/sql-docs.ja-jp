---
title: "Windows アプリケーションで URL アクセスの使用 |Microsoft ドキュメント"
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
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
caps.latest.revision: 48
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 782be214cb491e1fdddf6ff7d45ac377fcfbf8a4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="integrating-reporting-services-using-url-access---windows-application"></a>URL アクセスの Windows アプリケーションを使用して Reporting Services の統合
  レポート サーバーへの URL アクセスは Web 環境用に最適化されていますが、URL アクセスを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーションに埋め込むこともできます。 ただし、Windows フォームに関連する URL アクセスでは、Web ブラウザー テクノロジを使用する必要があります。 URL アクセスと Windows フォームでは、次の統合シナリオを使用できます。  
  
-   プログラムで Web ブラウザーを起動し、Windows フォーム アプリケーションからレポートを表示します。  
  
-   Windows フォームで <xref:System.Windows.Forms.WebBrowser> コントロールを使用し、レポートを表示します。  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a>Windows フォームからの Internet Explorer の起動  
 <xref:System.Diagnostics.Process> クラスを使用して、コンピューターで実行されているプロセスにアクセスできます。 <xref:System.Diagnostics.Process>クラスは、便利な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]開始、停止、制御、およびアプリケーションの監視を構成します。 表示するには、特定のレポート、レポート サーバー データベースにすることができます、 **IExplore**プロセス、レポートに URL を渡しています。 次のコード例を使用すると、ユーザーが Windows フォームのボタンをクリックしたときに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer が起動し、特定のレポート URL を渡すことができます。  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a>Windows フォームへのブラウザー コントロールの埋め込み  
 外部 Web ブラウザーでレポートを表示したくない場合は、<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Windows フォームの一部としてシームレスに Web ブラウザーを埋め込むことができます。  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a>Windows フォームに WebBrowser コントロールを追加するには  
  
1.  いずれかで新しい Windows アプリケーションを作成[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[csprcs](../../includes/csprcs-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]です。  
  
2.  検索、<xref:System.Windows.Forms.WebBrowser>内の制御、**ツールボックス** ダイアログ ボックス。  
  
     場合、**ツールボックス**は非表示、アクセスできる をクリックして、**ビュー**メニュー項目を選択して**ツールボックス**です。  
  
3.  ドラッグ、<xref:System.Windows.Forms.WebBrowser>コントロールを Windows フォームのデザイン画面にします。  
  
     <xref:System.Windows.Forms.WebBrowser>WebBrowser1 という名前のコントロールがフォームに追加  
  
 直接、<xref:System.Windows.Forms.WebBrowser>コントロールを呼び出すことによって、URL、**移動**メソッドです。 次の例に示すように、実行時に特定の URL アクセス文字列を <xref:System.Windows.Forms.WebBrowser> コントロールに割り当てることができます。  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a>参照  
 [アプリケーションへの Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [URL アクセスを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [SOAP を使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)   
 [ReportViewer コントロールを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)   
 [URL アクセスと #40 です。SSRS &#41;](../../reporting-services/url-access-ssrs.md)  
  
  
