---
title: "ReportViewer 2016 コントロールの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a6a0bbee9141df565966df3e90f396e33c9b96a7
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>Reporting Services の ReportViewer コントロールを使用して - 開始の統合

開発者が ASP.Net web サイト、および Reporting Services 2016 の ReportViewer コントロールでの Windows フォーム アプリで改ページ調整されたレポートを埋め込むことができる方法について説明します。 コントロールを新しいプロジェクトに追加または既存のプロジェクトを更新することができます。

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>新しい web プロジェクトへの ReportViewer コントロールの追加

1. 新しい**空の ASP.NET Web サイト**か、既存の ASP.NET プロジェクトを開きます。

    ![ssRS---ASPNET-プロジェクトの新規作成](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. 使用して、ReportViewer 2016 コントロールの nuget パッケージのインストール、 **Nuget パッケージ マネージャー コンソール**です。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. プロジェクトに新しい .aspx ページを追加し、ページ内で使用するための ReportViewer コントロール アセンブリを登録します。

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. 追加、 **ScriptManagerControl**ページにします。

5. ReportViewer コントロールをページに追加します。 次のスニペットは、リモートのレポート サーバーでホストされているレポートを参照する更新できます。

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
最後のページは、次のようになります。

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="Sample" %>

<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <meta http-equiv="X-UA-Compatible" content="IE=edge" /> 
    <title></title>
</head>
<body>
    <form id="form1" runat="server">
    <asp:ScriptManager runat="server"></asp:ScriptManager>        
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
            <ServerReport ReportServerUrl="http://AContosoDepartment/ReportServer" ReportPath="/LatestSales" />
        </rsweb:ReportViewer>
    </form>
</body>
</html>

```

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>ReportViewer コントロールを使用する既存のプロジェクトの更新

既存のプロジェクトで ReportViewer 2016 コントロールの使用、Nuget 経由でコントロールを追加、およびバージョンへのアセンブリ参照を更新する*14.0.0.0*です。 これにより、プロジェクトの web.config および ReportViewer コントロールを参照するすべての .aspx ページの更新が含まれます。

### <a name="sample-webconfig-changes"></a>サンプルの web.config の変更

```
<?xml version="1.0"?>
<!--
  For more information on how to configure your ASP.NET application, please visit
  http://go.microsoft.com/fwlink/?LinkId=169433
  -->
<configuration>
  <system.web>
    <compilation debug="true" targetFramework="4.5.2">
      <assemblies>
        <!-- All assemblies updated to version 14.0.0.0. -->
        <add assembly="Microsoft.ReportViewer.Common, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.DataVisualization, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.Design, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.ProcessingObjectModel, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebDesign, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
        <add assembly="Microsoft.ReportViewer.WinForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </assemblies>
      <buildProviders>
        <!-- Version updated to 14.0.0.0. -->
        <add extension=".rdlc"
          type="Microsoft.Reporting.RdlBuildProvider, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
      </buildProviders>
    </compilation>
    <httpRuntime targetFramework="4.5.2"/>
    <httpHandlers>
      <!-- Version updated to 14.0.0.0 -->
      <add path="Reserved.ReportViewerWebControl.axd" verb="*"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"
        validate="false"/>
    </httpHandlers>
  </system.web>
  <system.webServer>
    <validation validateIntegratedModeConfiguration="false"/>
    <modules runAllManagedModulesForAllRequests="true"/>
    <handlers>
      <!-- Version updated to 14.0.0.0 -->
      <add name="ReportViewerWebControlHandler" verb="*" path="Reserved.ReportViewerWebControl.axd" preCondition="integratedMode"
        type="Microsoft.Reporting.WebForms.HttpHandler, Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845DCD8080CC91"/>
    </handlers>
  </system.webServer>
</configuration>
```

### <a name="sample-aspx"></a>サンプルの .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>新しい Windows フォーム プロジェクトへの ReportViewer コントロールの追加

1. 新しい**Windows フォーム アプリケーション**か、既存のプロジェクトを開きます。

    ![ssRS---winforms-プロジェクトの新規作成](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. 使用して、ReportViewer 2016 コントロールの nuget パッケージのインストール、 **Nuget パッケージ マネージャー コンソール**です。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. コードから新しいコントロールを追加または[コントロールをツールボックスに追加](##adding-control-to-visual-studio-toolbar)です。

    ```
    private Microsoft.Reporting.WinForms.ReportViewer reportViewer1;
    
    private void InitializeComponent()
    {
        this.reportViewer1 = new Microsoft.Reporting.WinForms.ReportViewer();
        this.SuspendLayout();
        // 
        // reportViewer1
        // 
        this.reportViewer1.Location = new System.Drawing.Point(168, 132);
        this.reportViewer1.Name = "reportViewer1";
        this.reportViewer1.ServerReport.BearerToken = null;
        this.reportViewer1.Size = new System.Drawing.Size(396, 246);
        this.reportViewer1.TabIndex = 0;
        // 
        // Form1
        // 
        this.Controls.Add(this.reportViewer1);
    }
    ```

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>レポート ビューアー 2016 コントロールを 100% の高さを設定する方法

新しいレポート ビューアー 2016 コントロールは、HTML5 標準モードのページが最適化されていて、すべての最新ブラウザーでも動作します。 以前は、古い RVC コントロールでは、100% の height プロパティを設定するときに機能した場合でも、指定された高さ先祖のいずれも必要があります。 この動作は、HTML5 で変更されました。 新しい RVC コントロールでこのプロパティを設定すると、親要素に定義済みの高さがある場合にのみは正しく動作、つまり値ではなく auto、または RVC のすべての先祖 100% の高さすぎます。

これを行う 2 つの例を以下に示します。

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>すべての親の高さの要素を 100% に設定して

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <style>
        html,body,form,#div1 {
            height: 100%; 
        }
    </style>
   </head>
<body>
    <form id="form1" runat="server">
    <div id="div1" >
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>Reportviewer コントロールの親のスタイルの高さの属性を設定して

ビューポートの割合の長さの詳細については、次を参照してください。[ビューポート割合長さ](https://www.w3.org/TR/css3-values/#viewport-relative-lengths)です。

```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
</head>
<body>
    <form id="form1" runat="server">
    <div style="height:100vh;">
            <asp:ScriptManager runat="server"></asp:ScriptManager>
        <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote" Height="100%" Width="100%">
            <ServerReport ReportServerUrl="http://test/ReportServer" ReportPath="/testreport" />
        </rsweb:ReportViewer>
    </div>
    </form>
</body>
</html>

```

## <a name="adding-control-to-visual-studio-toolbar"></a>Visual Studio ツールバーにコントロールを追加します。

レポート ビューアー コントロールは、NuGet パッケージとして付属しているようになりました。 このため、既定では、Visual Studio ツールボックスに表示するレポート ビューアー コントロールは表示されません。 ツールボックスにコントロールを追加するには、次の操作します。

1. WinForms または WebForms 前述のいずれかの NuGet パッケージをインストールします。

2. ツールボックスに表示されている ReportViewer コントロールを削除します。 これは、コントロール 12.x のバージョンにします。

    ![ssRS の削除-古い-rvcontrol-ツールボックス](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. 右クリックで任意の場所、ツールボックスにし、**アイテムの選択.**.

    ![ssRS のツールボックスでのアイテムの選択](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. **の .NET Framework コンポーネント****参照**です。

    ![ssRS ツールボックス参照](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. 選択、 **Microsoft.ReportViewer.WinForms.dll**または**Microsoft.ReportViewer.WebForms.dll** NuGet パッケージをインストールするからです。

    > [!NOTE] 
    > NuGet パッケージは、プロジェクトのソリューション ディレクトリにインストールされます。 Dll へのパスは、次のようになります:`{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40`または`{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40`です。

6. 新しいコントロールは、ツールボックス内で表示する必要があります。 行うことができますし、ツールボックス内の別のタブにする場合。

    ![ssRS ツールボックス-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>注意点

- これにより、現在のプロジェクト内のインストールされている NuGet パッケージへの参照が追加されます。 ツールボックス内の項目は、他のプロジェクトに保持されます。 新しいソリューション/プロジェクトの NuGet パッケージをインストールするときに、ツールボックス項目が、以前のバージョンを参照する可能性があります。 

- アセンブリが使用できないなった場合でも、コントロールはツールボックスに残ります。 そのプロジェクトが削除された Visual Studio は、ツールボックスからコントロールを追加する場合に、エラーをスローします。 このエラーを修正、ツールボックスからコントロールを削除し、上記の手順を使用して再度追加します。


## <a name="common-issues"></a>一般的な問題
    
- 最新のブラウザーで使用するのには、2016 の ReportViewer コントロールは設計されています。 ブラウザー IE 互換モードで web ページを表示する場合、コントロールが機能しない可能性があります。 イントラネットのサイトは、互換性モードのイントラネットのページを表示するように促す設定を上書きするメタ タグを必要があります。

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>フィードバックを提供します。

チームが上のコントロールで発生する問題について通知、 [Reporting Services MSDN フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices)時に電子メールまたは[ RVCFeedback@microsoft.com](mailto:RVCFeedback@microsoft.com)です。

## <a name="see-also"></a>参照

[2016 ReportingViewer コントロール内のデータ コレクション](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
他に質問しますか。 [Reporting Services のフォーラムを再試行してください。](http://go.microsoft.com/fwlink/?LinkId=620231)


