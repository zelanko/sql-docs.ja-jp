---
title: "SQL Server エージェントのエラー ログに実行トレース メッセージを書き込む | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- writing trace messages
- traces [SQL Server], SQL Server Agent logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: 90e3731e-6fae-43db-833e-9accecdd1c03
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 19c834e42cd6b2a9526b6ab894a33e4ef9aafc95
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="write-execution-trace-messages-to-the-sql-server-agent-error-log-sql-server-management-studio"></a>SQL Server エージェント エラー ログへの実行トレース メッセージの書き込み (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのエラー ログに実行トレース メッセージが書き込まれるようにエージェントを構成する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   SQL Server Management Studio を使用して SQL Server エージェント エラー ログに実行トレース メッセージを書き込むには  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   このオプションを有効にするとエラー ログが大きくなるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] に関する特定の問題を調査する場合にのみ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのエラー ログに実行トレース メッセージを書き込むようにしてください。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>  
#### <a name="to-write-execution-trace-messages-to-the-sql-server-agent-error-log"></a>SQL Server エージェントのエラー ログに実行トレース メッセージを書き込むには  
  
1.  **オブジェクト エクスプローラー**で、プラス記号をクリックして、実行トレース メッセージの書き込み先となる [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのエラー ログを含むサーバーを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]**を選択します。  
  
3.  **[全般]** ページの *[SQL Server エージェントのプロパティ - <サーバー名>]* ダイアログ ボックスの **[エラー ログ]** で **[実行トレース メッセージを含める]** チェック ボックスをオンにします。  
  
4.  **[OK]** をクリックします。  
  
