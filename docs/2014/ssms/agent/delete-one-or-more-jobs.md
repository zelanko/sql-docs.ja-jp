---
title: 1 つまたは複数のジョブの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0d9df271c457cb0f05f9fdfe70952b6d02224963
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783255"
---
# <a name="delete-one-or-more-jobs"></a>1 つまたは複数のジョブの削除
  このトピックでは、で[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、、または SQL Server 管理オブジェクト[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を[!INCLUDE[tsql](../../includes/tsql-md.md)]使用して、エージェントジョブを削除する方法について説明します。  
  
 
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 
  **sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか削除できません。  
  
 
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-delete-a-job"></a>ジョブを削除するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  
  **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、削除するジョブを右クリックして、 **[削除]** をクリックします。  
  
3.  
  **[オブジェクトの削除]** ダイアログ ボックスで、削除するジョブが選択されていることを確認します。  
  
4.  **[OK]** をクリックします。  
  
#### <a name="to-delete-multiple-jobs"></a>複数のジョブを削除するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  
  **[SQL Server エージェント]** を展開します。  
  
3.  [ジョブの**利用状況モニター**] を右クリックし、[**ジョブの利用状況の表示**] をクリックします。  
  
4.  ジョブの利用状況モニターで、削除する複数のジョブを選択します。次に、選択したジョブを右クリックして、 **[ジョブの削除]** をクリックします。  
  

  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-delete-a-job"></a>ジョブを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 詳細については、「 [sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)」を参照してください。  

##  <a name="SMO"></a>SQL Server 管理オブジェクトの使用  

### <a name="to-delete-multiple-jobs"></a>複数のジョブを削除するには
  
 Visual Basic、 `JobCollection` Visual C#、PowerShell など、選択したプログラミング言語でクラスを使用します。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](https://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
