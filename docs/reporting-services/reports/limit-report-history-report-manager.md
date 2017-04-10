---
title: "レポート履歴を制限する (レポート マネージャー) | Microsoft Docs"
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
  - "レポート履歴の確認"
  - "レポート履歴 [Reporting Services], 表示履歴"
  - "レポート履歴 [Reporting Services], 構成履歴"
  - "履歴データ [Reporting Services]"
  - "レポート履歴の表示"
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# レポート履歴を制限する (レポート マネージャー)
  レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。 レポート履歴は必要時に作成できるほか、どの程度の頻度でスナップショットを作成し、レポート履歴に追加するかをスケジュールで設定することもできます。  
  
 レポート履歴は、レポート サーバー データベースに格納されます。 レポート スナップショットに大量のデータが含まれている場合は、スナップショットを保持することによるデータベース サイズへの影響を最小限に抑えるために、レポート履歴を制限することを検討する必要があります。  
  
### レポート サーバーのレポート履歴を構成するには  
  
1.  レポート マネージャーのグローバル ツール バーで、**[サイトの設定]** をクリックします。  
  
2.  すべてのレポート履歴を制限なく保持する場合は、**[レポート履歴に無制限の数のスナップショットを保持する]** を選択します。 それ以外の場合は、**[レポート履歴のコピーの数を制限する]** を選択し、特定のレポートに対して保持できるスナップショットの最大数を指定します。  
  
3.  **[適用]**をクリックします。  
  
### 特定のレポートのレポート履歴を構成するには  
  
1.  レポート マネージャーで、履歴を構成するレポートに移動し、そのレポートをクリックして開きます。  
  
2.  **[プロパティ]** タブをクリックします。  
  
3.  **[履歴]** タブをクリックします。  
  
4.  レポートのオプションを選択し、**[適用]** をクリックします。 各オプションに関する詳細については、「[[スナップショット オプション] プロパティ ページ &#40;レポート マネージャー&#41;](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md)」を参照してください。  
  
## 参照  
 [レポート履歴へのスナップショットの追加 &#40;レポート マネージャー&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  