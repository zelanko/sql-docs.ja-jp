---
title: "ジョブ カテゴリ情報の一覧の表示 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f369092eeb9e9ab004d0bd2fb91065af9a9bbfea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="list-job-category-information"></a>ジョブ カテゴリ情報の一覧の表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[tsql](../../includes/tsql_md.md)] または SQL Server 管理オブジェクトを使用してジョブ カテゴリ情報の一覧を表示する方法について説明します。  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **ジョブ カテゴリ情報の一覧を表示する方法:**  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
詳細については、「 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-list-job-category-information"></a>ジョブ カテゴリ情報の一覧を表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
詳細については、「 [sp_help_category (Transact-SQL)](http://msdn.microsoft.com/en-us/8cad1dcc-b43e-43bd-bea0-cb0055c84169)」を参照してください。  
  
## <a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ カテゴリ情報の一覧を表示するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **JobCategory** クラスを使用します。  
  
