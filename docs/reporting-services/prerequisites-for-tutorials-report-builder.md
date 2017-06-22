---
title: "チュートリアル (レポート ビルダー) の前提条件 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2c2056dccbb2d65e880928e4ec37a70080cfbf53
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---

# <a name="prerequisites-for-tutorials-report-builder"></a>チュートリアルの前提条件 (レポート ビルダー)

レポート ビルダー チュートリアルを実行するには、レポート サーバー上、またはレポート サーバーと統合されている SharePoint サイト上で、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] のページ分割されたレポートを表示および保存できる必要があります。 データの場合は、すべてのチュートリアルは、SQL Server のインスタンスによって処理される必要があるリテラル クエリを使用します。  
  
レポート サーバーやサイト、またはデータ ソースにアクセスできない場合は、オフラインのレポートを作成することによってレポート ビルダーについて学習できます。 「[チュートリアル: オフラインでのクイック グラフ レポートの作成 (レポート ビルダー)](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)」を参照してください。  

## <a name="requirements"></a>必要条件

レポート ビルダーのチュートリアルを完了するには、次の条件を満たしている必要があります。  
  
-   レポート ビルダーへのアクセス。 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーまたは SharePoint 統合モードの [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーから、レポート ビルダーを実行できます。 これらの異なるサーバーでは、最初の手順であるレポート ビルダーを開く方法のみが異なります。  
  
    レポート サーバーで、 **[新規]** > **[ページ分割されたレポート]**を選択します。
  
    SharePoint 統合モードのレポート サーバーで、 **[ドキュメント]** タブの **[新しいドキュメント]**を選択し、ドロップ ダウン リストから **[レポート ビルダー レポート]**を選択します。 たとえば、 `http://<servername>/sites/mySite/reports`のようにします。 SharePoint 管理者は、各ドキュメント ライブラリのレポート ビルダー レポート機能を有効にする必要があります。  
  
-   [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバー、または [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーと統合されている SharePoint サイトの URL。 レポート、共有データ ソース、共有データセット、レポート パーツ、およびモデルを保存および表示する権限が必要です。 既定では、レポート サーバーの URL は `http://<servername>/reportserver`です。 既定では、SharePoint サイトの URL は `http://<sitename>` または `http://<server>/site`です。  
  
-   SQL Server インスタンスと任意のデータベースに読み取り専用アクセスのための十分な資格情報の名前。 データセット クエリのチュートリアルでは、リテラル データを使用するが、各クエリは、レポート データセットに必要なメタデータを返す SQL Server インスタンスによって処理する必要があります。 たとえば、 `data source=<servername>`という接続文字列では、サーバーしか指定されていません。 この場合は、そのサーバーにアクセスする権限を付与したシステム管理者によって割り当てられた既定のデータベースに対する読み取りアクセス権が必要です。 `data source=<servername>;initial catalog=<database>`という接続文字列のように、データベースを指定することもできます。  
  
-   [チュートリアル: マップ レポート (レポート ビルダー)](Tutorial:%20Map%20Report%20\(Report%20Builder\).md)、背景として Bing maps をサポートするために、レポート サーバーを構成する必要があります。 詳細については、「 [マップ レポートのサポートを計画する](http://msdn.microsoft.com/en-us/5ddc97a7-7ee5-475d-bc49-3b814dce7e19)」を参照してください。   

-   [チュートリアル: を作成する詳細レポートとメイン レポート (レポート ビルダー)](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md)チュートリアルには、Contoso Sales キューブへのアクセスが必要です。 詳細については、チュートリアルを参照してください。 
  
レポート サーバー管理者は、レポート サーバーに対する必要な権限の許可、 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] のフォルダーの場所の構成、およびレポート ビルダーの既定のオプションの構成を行う必要があります。 詳細については、「 [レポート ビルダーのインストールとアンインストール](http://msdn.microsoft.com/library/2c9a5814-17bf-4947-8fb3-6269e7caa416)」を参照してください。  

## <a name="next-steps"></a>次の手順

[レポート ビルダー チュートリアル](../reporting-services/report-builder-tutorials.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
