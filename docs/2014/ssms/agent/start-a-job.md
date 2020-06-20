---
title: ジョブの開始 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d5af895df518a915dacd953331b9139471933aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058669"
---
# <a name="start-a-job"></a>Start a Job
  このトピック [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、または SQL Server 管理オブジェクトを使用して、でエージェントジョブの実行を開始する方法について説明し [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。  
  
 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行される特定の一連の処理のことです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブは、1 つのローカル サーバーで実行することも、複数のリモート サーバーで実行することもできます。  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ジョブを開始する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
  
### <a name="to-start-a-job"></a>ジョブを開始するには  
  
1.  **オブジェクト エクスプローラー**で、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。 ジョブの開始方法に応じて、次のいずれかを行います。  
  
    -   単一のサーバーまたはターゲット サーバー上で作業を行っている場合、またはマスター サーバー上でローカル サーバー ジョブを実行している場合、開始するジョブを右クリックして、**[ジョブの開始]** をクリックします。  
  
    -   複数のジョブを開始するには、 **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。 ジョブの利用状況モニターでは、複数のジョブを選択し、選択内容を右クリックして、 **[ジョブの開始]** をクリックできます。  
  
    -   マスター サーバー上で作業を行っていて、すべての対象サーバーで同時にジョブを実行する場合、開始するジョブを右クリックし、 **[ジョブの開始]** をクリックします。次に、 **[すべての対象サーバーで開始]** をクリックします。  
  
    -   マスター サーバー上で作業を行っていて、ジョブのターゲット サーバーを指定する場合、開始するジョブを右クリックし、**[ジョブの開始]** をクリックします。次に、**[特定のターゲット サーバーで開始]** をクリックします。 **[ダウンロード命令の通知]** ダイアログ ボックスの **[特定のターゲット サーバー]** チェック ボックスをオンにし、このジョブが実行される各ターゲット サーバーを選択します。  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
  
### <a name="to-start-a-job"></a>ジョブを開始するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 詳細については、「[sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)」をご覧ください。  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 管理オブジェクトの使用  

### <a name="to-start-a-job"></a>ジョブを開始するには
  
 Visual Basic、Visual C#、PowerShell などのプログラミング言語で `Start` クラスの `Job` メソッドを呼び出します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
