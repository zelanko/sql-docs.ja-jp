---
title: ジョブ カテゴリ情報の一覧の表示
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 82ef47eed4a27b1a9f3bac3564f566e44a8143b6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733002"
---
# <a name="list-job-category-information"></a>ジョブ カテゴリ情報の一覧の表示
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../includes/tsql-md.md)] または SQL Server 管理オブジェクトを使用してジョブ カテゴリ情報の一覧を表示する方法について説明します。  
  
-   **作業を開始する準備:**  
  
    [セキュリティ](#Security)  
  
-   **ジョブ カテゴリ情報の一覧を表示する方法:**  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理オブジェクト](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>はじめに  
  
### <a name="security"></a><a name="Security"></a>セキュリティ  
詳細については、「 [SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Transact-SQL の使用  
  
#### <a name="to-list-job-category-information"></a>ジョブ カテゴリ情報の一覧を表示するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
詳細については、「 [sp_help_category (Transact-SQL)](https://msdn.microsoft.com/8cad1dcc-b43e-43bd-bea0-cb0055c84169)」を参照してください。  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>SQL Server 管理オブジェクトの使用  
**ジョブ カテゴリ情報の一覧を表示するには**  
  
Visual Basic、Visual C#、PowerShell などのプログラミング言語で **JobCategory** クラスを使用します。  
  
