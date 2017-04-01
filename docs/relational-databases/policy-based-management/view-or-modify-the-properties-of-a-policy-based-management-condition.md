---
title: "ポリシー ベースの管理条件のプロパティの表示または変更 | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポリシー ベースの管理、ポリシー条件の表示"
  - "ポリシー ベースの管理、ポリシー条件の変更"
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# ポリシー ベースの管理条件のプロパティの表示または変更
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] でポリシー ベースの管理条件のプロパティを表示または変更する方法について説明します。  
  

  
##  <a name="BeforeYouBegin"></a> はじめに  
  

  
####  <a name="Permissions"></a> Permissions  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### 条件のプロパティを表示または変更するには  
  
1.  **オブジェクト エクスプローラー**で、表示または変更する条件を含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[管理]** フォルダーを展開します。  
  
3.  プラス記号をクリックして **[ポリシー管理]**を展開します。  
  
4.  プラス記号をクリックして **[条件]** フォルダーを展開します。  
  
5.  表示または編集する条件を右クリックし、**[プロパティ]** をクリックします。 [**条件を開く-***condition_name*] ダイアログ ボックスで使用可能なオプションの詳細については、「[[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [全般] ページ](../Topic/Create%20New%20Condition%20or%20Open%20Condition%20Dialog%20Box,%20General%20Page.md)」、「[[条件を開く] ダイアログ ボックス、[依存ポリシー] ページ](../Topic/Open%20Condition%20Dialog%20Box,%20Dependent%20Policies%20Page.md)」「[[新しい条件の作成] または [条件を開く] ダイアログ ボックスの [説明] ページ](../Topic/Create%20New%20Condition%20or%20Open%20Condition%20Dialog%20Box,%20Description%20Page.md)」、「[[高度な編集] &#40;条件&#41; ダイアログ ボックス](../Topic/Advanced%20Edit%20\(Condition\)%20Dialog%20Box.md)」を参照してください。  
  
6.  完了したら、 **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 条件のプロパティを表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 詳細については、「[syspolicy_conditions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md)」を参照してください。  
  
  