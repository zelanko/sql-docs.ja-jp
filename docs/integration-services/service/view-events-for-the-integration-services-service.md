---
title: "Integration Services サービスのイベントを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント [Integration Services]"
  - "サービス [Integration Services], イベント"
  - "Integration Services サービス, イベント"
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Integration Services サービスのイベントを表示する
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスのイベントを表示できるツールには、次の 2 つがあります。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の **[ログ ファイルの表示]** ダイアログ ボックス。 **[ログ ファイルの表示]** ダイアログ ボックスには、ログのエクスポート、フィルター、および検索を行うオプションがあります。 **[ログ ファイルの表示]** のオプションの詳細については、「[[ログ ファイルの表示] の F1 ヘルプ](../Topic/Log%20File%20Viewer%20F1%20Help.md)」を参照してください。  
  
-   Windows イベント ビューアー。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サービスによってログに記録されるイベントの詳細については、「[Integration Services サービスによってログに記録されるイベント](../../integration-services/service/events-logged-by-the-integration-services-service.md)」を参照してください。  
  
### SQL Server Management Studio で Integration Services のサービス イベントを表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きます。  
  
2.  **[ファイル]** メニューの **[オブジェクト エクスプローラーを接続]** をクリックします。  
  
3.  **[サーバーへの接続]** ダイアログ ボックスで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のサーバーの種類を選択し、接続するサーバー名を選択または参照して、**[接続]** をクリックします。  
  
4.  オブジェクト エクスプローラーで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を右クリックして、**[ログの表示]** をクリックします。  
  
5.  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のイベントを表示するには、**[SQL Server Integration Services]** を選択します。 **[NT イベント]** オプションは、**[SQL Server Integration Services]** オプションに応じて、自動的に選択または選択解除されます。  
  
### Windows イベント ビューアーで Integration Services のサービス イベントを表示するには  
  
1.  **[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]**、カテゴリの表示を使用している場合は **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。  
  
2.  **[イベント ビューアー]** をクリックします。  
  
3.  **[イベント ビューアー]** ダイアログ ボックスで、**[アプリケーション]** をクリックします。  
  
4.  **[アプリケーション]** スナップインから **[ソース]** 列の値が **[SQLISService]** のエントリを探して右クリックし、**[プロパティ]** をクリックします。  
  
5.  必要に応じて、上矢印または下矢印をクリックして、前後のイベントを表示します。  
  
6.  必要に応じて、[クリップボードにコピー] アイコンをクリックして、イベントの情報をコピーします。  
  
7.  イベントのデータをバイトと単語のどちらで表示するか選択します。  
  
8.  **[OK]**をクリックします。  
  
9. **[ファイル]** メニューの **[終了]** をクリックして、**[イベント ビューアー]** ダイアログ ボックスを閉じます。  
  
## 参照  
 [Integration Services サービスを管理する](../../integration-services/service/manage-the-integration-services-service.md)   
 [データ フロー パフォーマンス カウンターのログを追加する](../../integration-services/performance/add-a-log-for-data-flow-performance-counters.md)  
  
  