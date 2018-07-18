---
title: ジョブ カテゴリへのジョブの割り当て | Microsoft Docs
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
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8dbed6c673968c46264487ed606e2fc2586dd4a6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275688"
---
# <a name="assign-a-job-to-a-job-category"></a>ジョブ カテゴリへのジョブの割り当て
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブをジョブ カテゴリに割り当てる方法について説明します。  
  
 ジョブ カテゴリを使用してジョブを管理すると、フィルター操作やグループ化を簡単に行うことができます。 たとえば、データベース バックアップに関するすべてのジョブを [データベースのメンテナンス] カテゴリとしてまとめます。 ジョブは、ビルトイン ジョブ カテゴリに割り当てたり、ユーザー定義ジョブ カテゴリを作成し、そこに割り当てたりすることができます。  
  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>ジョブ カテゴリにジョブを割り当てるには  
  
1.  **オブジェクト エクスプ ローラー**で、プラス記号をクリックして、ジョブ カテゴリにジョブを割り当てるサーバーを展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[ジョブ]** フォルダーを展開します。  
  
4.  編集するジョブを右クリックし、 **[プロパティ]** を選択します。  
  
5.  *[ジョブのプロパティ - <ジョブ名>]* ダイアログ ボックスの **[カテゴリ]** 一覧で、ジョブに割り当てるジョブ カテゴリを選択します。  
  
6.  **[OK]** をクリックします。  
  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>ジョブ カテゴリにジョブを割り当てるには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_update_job &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)します。  
  
  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **ジョブ カテゴリにジョブを割り当てるには**  
  
 使用して、 `JobCategory` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス。  
  
  
  
  
