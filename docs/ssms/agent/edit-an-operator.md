---
title: オペレーターの編集 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8fc3f6df5fc05f4adca7071397e70455548ed79d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="edit-an-operator"></a>Edit an Operator
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] または [!INCLUDE[tsql](../../includes/tsql_md.md)]を使用して、通知の受信や通知用の電子メール アドレス、ポケットベル アドレス、Net SEND アドレスなど、オペレーターの可用性を編集する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **オペレーターを編集する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   今後のバージョンの **では、** エージェントからポケットベル オプションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] net send [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オプションが削除される予定です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。  
  
-   SQL Server エージェントは、データベース メールを使用して、電子メールおよびポケットベルによる通知をオペレーターへ送信するように構成する必要があります。 詳細については、「 [オペレーターへの警告の割り当て](http://msdn.microsoft.com/library/ms190038.aspx)」を参照してください。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
オペレーターを編集できるのは、 **sysadmin** 固定サーバー ロールのメンバーだけです。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-edit-an-operator"></a>オペレーターを編集するには  
  
1.  **オブジェクト エクスプローラー**で、編集するオペレーターを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  プラス記号をクリックして **[オペレーター]** フォルダーを展開します。  
  
4.  編集するオペレーターを右クリックし、 **[プロパティ]** をクリックします。  
  
    *[<オペレーター名> のプロパティ]* ダイアログ ボックスに表示される使用可能なオプションの詳細については、以下を参照してください。  
  
    -   [オペレーターのプロパティ - [新しいオペレーター] ([全般] ページ)](../../ssms/agent/operator-properties-new-operator-general-page.md)  
  
    -   [オペレーターのプロパティ - [新しいオペレーター] ([通知] ページ)](../../ssms/agent/operator-properties-new-operator-notifications-page.md)  
  
    -   [[オペレーターのプロパティ] ([履歴] ページ)](../../ssms/agent/operator-properties-history-page.md)  
  
5.  完了したら、 **[OK]** をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-edit-an-operator"></a>オペレーターを編集するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.)
    --  when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'François Ajenstat',  
        @enabled = 1,  
        @email_address = N'françoisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
詳細については、「 [sp_update_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/231750a6-4828-4d03-afe6-b91d38c42ed3)」を参照してください。  
  
