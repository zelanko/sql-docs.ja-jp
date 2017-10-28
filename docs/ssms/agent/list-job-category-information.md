---
title: "ジョブ カテゴリ情報の一覧の表示 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6707983f3fe707a5253ff6722adb190579bd1d48
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="list-job-category-information"></a>ジョブ カテゴリ情報の一覧の表示
このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[tsql](../../includes/tsql_md.md)] または SQL Server 管理オブジェクトを使用してジョブ カテゴリ情報の一覧を表示する方法について説明します。  
  
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
  

