---
title: ログ配布構成からのセカンダリ データベースの削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- deleting secondary databases
- secondary databases [SQL Server], in log shipping
- removing secondary databases
- secondary data files [SQL Server], removing
- log shipping [SQL Server], secondary databases
ms.assetid: ebe368a4-ca1c-45d0-9a71-3ddbd5b26a8e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0849d4e10df746dd98e271bb3eb35696cb20337b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774826"
---
# <a name="remove-a-secondary-database-from-a-log-shipping-configuration-sql-server"></a>ログ配布構成からのセカンダリ データベースの削除 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ログ配布セカンダリ データベースを削除する方法を説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してログ配布セカンダリデータベースを削除するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Related Tasks](#RelatedTasks)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 ログ配布ストアド プロシージャには、 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-remove-a-log-shipping-secondary-database"></a>ログ配布セカンダリ データベースを削除するには  
  
1.  現在のログ配布プライマリ サーバーである [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  
  **[データベース]** を展開し、ログ配布プライマリ データベースを右クリックして **[プロパティ]** をクリックします。  
  
3.  
  **[ページの選択]** の **[トランザクション ログの配布]** をクリックします。  
  
4.  
  **[セカンダリ サーバー インスタンスとデータベース]** で、削除するデータベースをクリックします。  
  
5.  **[削除]** をクリックします。  
  
6.  
  **[OK]** をクリックすると構成が更新されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-remove-a-secondary-database"></a>セカンダリ データベースを削除するには  
  
1.  プライマリ サーバーで [sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql) を実行して、セカンダリ データベースに関する情報をプライマリ サーバーから削除します。  
  
2.  セカンダリ サーバーで [sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql) を実行して、セカンダリ データベースを削除します。  
  
    > [!NOTE]  
    >  同じセカンダリ ID を持つセカンダリ データベースが他にない場合は、 **sp_delete_log_shipping_secondary_primary** が **sp_delete_log_shipping_secondary_database** により呼び出され、セカンダリ ID のエントリ、およびコピー ジョブと復元ジョブが削除されます。  
  
3.  セカンダリ サーバーでコピー ジョブと復元ジョブを無効にします。 詳細については、「 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)」をご覧ください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [ログ配布を SQL Server 2014 &#40;Transact-sql&#41;にアップグレードする](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [ログ配布 &#40;SQL Server&#41;を構成する](configure-log-shipping-sql-server.md)  
  
-   [ログ配布構成 &#40;SQL Server にセカンダリデータベースを追加&#41;](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [ログ配布 &#40;SQL Server の削除&#41;](remove-log-shipping-sql-server.md)  
  
-   [ログ配布レポート &#40;SQL Server Management Studio を表示&#41;](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [Transact-sql&#41;&#40;ログ配布の監視](monitor-log-shipping-transact-sql.md)  
  
-   [ログ配布のセカンダリ &#40;SQL Server にフェールオーバーする&#41;](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](about-log-shipping-sql-server.md)   
 [Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md)  
  
  
