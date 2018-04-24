---
title: イベントの転送先サーバーを指定する方法 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6a204a92259fa97fdb5324353ed3266ed3389567
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のイベントの転送先サーバーを指定する方法について説明します。 イベントの転送の適用対象は、単一のコンピューターでホストされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンス間で転送されるイベントではなく、サーバー間で転送されるイベントであることに注意してください。 また、転送されたイベントを受信するには、警告管理サーバーが SQL Server の既定のインスタンスでなければならないことにも注意してください。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [Security](#Security)  
  
-   **イベントの転送先サーバーを指定する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-designate-an-events-forwarding-server"></a>イベントの転送先サーバーを指定するには  
  
1.  **オブジェクト エクスプ ローラー** で、プラス記号をクリックして、別のサーバーにイベントを転送するサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]**を選択します。  
  
3.  *[SQL Server エージェントのプロパティ - <サーバー名>]* ダイアログ ボックスの **[ページの選択]** で **[詳細設定]** を選択します。  
  
4.  **[SQL Server イベントの転送]**で、 **[イベントを別のサーバーに転送する]** チェック ボックスをオンにします。  
  
5.  **[サーバー]** ボックスの一覧でサーバーを選択し、 **[イベント]**で次のいずれかの操作を行います。  
  
    -   ローカルの警告で処理されていないイベントのみを転送する場合は、 **[未処理のイベント]** をクリックします。  
  
    -   ローカルの警告によって処理されたかどうかにかかわらず、すべてのイベントを転送する場合は、 **[すべてのイベント]** をクリックします。  
  
6.  **[次のレベル以上のイベント発生時]** ボックスの一覧で、選択したサーバーにイベントを転送するときの重大度レベルをクリックします。  
  
7.  完了したら、 **[OK]**をクリックします。  
  
