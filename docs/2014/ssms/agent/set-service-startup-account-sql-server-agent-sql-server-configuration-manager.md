---
title: SQL Server エージェントのサービス開始アカウントを設定する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
author: stevestein
ms.author: sstein
ms.openlocfilehash: b822da364fef2831f0f183089ce1cc330ca3118e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067578"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行する Windows アカウントとそのネットワーク権限を定義します。 このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 構成マネージャーを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェント サービス アカウントを設定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントのサービス開始アカウントを設定するには](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを操作する場合、サービス開始アカウントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators グループのメンバーである必要はありません。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定サーバー ロールのメンバーである必要があります。 マルチサーバー ジョブの処理を使用する場合は、アカウントはマスター サーバーの msdb データベースの TargetServersRole ロールのメンバーでもなければなりません。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 この機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の固定サーバーロールのメンバーであるアカウントの資格情報を使用するようにエージェントを構成する必要があり `sysadmin` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
 エージェントサービスアカウントに必要な Windows アクセス許可の詳細については [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>SQL Server エージェントのサービス開始アカウントを設定するには  
  
1.  **[登録済みサーバー]** で、プラス記号をクリックして **[データベース エンジン]** を展開します。  
  
2.  プラス記号をクリックして、 **[ローカル サーバー グループ]** フォルダーを展開します。  
  
3.  サービス開始カウントを設定するサーバー インスタンスを右クリックし、**[SQL Server 構成マネージャー]** をクリックします。  
  
4.  **[ユーザー アカウント制御]** ダイアログ ボックスで、 **[はい]** をクリックします。  
  
5.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのコンソール ペインで、 **[SQL Server のサービス]** をクリックします。  
  
6.  詳細ペインで、サービス開始アカウントを変更する **(server_name)**_]_( *server_name* は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント インスタンスの名前) を右クリックし、 **[プロパティ]** をクリックします。  
  
7.  [ **SQL Server エージェント**_(server_name)_ **のプロパティ**] ダイアログボックスの [**ログオン**] タブで、[次のアカウントで**ログオン**] で次のオプションのいずれかを選択します。  
  
    -   **[ビルトイン アカウント]**: ジョブがローカル サーバーのリソースだけを必要とする場合はこのオプションを選択します。 Windows ビルトイン アカウントの選択方法については、「 [SQL Server エージェント サービスのアカウントの選択](https://msdn.microsoft.com/library/ms191543.aspx)」をご覧ください。  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、 **では** Local Service [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]アカウントはサポートしません。  
  
    -   **[このアカウント]**: ジョブがネットワーク経由のリソース (アプリケーション リソースを含む) を必要とする場合、他の Windows アプリケーション ログにイベントを転送する場合、またはメールやポケットベルを使用してオペレーターに通知する場合は、このオプションを選択します。  
  
         このオプションを選択する場合:  
  
        1.  **[アカウント名]** ボックスに、SQL Server エージェントを実行するために使用するアカウントを入力します。 または、 **[参照]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開き、使用するアカウントを選択します。  
  
        2.  **[パスワード]** ボックスに、アカウントのパスワードを入力します。 **[パスワードの確認入力]** ボックスに、パスワードを再度入力します。  
  
8.  **[OK]** をクリックします。  
  
9. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[閉じる]** ボタンをクリックします。  
  
  
