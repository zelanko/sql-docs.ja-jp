---
title: ジョブの有効化または無効化 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1fa9a2700bd2f6a9ce2b074b1633182fc30c9aa7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211416"
---
# <a name="disable-or-enable-a-job"></a>Disable or Enable a Job
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)]エージェント ジョブを無効にする方法について説明します。 ジョブを無効にしても、ジョブは削除されるわけではなく、必要に応じて再び有効にすることができます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **ジョブを無効または有効にする方法:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
 詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> SQL Server Management Studio の使用  
  
#### <a name="to-disable-or-enable-a-job"></a>ジョブを無効または有効にするには  
  
1.  **オブジェクトエクスプローラー**で、の[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]インスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を展開します。  
  
3.  **[ジョブ]** を展開し、無効または有効にするジョブを右クリックします。  
  
4.  ジョブを無効にするには、 **[無効化]** をクリックします。 ジョブを有効にするには、 **[有効化]** をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> Transact-SQL の使用  
  
#### <a name="to-disable-or-enable-a-job"></a>ジョブを無効または有効にするには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 詳細については、「 [sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)」を参照してください。  
  
  
