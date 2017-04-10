---
title: "チュートリアルの前提条件 (レポート ビルダー) | Microsoft Docs"
ms.custom: ""
ms.date: "06/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# チュートリアルの前提条件 (レポート ビルダー)
レポート ビルダー チュートリアルを実行するには、レポート サーバー上、またはレポート サーバーと統合されている SharePoint サイト上で、[!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] のページ分割されたレポートを表示および保存できる必要があります。 すべてのチュートリアルでは、データを取得するために、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のインスタンスで処理される必要があるリテラル クエリを使用します。  
  
レポート サーバーやサイト、またはデータ ソースにアクセスできない場合は、オフラインのレポートを作成することによってレポート ビルダーについて学習できます。 「[チュートリアル: オフラインでのクイック グラフ レポートの作成 (レポート ビルダー)](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)」を参照してください。  
  
## 必要条件  
レポート ビルダーのチュートリアルを完了するには、次の条件を満たしている必要があります。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] レポート ビルダーへのアクセス。 [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーまたは SharePoint 統合モードの [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーから、レポート ビルダーを実行できます。 これらの異なるサーバーでは、最初の手順であるレポート ビルダーを開く方法のみが異なります。  
  
    レポート サーバーで、**[新規]** > **[ページ分割されたレポート]** を選択します。
  
    SharePoint 統合モードのレポート サーバーで、**[ドキュメント]** タブの **[新しいドキュメント]** を選択し、ドロップ ダウン リストから **[レポート ビルダー レポート]** を選択します。 たとえば、`http://<servername>/sites/mySite/reports` のようにします。 SharePoint 管理者は、各ドキュメント ライブラリのレポート ビルダー レポート機能を有効にする必要があります。  
  
-   [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバー、または [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] レポート サーバーと統合されている SharePoint サイトの URL。 レポート、共有データ ソース、共有データセット、レポート パーツ、およびモデルを保存および表示する権限が必要です。 既定では、レポート サーバーの URL は `http://<servername>/reportserver` です。 既定では、SharePoint サイトの URL は `http://<sitename>` または `http://<server>/site` です。  
  
-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスの名前と任意のデータベースへの読み取り専用アクセスに必要な資格情報。 チュートリアルのデータセット クエリでは、リテラル データを使用します。ただし、各クエリは、レポート データセットに必要なメタデータを返すように、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスで処理される必要があります。 たとえば、`data source=<servername>` という接続文字列では、サーバーしか指定されていません。 この場合は、そのサーバーにアクセスする権限を付与したシステム管理者によって割り当てられた既定のデータベースに対する読み取りアクセス権が必要です。 `data source=<servername>;initial catalog=<database>` という接続文字列のように、データベースを指定することもできます。  
  
-   「[マップ レポート](Tutorial:%20Map%20Report%20\(Report%20Builder\).md)」チュートリアルでは、レポート サーバーが Bing Maps を背景としてサポートするように構成されている必要があります。 詳細については、「[マップ レポートのサポートを計画する](http://msdn.microsoft.com/ja-jp/5ddc97a7-7ee5-475d-bc49-3b814dce7e19)」を参照してください。   

-   「[詳細レポートとメイン レポートの作成](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md)」チュートリアルでは、Contoso Sales キューブへのアクセスが必要です。 詳細については、チュートリアルを参照してください。 
  
レポート サーバー管理者は、レポート サーバーに対する必要な権限の許可、[!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] のフォルダーの場所の構成、およびレポート ビルダーの既定のオプションの構成を行う必要があります。 詳細については、「[レポート ビルダーのインストールとアンインストール](../Topic/Install%20and%20Uninstall%20Report%20Builder.md)」を参照してください。  
  
## 参照  
[レポート ビルダー チュートリアル](../reporting-services/report-builder-tutorials.md)  
  
