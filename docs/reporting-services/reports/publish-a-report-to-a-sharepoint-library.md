---
title: "SharePoint ライブラリへのレポートのパブリッシュ | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "配置 [Reporting Services], SharePoint 統合モードのレポート"
  - "SharePoint 統合 [Reporting Services], ライブラリへのパブリッシュ"
  - "レポートのパブリッシュ [Reporting Services], SharePoint ライブラリへの"
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# SharePoint ライブラリへのレポートのパブリッシュ
  SharePoint 統合用に構成されている SharePoint サイトにレポートをパブリッシュするには、レポート デザイナーでレポート プロジェクトのプロパティを設定する必要があります。 プロジェクトのプロパティでは、サーバー、レポート、および共有データ ソースへの参照はすべて、完全修飾 URL で指定する必要があります。 レポート定義では、サブレポートや詳細レポートへの参照、および Web ベースの画像などのリソースへの参照はすべて完全修飾 URL で指定する必要があります。  
  
 プロジェクトにプロパティを設定するには、SharePoint サイトの**メンバー**権限または**所有者**権限が必要です。 詳細については、「[SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。  
  
### レポートを SharePoint サイトにパブリッシュするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で既存または新規のレポート サーバー プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 *[\<project>***プロパティ ページ]** ダイアログ ボックスが開きます。  
  
3.  **[構成]** ボックスで、レポートのビルドとパブリッシュに使用するソリューション ビルド構成の名前を選択します。 現在の構成は **[アクティブ]** (*\<configuration>*) として表示されます。  
  
4.  プロジェクトの共有データ ソースをパブリッシュし、以前にパブリッシュされた共有データ ソースを上書きするには、**[OverwriteDataSources]** を **[True]** に設定します。  
  
5.  (省略可) **[TargetDataSourceFolder]** には、SharePoint ライブラリまたはライブラリ フォルダーの URL (*http://TestServer/TestSite/Documents/DataSources* など) を入力します。  
  
     値を指定しない場合は、**[TargetReportFolder]** の値が使用されます。  
  
6.  **[TargetReportFolder]** にはライブラリまたはライブラリ フォルダーの URL (*http://TestServer/TestSite/Documents/Reports* など) を入力します。  
  
7.  **[TargetServerURL]** に、SharePoint トップレベル サイトまたはサブサイトの URL を入力します。 サイトを指定しなかった場合は、既定のトップレベル サイトが使用されます (たとえば、*http://servername*、*http://servername/site、http://servername/site/subsite*、*http://servername/site/subsite* など)。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. ソリューション エクスプローラーで、パブリッシュするレポートを右クリックし、**[配置]** をクリックします。 これで、**[TargetReportFolder]** で指定した場所にレポートがパブリッシュされます。 配置エラーは出力ウィンドウに表示されます。  
  
## 参照  
 [[プロパティ ページ] ダイアログ ボックス](../Topic/Project%20Property%20Pages%20Dialog%20Box.md)   
 [配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [レポート サーバーへのレポートのパブリッシュ](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [レポートで Office Data Connection (.odc) を使用する (Reporting Services の SharePoint 統合モード)](../../reporting-services/report-data/use an office data connection (.odc) with reports.md)  
  
  