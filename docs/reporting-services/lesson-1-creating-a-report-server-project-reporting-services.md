---
title: "レッスン 1: 作成、レポート サーバー プロジェクト (Reporting Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
caps.latest.revision: 57
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 6292a812cb1456892a6dad78408d0d64ce0b1a9e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/27/2017

---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>レッスン 1 : レポート サーバー プロジェクトの作成 (Reporting Services)

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。[レッスン 1: レポート サーバー プロジェクト (Reporting Services) を作成する](https://msdn.microsoft.com/en-US/library/ms167559(SQL.120).aspx)です。

このレッスンで、 *レポート サーバー プロジェクト* と *レポート定義 (.rdl)* ファイルを [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)] Visual Studio 内に作成します。 

[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でレポートを作成するには、まず、レポート定義ファイル (.rdl) やレポートに必要なその他のリソース ファイルを格納できる、レポート サーバー プロジェクトが必要です。 

次のレッスンでは、実際のレポート定義ファイルを作成し、レポートのデータ ソース、データセット、レイアウトを定義します。 作成したレポートを実行すると、データが取得され、レイアウト定義に従って画面上に表示されます。 その状態からエクスポート、印刷、保存を行うことができます。  
  
  
  
## <a name="to-create-a-report-server-project"></a>レポート サーバー プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio_md](../includes/ssbidevstudio-md.md)]を開きます。  
  
2.  **ファイル**メニュー >**新規** > **プロジェクト**です。  

    ![ssrs-ssdt-file-01-new-project](../reporting-services/media/ssrs-ssdt-file-01-new-project.png)
  
3.  **[インストール済み]** > **[テンプレート]** > **[ビジネス インテリジェンス]**で、 **[Reporting Services]**をクリックします。

    ![ssrs-ssdt-01-new-rs-project](../reporting-services/media/ssrs-ssdt-01-new-rs-project.png)

5. **[レポート サーバー プロジェクト]** ![ssrs_ssdt_report_server_project](../reporting-services/media/ssrs-ssdt-report-server-project.png)でレポート サーバー プロジェクトを作成する方法を学習します。 

   >**注**: が表示されない場合、 **Business Intelligence**または**レポート サーバー プロジェクト**オプション、ビジネス インテリジェンス テンプレートで SSDT を更新する必要があります。 「 [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)」を参照してください。  
  
5.  **[名前]**に「 **utorial**」と入力します。  

    既定では、新しいディレクトリの Visual Studio 2015\Projects フォルダーに作成されます。
    
    ![ssrs-ssdt-01-solution-location](../reporting-services/media/ssrs-ssdt-01-solution-location.png)
  
6.  **[OK]** をクリックすると、プロジェクトが作成されます。  
  
    Tutorial プロジェクトが右側の [ソリューション エクスプローラー] ウィンドウに表示されます。  
  
## <a name="to-create-a-new-report-definition-file"></a>新しいレポート定義ファイルを作成するには  
  
1.  **[ソリューション エクスプローラー]** ウィンドウで、 **[レポート] を右クリックし、** > **[追加]** > **[新しいアイテム]**の順に選択します。 

    >**ヒント**: **[ソリューション エクスプローラー]** ウィンドウが表示されない場合は、 **[表示]** メニューの **[ソリューション エクスプローラー]**をクリックします。 

    ![ssrs_ssdt_add_report](../reporting-services/media/ssrs-ssdt-add-report.png)
  
2.  **[新しいアイテムの追加]** ウィンドウで、 **[レポート]** ![ssrs_ssdt_report](../reporting-services/media/ssrs-ssdt-report.png)でレポート サーバー プロジェクトを作成する方法を学習します。  
  
3.  **[名前]**に「 **Sales Orders.rdl** 」と入力して、 **[追加]**をクリックします。  
  
    レポート デザイナーを開き、デザイン ビューで新しい .rdl ファイルを表示します。  
    
    ![ssrs-ssdt-01-new-report-designer](../reporting-services/media/ssrs-ssdt-01-new-report-designer.png)
  
     レポート デザイナーは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で実行される [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]コンポーネントです。 **[デザイン]** ビューと **[プレビュー]**ビューの 2 つのビューがあります。 ビューを変更するには該当するタブをクリックします。  
  
    **[レポート データ]** ペインでデータを定義します。 **[デザイン]** ビューではレポートのレイアウトを定義します。 **[プレビュー]** ビューではレポートを実行して結果を確認できます。  
  
## <a name="next-lesson"></a>次のレッスン  
ここでは、"Tutorial" というレポート プロジェクトを作成し、このレポート プロジェクトにレポート定義ファイル (.rdl) を追加しました。 次に、レポートで使用するデータ ソースを指定します。 参照してください[レッスン 2: 接続情報 &#40; を指定します。Reporting Services &#41;](../reporting-services/lesson-2-specifying-connection-information-reporting-services.md).  
  
## <a name="see-also"></a>参照  
[基本的なテーブル レポートの作成 (SSRS チュートリアル)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  
  


