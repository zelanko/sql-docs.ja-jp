---
title: "ジョブ履歴の表示 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- viewing job history
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
- displaying job history
ms.assetid: 3bbd1556-abdb-48a3-b249-546eace76343
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6a9516665f4aaa42d93ccae0dae9388589b58069
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="view-the-job-history"></a>View the Job History
このトピックでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、[!INCLUDE[tsql](../../includes/tsql_md.md)]、または SQL Server 管理オブジェクトを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのジョブ履歴ログを表示する方法について説明します。  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ履歴ログを表示する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-view-the-job-history-log"></a>ジョブ履歴ログを表示するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を展開し、 **[ジョブ]**を展開します。  
  
3.  ジョブを右クリックし、 **[履歴の表示]**をクリックします。  
  
4.  ログ ファイル ビューアーにジョブ履歴が表示されます。  
  
5.  ジョブ履歴を更新するには、 **[最新の情報に更新]**をクリックします。 表示する列を少なくするには、 **[フィルター]** ボタンをクリックし、フィルターのパラメーターを入力します。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-view-the-job-history-log"></a>ジョブ履歴ログを表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- lists all job information for the NightlyBackups job.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobhistory   
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
詳しくは、「 [sp_help_jobhistory (Transact-SQL)](http://msdn.microsoft.com/en-us/a944d44e-411b-4735-8ce4-73888d4262d7)」をご覧ください。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ履歴ログを表示するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **Job** クラスの **EnumHistory** メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  

