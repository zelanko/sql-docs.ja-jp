---
title: "ポリシー ベースの管理ファセットのプロパティの表示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポリシー ベースの管理、ファセットのプロパティの表示"
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# ポリシー ベースの管理ファセットのプロパティの表示
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でポリシー ベースの管理ファセットのプロパティを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してファセットのプロパティを表示するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### ファセットのプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、プロパティを表示するファセットを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]**を展開します。  
  
4.  プラス記号をクリックして **[ファセット]** フォルダーを展開します。  
  
5.  プロパティを表示するファセットを右クリックし、**[プロパティ]** をクリックします。 **[ファセットのプロパティ – *\<ファセット名>*]** ダイアログ ボックスで使用可能なオプションの詳細については、「[[ファセットのプロパティ] ダイアログ ボックスの [全般] ページ](../Topic/Facet%20Properties%20Dialog%20Box,%20General%20Page.md)」、「[[ファセットのプロパティ] ダイアログ ボックスの [依存ポリシー] ページ](../Topic/Facet%20Properties%20Dialog%20Box,%20Dependent%20Policies%20Page.md)」、および「[[ファセットのプロパティ] ダイアログ ボックスの [依存条件] ページ](../Topic/Facet%20Properties%20Dialog%20Box,%20Dependent%20Conditions%20Page.md)」をご覧ください。  
  
6.  完了したら、 **[閉じる]**をクリックします。  
  
  