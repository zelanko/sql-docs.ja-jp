---
title: ジョブ カテゴリの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f939a713df2fb40f1b56fd0aee5f7b5c5876a4a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196572"
---
# <a name="delete-a-job-category"></a>ジョブ カテゴリの削除
  このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ カテゴリを削除する方法について説明します。  
  
 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。  
  

  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 ユーザー定義のジョブ カテゴリを削除するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはそのカテゴリに割り当てられているジョブを別のジョブ カテゴリに再割り当てするように要求します。 削除できるのはユーザー定義のジョブ カテゴリのみです。  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  

  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-delete-a-job-category"></a>ジョブ カテゴリを削除するには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを削除するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。  
  
4.  *[ジョブ カテゴリの管理 - <サーバー名>]* ダイアログ ボックスで、削除するジョブ カテゴリを選択します。  
  
5.  **[削除]** をクリックします。  
  
6.  **[ジョブ カテゴリ]** ダイアログ ボックスで **[はい]** をクリックします。  
  
7.  *[ジョブ カテゴリの管理 - <サーバー名>]* ダイアログ ボックスを閉じます。  
  

  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-delete-a-job-category"></a>ジョブ カテゴリを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_delete_category &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)します。  
  

  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブ カテゴリを削除するには**  
  
 呼び出す、 `JobCategory` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス。  
  

  
  
