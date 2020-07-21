---
title: SharePoint ライブラリへのレポートのパブリッシュ | Microsoft Docs
description: レポート デザイナーでプロジェクトのプロパティを設定して、SharePoint ライブラリにレポートをパブリッシュする方法について説明します。
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 093837d7d7d2c6833b4c7dce8fabbf554d634290
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510113"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>SharePoint ライブラリへのレポートのパブリッシュ
  SharePoint 統合用に構成されている SharePoint サイトにレポートをパブリッシュするには、レポート デザイナーでレポート プロジェクトのプロパティを設定する必要があります。 プロジェクトのプロパティでは、サーバー、レポート、および共有データ ソースへの参照はすべて、完全修飾 URL で指定する必要があります。 レポート定義では、サブレポートや詳細レポートへの参照、および Web ベースの画像などのリソースへの参照はすべて完全修飾 URL で指定する必要があります。  
  
 プロジェクトにプロパティを設定するには、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。 詳細については、「 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)」を参照してください。  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>レポートを SharePoint サイトにパブリッシュするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で既存または新規のレポート サーバー プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 _[\<プロジェクト>_ **プロパティ ページ]** ダイアログ ボックスが開きます。  
  
3.  **[構成]** ボックスで、レポートのビルドとパブリッシュに使用するソリューション ビルド構成の名前を選択します。 現在の構成は **[アクティブ]** ( *\<configuration>* ) として表示されます。  
  
4.  プロジェクトの共有データ ソースをパブリッシュし、以前にパブリッシュされた共有データ ソースを上書きするには、 **[OverwriteDataSources]** を **[True]** に設定します。  
  
5.  (省略可) **[TargetDataSourceFolder]** には、SharePoint ライブラリまたはライブラリ フォルダーの URL ( `https://TestServer/TestSite/Documents/DataSources`) として表示されます。  
  
     値を指定しない場合は、 **[TargetReportFolder]** の値が使用されます。  
  
6.  **[TargetReportFolder]** に、ライブラリまたはライブラリ フォルダーの URL (`https://TestServer/TestSite/Documents/Reports` など) を入力します。  
  
7.  **[TargetServerURL]** に、SharePoint トップレベル サイトまたはサブサイトの URL を入力します。 サイトを指定しなかった場合は、既定のトップレベル サイトが使用されます (たとえば、 `https://servername`、 `https://servername/site`、 `https://servername/site/subsite`) として表示されます。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. ソリューション エクスプローラーで、パブリッシュするレポートを右クリックし、 **[配置]** をクリックします。 これで、 **[TargetReportFolder]** で指定した場所にレポートがパブリッシュされます。 配置エラーは出力ウィンドウに表示されます。  
  
## <a name="see-also"></a>参照  
 [[プロパティ ページ] ダイアログ ボックス](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)   
 [レポート サーバーへのレポートのパブリッシュ](../../reporting-services/reports/publishing-reports-to-a-report-server.md)   
 [SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 &#40;SSRS&#41;](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [レポートで Office Data Connection &#40;.odc&#41; を使用する &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
