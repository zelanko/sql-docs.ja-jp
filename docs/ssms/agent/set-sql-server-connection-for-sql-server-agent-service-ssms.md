---
title: SQL Server エージェント サービスの SQL Server 接続の設定 | Microsoft Docs
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
- SQL Server Agent, connections
- connections [SQL Server], SQL Server Agent service
ms.assetid: 28b6178b-0a9e-4f2c-8562-7a62d2d2a285
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7db04539f73e192e83f4577e18900312de47fbb6
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980234"
---
# <a name="set-the-sql-server-connection-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set the SQL Server Connection for the SQL Server Agent Service (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> 
  [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] で [!INCLUDE[ssDE](../../includes/ssde_md.md)] を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] エージェントと [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]間の接続を設定する方法について説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスでは、Windows 認証を使用して、SQL Server のローカル インスタンスに接続できます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **SQL Server エージェントの SQL Server 接続を設定するために使用するもの:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]以降は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証がサポートされません。 このオプションは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を管理している場合にのみ使用できます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-set-the-sql-server-connection"></a>SQL Server の接続を設定するには  
  
1.  **オブジェクト エクスプローラー**で、SQL Server エージェント サービスへの接続を設定するサーバーをプラス記号をクリックして展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。  
  
3.  *[SQL Server エージェントのプロパティ - <サーバー名>]* ダイアログ ボックスの **[ページの選択]** で **[接続]** をクリックします。  
  
4.  **[SQL Server 接続]** で、**[Windows 認証を使用する]** を選択して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続できるようにします。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] 以降のデータベースへの接続には Windows 認証が必要です。  
  
