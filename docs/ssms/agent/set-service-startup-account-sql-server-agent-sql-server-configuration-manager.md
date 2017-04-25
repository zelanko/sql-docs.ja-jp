---
title: "SQL Server エージェントのサービス開始アカウントの設定 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ca20cf42839419f5d40826ef992087623dbc3059
ms.lasthandoff: 04/11/2017

---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>SQL Server エージェントのサービス開始アカウントの設定 (SQL Server 構成マネージャー)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのサービス開始アカウントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを実行する Windows アカウントとそのネットワーク権限を定義します。 このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 構成マネージャーを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]エージェント サービス アカウントを設定する方法について説明します。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントのサービス開始アカウントを設定するには](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]以降で [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを操作する場合、サービス開始アカウントが [!INCLUDE[msCoName](../../includes/msconame_md.md)] Administrators グループのメンバーである必要はありません。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのサービス開始アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]sysadmin 固定サーバー ロールのメンバーである必要があります。 マルチサーバー ジョブの処理を使用する場合は、アカウントはマスター サーバーの msdb データベースの TargetServersRole ロールのメンバーでもなければなりません。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>SQL Server エージェントのサービス開始アカウントを設定するには  
  
1.  **[登録済みサーバー]**で、プラス記号をクリックして **[データベース エンジン]**を展開します。  
  
2.  プラス記号をクリックして、 **[ローカル サーバー グループ]** フォルダーを展開します。  
  
3.  サービス開始カウントを設定するサーバー インスタンスを右クリックし、 **[SQL Server 構成マネージャー]**をクリックします。  
  
4.  **[ユーザー アカウント制御]** ダイアログ ボックスで、 **[はい]**をクリックします。  
  
5.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 構成マネージャーのコンソール ペインで、 **[SQL Server のサービス]**をクリックします。  
  
6.  詳細ペインで、サービス開始アカウントを変更する **[SQL Server エージェント *(server_name)*]** (*server_name* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント インスタンスの名前) を右クリックし、**[プロパティ]** をクリックします。  
  
7.  **[SQL Server エージェント***(server_name)***のプロパティ]** ダイアログ ボックスの **[ログオン]** タブで、**[次のアカウントでログオン]** から以下のいずれかのオプションを選択します。  
  
    -   **[ビルトイン アカウント]**: ジョブがローカル サーバーのリソースだけを必要とする場合はこのオプションを選択します。 Windows ビルトイン アカウントの選択方法については、「 [SQL Server エージェント サービスのアカウントの選択](http://msdn.microsoft.com/library/ms191543.aspx)」をご覧ください。  
  
        > [!IMPORTANT]  
        > [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスは、 **では** Local Service [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]アカウントはサポートしません。  
  
    -   **[このアカウント]**: ジョブがネットワーク経由のリソース (アプリケーション リソースを含む) を必要とする場合、他の Windows アプリケーション ログにイベントを転送する場合、またはメールやポケットベルを使用してオペレーターに通知する場合は、このオプションを選択します。  
  
        このオプションを選択する場合:  
  
        1.  **[アカウント名]** ボックスに、SQL Server エージェントを実行するために使用するアカウントを入力します。 または、 **[参照]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開き、使用するアカウントを選択します。  
  
        2.  **[パスワード]** ボックスに、アカウントのパスワードを入力します。 **[パスワードの確認入力]** ボックスに、パスワードを再度入力します。  
  
8.  **[OK]**をクリックします。  
  
9. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 構成マネージャーで、 **[閉じる]** ボタンをクリックします。  
  

