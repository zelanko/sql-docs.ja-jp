---
title: "SQL Server エージェントのエラー ログの名前の変更 (SQL Server Management Studio) | Microsoft Docs"
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
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- renaming SQL Server Agent error log
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: dee2b199-48af-44cb-9177-d029a5edb169
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83b8bbd9c08ac115c093a0c06b5dc2df6cd5bb57
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="rename-a-sql-server-agent-error-log-sql-server-management-studio"></a>Rename a SQL Server Agent Error Log (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラーが書き込まれるファイルの名前を変更する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントのエラー ログの名前を変更する方法](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを再開しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントから新しいログ ファイルに書き込まれません。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-rename-a-sql-server-agent-error-log"></a>SQL Server エージェント エラー ログの名前を変更するには  
  
1.  **オブジェクト エクスプローラー**で、名前を変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント エラー ログを含むサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]**を展開します。  
  
3.  **[エラー ログ]** フォルダーを右クリックし、 **[構成]**をクリックします。  
  
4.  **[SQL Server エージェント エラー ログの構成]** ダイアログ ボックスの **[エラー ログ ファイル]** ボックスに、エラー ログの新しいファイル パスとファイル名を入力します。 または、省略記号ボタン ( **[...]** ) をクリックして **[エージェント エラー ログの場所の指定]** ダイアログ ボックスを開きます。  
  
5.  完了したら、 **[OK]**をクリックします。  
  
