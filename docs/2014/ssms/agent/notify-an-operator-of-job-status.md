---
title: オペレーターにジョブの状態を通知する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7762daa362b73f981603f7d32a41b8084327e1f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185322"
---
# <a name="notify-an-operator-of-job-status"></a>Notify an Operator of Job Status
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントからジョブに関する通知をオペレーターに送信するための通知オプションを設定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **オペレーターにジョブの状態を通知する方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-notify-an-operator-of-job-status"></a>オペレーターにジョブの状態を通知するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、編集するジョブを右クリックして、 **[プロパティ]** をクリックします。  
  
3.  **[ジョブのプロパティ]** ダイアログ ボックスで、 **[通知]** ページをクリックします。  
  
4.  オペレーターに電子メールで通知する場合、 **[電子メール]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   **[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。  
  
    -   **[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。  
  
    -   **[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。  
  
5.  オペレーターにポケットベルで通知する場合、 **[ポケットベル]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   **[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。  
  
    -   **[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。  
  
    -   **[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。  
  
6.  オペレーターに net send で通知する場合、 **[Net Send]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   **[ジョブ成功時]** : ジョブが正常に完了した場合にオペレーターに通知します。  
  
    -   **[ジョブ失敗時]** : ジョブが正常に完了しなかった場合にオペレーターに通知します。  
  
    -   **[ジョブ完了時]** : 完了時の状態とは関係なくオペレーターに通知します。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-notify-an-operator-of-job-status"></a>オペレーターにジョブの状態を通知するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'François Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_add_notification &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)します。  
  
##  <a name="SMO"></a> SQL Server 管理オブジェクトの使用  
 **オペレーターにジョブの状態を通知するには**  
  
 使用して、 `Job` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラス。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  
  
