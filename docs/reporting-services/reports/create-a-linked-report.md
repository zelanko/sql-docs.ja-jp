---
title: "リンク レポートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "リンク レポート [Reporting Services], 作成"
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
caps.latest.revision: 44
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 44
---
# リンク レポートを作成する
  リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。 概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。  
  
 リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。 リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。 セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。  
  
 既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。 たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。  
  
 リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。 リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。  
  
### リンク レポートを作成するには  
  
1.  レポート マネージャーで、リンク先のレポートのあるフォルダーに移動し、オプション メニューを開いて、**[リンク レポートの作成]** をクリックします。  
  
2.  新規リンク レポートの名前を入力します。 必要に応じて、説明を入力します。  
  
3.  レポートを別のフォルダーに保存するには、**[場所の変更]** をクリックします。 保存先のフォルダーをクリックするか、または **[場所]** ボックスにフォルダー名を入力します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)] 別のフォルダーを指定しない場合、現在のフォルダー (リンク先のレポートが保存されているフォルダー) にリンク レポートが作成されます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] リンク レポートが表示されます。  
  
     リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。 次のアイコンでリンク レポートを示します。  
  
     ![リンク レポート アイコン](../../reporting-services/report-server/media/hlp-16linked.png "リンク レポート アイコン")  
  
## 参照  
 [レポートを開閉する (レポート マネージャー)](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [新しいリンク レポート ページ (レポート マネージャー)](../Topic/New%20Linked%20Report%20Page%20\(Report%20Manager\).md)   
 [アイテムの場所の選択 ページ (レポート マネージャー)](../Topic/Choose%20Item%20Location%20Page%20\(Report%20Manager\).md)   
 [全般プロパティ ページ、レポート (レポート マネージャー)](../Topic/General%20Properties%20Page,%20Reports%20\(Report%20Manager\).md)   
 [Reporting Services の概念 (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [レポート マネージャー (SSRS ネイティブ モード)](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  