---
title: "レポートのプレビュー | Microsoft Docs"
ms.custom: 
ms.date: 05/05/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Report Designer [Reporting Services], previewing reports
- previewing reports [Reporting Services]
- printing previews
- test servers [Reporting Services]
ms.assetid: 85117f6c-828e-45c9-810f-e700d9bfba67
caps.latest.revision: "44"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1ee5dbf3a8823554acbb811e874bfcd09196c0a1
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="previewing-reports"></a>レポートのプレビュー
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートをデザインするときに、そのレポートを実稼働環境にパブリッシュする前に表示することができます。 これを行うには、レポート デザイナーでプレビュー モードに切り替えるか、レポート デザイナーのプレビュー ウィンドウを使用するか、テスト環境のレポート サーバーにレポートをパブリッシュします。  
  
> [!NOTE]  
>  レポートをプレビューすると、レポートのデータがローカル コンピューターのファイルにキャッシュされます。 同じレポートを、同じクエリ、パラメーター、および資格情報を使用して再びプレビューすると、レポート デザイナーはクエリを再実行する代わりにキャッシュされたコピーを表示します。 データ ファイルは *\<reportname>*.rdl.data として、レポート定義ファイルと同じディレクトリに保存されます。 レポート デザイナーを終了してもファイルは削除されません。  
  
## <a name="preview-mode"></a>プレビュー モード  
 レポート デザイナーの ![ssrs_ssdt_preview](../../reporting-services/media/ssrs-ssdt-preview.png "ssrs_ssdt_preview") をクリックして、レポートをプレビューできます。 この場合、レポート サーバーで提供されるものと同じレポート処理および表示機能を使用して、レポートがローカルで実行されます。 表示されるレポートは対話型のイメージです。ユーザーは、パラメーターの選択、リンクのクリック、ドキュメント マップの表示、レポートの非表示部分の展開と折りたたみなどを行うことができます。 また、インストールされている任意の表示形式にレポートをエクスポートできます。  
  
## <a name="standalone-preview"></a>スタンドアロン プレビュー  
 レポートをプレビューするもう 1 つの方法は、作成したカスタム アセンブリをデバッグする際などに、デバッグ構成でレポート プロジェクトを実行することです。 レポートは既定のブラウザーで開きます。 プロジェクトの実行方法には、次の 3 とおりがあります。  
  
-   **[デバッグ]** メニューの **[デバッグ開始]** をクリックする。  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の標準ツールバー ![ssrs_ssdt_startdebug](../../reporting-services/reports/media/ssrs-ssdt-startdebug.png "ssrs_ssdt_startdebug") の **[開始]** ボタンをクリックする。  
  
-   **F5**キーを押す。  
  
 レポートを作成しても配置しないプロジェクト構成を使用している場合は、現在の構成の **StartItem** プロパティで指定されたレポートが、別のプレビュー ウィンドウで開きます。 プレビュー ウィンドウは、プレビュー モードと同じ方法でレポートを表示し、同じ機能を提供します。  
  
> [!NOTE]  
>  レポートをデバッグする前に、開始アイテムを設定する必要があります。 たとえば、デバッグ モードを実行すると、ブラウザーはレポートではなくメイン レポートのサーバー ページをプレビュー モードで開きます。 開始アイテムを設定するには、ソリューション エクスプローラーでレポート プロジェクトを右クリックし、 **[プロパティ]**をクリックします。次に、 **[StartItem]**で、表示するレポートの名前を選択します。  
  
 プロジェクトの開始アイテムではない特定のレポートをプレビューする場合は、レポートを作成しても配置しない構成 (DebugLocal 構成など) を選択し、レポートを右クリックして、 **[実行]**をクリックします。 レポートを配置しない構成を選択する必要があります。そうしないと、レポートはローカルのプレビュー ウィンドウに表示されずに、レポート サーバーにパブリッシュされます。  
  
## <a name="publishing-to-a-test-server"></a>テスト サーバーへのパブリッシュ  
 レポートのテストは、テスト サーバーにレポートをパブリッシュしてレポートを参照し、プレビューすることで行うこともできます。 テスト サーバーにレポートをパブリッシュする操作は、実稼働サーバーにレポートをパブリッシュする場合と同じです。 レポートのパブリッシュ方法の詳細については、「 [レポート サーバーへのレポートのパブリッシュ](../../reporting-services/reports/publishing-reports-to-a-report-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/print-reports-report-builder-and-ssrs.md)   
 [レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)   
 [レポートのパブリッシュ](http://msdn.microsoft.com/library/ef5a514e-e818-4041-a8b0-15835f9a046b)   
 [レポートでのカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
