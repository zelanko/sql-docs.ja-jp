---
title: オペレーターにジョブの状態を通知する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
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
ms.openlocfilehash: ff9340d7c9fb768f9e057d00868a9e238421a5f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72798202"
---
# <a name="notify-an-operator-of-job-status"></a>Notify an Operator of Job Status
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)]、または SQL Server 管理オブジェクトを使用して、エージェントが[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ジョブに関する通知をオペレーターに送信できるように、で通知オプションを設定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **オペレーターにジョブの状態を通知するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server 管理オブジェクト](#SMO)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-notify-an-operator-of-job-status"></a>オペレーターにジョブの状態を通知するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  
  **[SQL Server エージェント]**、 **[ジョブ]** の順に展開し、編集するジョブを右クリックして、 **[プロパティ]** をクリックします。  
  
3.  
  **[ジョブのプロパティ]** ダイアログ ボックスで、 **[通知]** ページをクリックします。  
  
4.  オペレーターに電子メールで通知する場合、 **[電子メール]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   ジョブが**成功**した場合、ジョブが正常に完了したことをオペレーターに通知します。  
  
    -   ジョブが正常に完了しなかったときにオペレーターに通知する**ジョブが失敗した場合**。  
  
    -   **ジョブが**完了したら、完了ステータスに関係なくオペレーターに通知します。  
  
5.  オペレーターにポケットベルで通知する場合、 **[ポケットベル]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   ジョブが**成功**した場合、ジョブが正常に完了したことをオペレーターに通知します。  
  
    -   ジョブが正常に完了しなかったときにオペレーターに通知する**ジョブが失敗した場合**。  
  
    -   **ジョブが**完了したら、完了ステータスに関係なくオペレーターに通知します。  
  
6.  オペレーターに net send で通知する場合、 **[Net Send]** チェック ボックスをオンにして一覧からオペレーターを選択し、次のいずれかをクリックします。  
  
    -   ジョブが**成功**した場合、ジョブが正常に完了したことをオペレーターに通知します。  
  
    -   ジョブが正常に完了しなかったときにオペレーターに通知する**ジョブが失敗した場合**。  
  
    -   **ジョブが**完了したら、完了ステータスに関係なくオペレーターに通知します。  
  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-notify-an-operator-of-job-status"></a>オペレーターにジョブの状態を通知するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that Fran??ois Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'Fran??ois Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 詳細については、「 [sp_add_notification &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)」を参照してください。  
  
##  <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
 **オペレーターにジョブの状態を通知するには**  
  
 Visual Basic、 `Job` Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
