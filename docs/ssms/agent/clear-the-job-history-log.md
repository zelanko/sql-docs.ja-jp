---
title: "ジョブ履歴ログのクリア | Microsoft Docs"
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
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8ece46cd518c4b94094015e26d1c8d6587edce50
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="clear-the-job-history-log"></a>Clear the Job History Log
このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] or SQL Server Management Objects.  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ履歴ログを消去する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-clear-the-job-history-log"></a>ジョブ履歴ログを消去するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**を展開し、 **[ジョブ]**を展開します。  
  
3.  ジョブを右クリックし、 **[履歴の表示]**をクリックします。  
  
4.  **[ログ ファイルの表示]**ダイアログ ボックスで、履歴を消去するジョブを選択し、次のいずれかの手順を実行します。  
  
    -   **[削除]**をクリックし、 **[履歴の削除]** ダイアログ ボックスの **[すべての履歴を削除する]** をクリックします。 すべてのジョブ履歴を削除することも、指定日よりも古い履歴のみを削除することもできます。 すべてのジョブ履歴を削除するには、 **[すべての履歴を削除する]**をクリックします。 指定日よりも古いジョブ履歴ログを削除するには、 **[次の日付以前の履歴を削除する]**をクリックしてから日付を指定します。  
  
    -   マルチサーバー ジョブの履歴ログを消去するには、 **[ジョブ ステータス]** をクリックします。 **[ジョブ]**をクリックしてからジョブ名をクリックし、 **[ジョブ履歴の表示]**をクリックします。  
  
5.  **[削除]**をクリックします。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-clear-the-job-history-log"></a>ジョブ履歴ログを消去するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ履歴ログを消去するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **JobServer** クラスの **PurgeJobHistory** メソッドを使用します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  

