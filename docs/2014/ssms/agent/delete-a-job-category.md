---
title: ジョブ カテゴリの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bb392991afbb3707fafdb18a28cc3de53f97c78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783200"
---
# <a name="delete-a-job-category"></a>ジョブ カテゴリの削除
  このトピックでは、または[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Server 管理オブジェクトを使用[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でエージェントジョブカテゴリを削除する方法について説明します。  
  
 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。  

##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 ユーザー定義のジョブ カテゴリを削除するとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントはそのカテゴリに割り当てられているジョブを別のジョブ カテゴリに再割り当てするように要求します。 削除できるのはユーザー定義のジョブ カテゴリのみです。  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  

##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
### <a name="to-delete-a-job-category"></a>ジョブ カテゴリを削除するには  
  
1.  
  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリを削除するサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  
  **[ジョブ]** フォルダーを右クリックし、 **[ジョブ カテゴリの管理]** をクリックします。  
  
4.  [**ジョブカテゴリ**_server_name_の管理] ダイアログボックスで、削除するジョブカテゴリを選択します。  
  
5.  
  **[削除]** をクリックします。  
  
6.  
  **[ジョブ カテゴリ]** ダイアログ ボックスで **[はい]** をクリックします。  
  
7.  [**ジョブカテゴリ**の_server_name_の管理] ダイアログボックスを閉じます。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
### <a name="to-delete-a-job-category"></a>ジョブ カテゴリを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 詳細については、「 [sp_delete_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)」を参照してください。  

  
##  <a name="SMO"></a>SQL Server 管理オブジェクトの使用  

### <a name="to-delete-a-job-category"></a>ジョブ カテゴリを削除するには
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `JobCategory` クラスを呼び出します。  
