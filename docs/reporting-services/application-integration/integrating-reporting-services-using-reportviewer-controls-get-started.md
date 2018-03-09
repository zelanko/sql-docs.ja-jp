---
title: "ReportViewer 2016 Cortana の概要 | Microsoft Docs"
ms.custom: 
ms.date: 06/12/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: application-integration
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a821c4-2920-400c-be03-93d26c749bb1
caps.latest.revision: "12"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Active
ms.openlocfilehash: 9b177bb647fd1c9daf5fb330f3bff15cf3e73ab3
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="integrating-reporting-services-using-reportviewer-controls---get-started"></a>ReportViewer コントロールを使用した Reporting Services の統合 - 概要

開発者が Reporting Services 2016 ReportViewer コントロールを使用して ASP.NET Web サイトと Windows フォーム アプリにページ分割されたレポートを埋め込む方法について説明します。 このコントロールは、新しいプロジェクトに追加するか、既存のプロジェクトを更新して追加することができます。

## <a name="adding-the-reportviewer-control-to-a-new-web-project"></a>新しい Web プロジェクトに ReportViewer コントロールを追加する

1. 新しい **[ASP.NET 空の Web サイト]** を作成するか、既存の ASP.NET プロジェクトを開きます。

    ![ssRS-Create-New-ASPNET-Project](../../reporting-services/application-integration/media/ssrs-create-new-aspnet-project.png)

2. **NuGet パッケージ マネージャー コンソール**から ReportViewer 2016 コントロール NuGet パッケージをインストールします。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WebForms
    ```
3. 新しい .aspx パッケージをプロジェクトに追加し、ページ内で使用できるように ReportViewer コントロール アセンブリを登録します。

    ```
    <%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>
    ```
    
4. ページに **ScriptManagerControl** を追加します。

5. ページに ReportViewer コントロールを追加します。 リモート レポート サーバーでホストされているレポートを参照するように次のスニペットを更新することができます。

    ```
    <rsweb:ReportViewer ID="ReportViewer1" runat="server" ProcessingMode="Remote">
      <ServerReport ReportPath="" ReportServerUrl="" />
    </rsweb:ReportViewer>
    ```
    
最終的なページは次のようになります。

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

## <a name="updating-an-existing-project-to-use-the-reportviewer-control"></a>ReportViewer コントロールを使用するように既存のプロジェクトを更新する

既存のプロジェクトで ReportViewer 2016 コントロールを利用するには、NuGet を使用してコントロールを追加し、アセンブリの参照をバージョン *14.0.0.0* に更新します。 これで、プロジェクトの web.config と、ReportViewer コントロールを参照するすべての .aspx ページの更新が含まれるようになります。

### <a name="sample-webconfig-changes"></a>サンプル web.config の変更

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

### <a name="sample-aspx"></a>サンプル .aspx

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SampleAspx" %>

<!-- Update version to 14.0.0.0 -->
<%@ Register assembly="Microsoft.ReportViewer.WebForms, Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91" namespace="Microsoft.Reporting.WebForms" tagprefix="rsweb" %>

<!DOCTYPE html>
```

## <a name="adding-the-reportviewer-control-to-a-new-windows-forms-project"></a>新しい Windows フォーム プロジェクトに ReportViewer コントロールを追加する

1. 新しい **Windows フォーム アプリケーション**を作成するか、既存のプロジェクトを開きます。

    ![ssRS-Create-New-winforms-Project](../../reporting-services/application-integration/media/ssrs-create-new-winforms-project.png)

2. **NuGet パッケージ マネージャー コンソール**から ReportViewer 2016 コントロール NuGet パッケージをインストールします。

    ```
    Install-Package Microsoft.ReportingServices.ReportViewerControl.WinForms
    ```
3. コードから新しいコントロールを追加するか、[コントロールをツールボックスに追加](##adding-control-to-visual-studio-toolbar)します。

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

## <a name="how-to-set-100-height-on-the-report-viewer-2016-control"></a>ReportViewer 2016 コントロールで 100% の高さを設定する方法

新しい ReportViewer 2016 コントロールは、HTML5 標準モードのページに合わせて最適化されており、すべての最新ブラウザー上で動作します。 これまで、以前のバージョンの RVC コントロールでは、高さのプロパティを 100% に設定すると、親要素に高さが指定されていない場合でも機能していました。 この動作は HTML5 で変更されました。 新しい RVC コントロールでこのプロパティを設定すると、親要素に定義済みの高さがある場合 (つまり、自動の値ではない場合)、または RVC のすべての親要素も 100% の高さの場合にのみ、正しく機能するようになります。

この処理を実行する 2 つの例を紹介します。

### <a name="by-setting-the-height-of-all-the-parent-elements-to-100"></a>すべての親要素の高さを 100% に設定する

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

### <a name="by-setting-the-style-height-attribute-on-the-parent-of-the-reportviewer-control"></a>ReportViewer コントロールの親要素に style の height 属性を設定する

ビューポートの割合の長さについては、「[Viewport-percentage lengths](https://www.w3.org/TR/css3-values/#viewport-relative-lengths)」(ビューポートの割合の長さ) を参照してください。

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

## <a name="adding-control-to-visual-studio-toolbar"></a>Visual Studio ツール バーにコントロールを追加する

ReportViewer コントロールは NuGet パッケージに含まれるようになりました。 そのため、既定の Visual Studio ツールボックスに ReportViewer コントロールは表示されません。 コントロールをツールボックスに追加するには、次の手順を実行します。

1. 前述のように、WinForms または WebForms 用の NuGet パッケージをインストールします。

2. ツールボックスに表示されている ReportViewer コントロールを削除します。 これはバージョン 12.x のコントロールです。

    ![ssRS-remove-old-rvcontrol-toolbox](../../reporting-services/application-integration/media/ssrs-remove-old-rvcontrol-toolbox.png)

3. ツールボックス内のいずれかの場所を右クリックし、**[アイテムの追加]** を選択します。

    ![ssRS-toolbox-choose-item](../../reporting-services/application-integration/media/ssrs-toolbox-choose-item.png)
    
4. **[.NET Framework コンポーネント]** の **[参照]** を選択します。

    ![ssRS-toolbox-browse](../../reporting-services/application-integration/media/ssrs-toolbox-browse.png)

5. インストールされた NuGet パッケージから **Microsoft.ReportViewer.WinForms.dll** または **Microsoft.ReportViewer.WebForms.dll** を選択します。

    > [!NOTE] 
    > NuGet パッケージは、プロジェクトのソリューション ディレクトリにインストールされます。 dll のパスは、`{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.Winforms.{version}\lib\net40` または `{Solution Directory}\packages\Microsoft.ReportingServices.ReportViewerControl.WebForms.{version}\lib\net40` のようになります。

6. ツールボックス内に新しいコントロールが表示されます。 必要に応じて、ツールボックス内の別のタブに移動することができます。

    ![ssRS-toolbox-rvcontrol](../../reporting-services/application-integration/media/ssrs-toolbox-rvcontrol.png)

### <a name="things-to-be-aware-of"></a>注意事項

- この手順で、インストールされている NuGet パッケージへの参照が現在のプロジェクトに追加されます。 このツールボックスの項目は、他のプロジェクトにも表示されます。 新しいソリューション/プロジェクトに NuGet パッケージをインストールすると、ツールボックスの項目は以前のバージョンを参照する可能性があります。 

- そのアセンブリを使用できなくなっても、コントロールはツールボックスに残ります。 プロジェクトを削除した場合、ツールボックスからこのコントロールを追加しようとすると、Visual Studio からエラーがスローされます。 このエラーを修正するには、ツールボックスからコントロールを削除し、前述の手順を使用して追加し直してください。


## <a name="common-issues"></a>一般的な問題
    
- ReportViewer 2016 コントロールは、最新のブラウザーで使用するように設計されています。 IE 互換モードで Web ページを表示するブラウザーの場合、コントロールが機能しない可能性があります。 イントラネット サイトの場合、状況によっては、互換モードでイントラネット ページを表示するように促す設定をメタ タグで上書きする必要があります。

    ```
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    ```
      
## <a name="providing-feedback"></a>フィードバックの送信

このコントロールで問題が発生した場合は、[Reporting Services MSDN フォーラム](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=sqlreportingservices)か、電子メール ([RVCFeedback@microsoft.com](mailto:RVCFeedback@microsoft.com)) でチームにお知らせください。

## <a name="see-also"></a>参照

[2016 ReportViewer コントロールのデータ コレクション](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-data-collection.md)  
その他の質問 [Reporting Services のフォーラムにアクセスします](http://go.microsoft.com/fwlink/?LinkId=620231)

