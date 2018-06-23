---
title: 1 つまたは複数のジョブの削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98721e58322867b942703fc245115b497ad79c34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164220"
---
# <a name="delete-one-or-more-jobs"></a>1 つまたは複数のジョブの削除
  このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、または SQL Server 管理オブジェクトを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、 or SQL Server Management Objects.  
  
 
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
 **sysadmin** 固定サーバー ロールのメンバー以外は、所有しているジョブしか削除できません。  
  
 
  
##  <a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-delete-a-job"></a>ジョブを削除するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開し、 **[ジョブ]** を展開します。次に、削除するジョブを右クリックして、 **[削除]** をクリックします。  
  
3.  **[オブジェクトの削除]** ダイアログ ボックスで、削除するジョブが選択されていることを確認します。  
  
4.  **[OK]** をクリックします。  
  
#### <a name="to-delete-multiple-jobs"></a>複数のジョブを削除するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブの利用状況モニター]** を右クリックし、 **[ジョブの利用状況の表示]** をクリックします。  
  
4.  ジョブの利用状況モニターで、削除する複数のジョブを選択します。次に、選択したジョブを右クリックして、 **[ジョブの削除]** をクリックします。  
  

  
##  <a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-delete-a-job"></a>ジョブを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 詳細については、次を参照してください。 [sp_delete_job &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)です。  
  

  
##  <a name="SMO"></a> SQL Server 管理オブジェクトを使用します。  
 **複数のジョブを削除するには**  
  
 使用して、 `JobCollection` Visual Basic、Visual c#、PowerShell など、選択したプログラミング言語を使用してクラスです。 詳細については、「 [SQL Server 管理オブジェクト (SMO) プログラミング ガイド](http://msdn.microsoft.com/library/ms162169.aspx)」を参照してください。  
  

  
  
