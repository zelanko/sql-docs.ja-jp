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
manager: craigg
ms.openlocfilehash: 30c50d1f6efc44c17eac76e0e03432c2461da296
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63033671"
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行する Windows アカウントとそのネットワーク権限を定義します。 このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 構成マネージャーを使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]エージェント サービス アカウントを設定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェントのサービス開始アカウントを設定するには](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   
  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを操作する場合、サービス開始アカウントが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Administrators グループのメンバーである必要はありません。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービス開始アカウントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sysadmin 固定サーバー ロールのメンバーである必要があります。 マルチサーバー ジョブの処理を使用する場合は、アカウントはマスター サーバーの msdb データベースの TargetServersRole ロールのメンバーでもなければなりません。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 この機能を実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]には、の`sysadmin` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]固定サーバーロールのメンバーであるアカウントの資格情報を使用するようにエージェントを構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
 エージェントサービスアカウントに必要な Windows アクセス許可の詳細については、「 [SQL Server エージェントサービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」および「 [windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>SQL Server エージェントのサービス開始アカウントを設定するには  
  
1.  
  **[登録済みサーバー]** で、プラス記号をクリックして **[データベース エンジン]** を展開します。  
  
2.  プラス記号をクリックして、 **[ローカル サーバー グループ]** フォルダーを展開します。  
  
3.  サービス開始カウントを設定するサーバー インスタンスを右クリックし、**[SQL Server 構成マネージャー]** をクリックします。  
  
4.  
  **[ユーザー アカウント制御]** ダイアログ ボックスで、 **[はい]** をクリックします。  
  
5.  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのコンソール ペインで、 **[SQL Server のサービス]** をクリックします。  
  
6.  詳細ペインで、[ **SQL Server エージェント**_(server_name)_] を右クリックし** ます。ここで、server_name [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、サービス開始アカウントを変更するエージェントインスタンスの名前です。 [**プロパティ**] を選択します。  
  
7.  [ **SQL Server エージェント**_(server_name)_ **のプロパティ**] ダイアログボックスの [**ログオン**] タブで、[次のアカウントで**ログオン**] で次のオプションのいずれかを選択します。  
  
    -   [**ビルトインアカウント**]: ジョブがローカルサーバーのリソースのみを必要とする場合は、このオプションを選択します。 Windows ビルトイン アカウントの選択方法については、「 [SQL Server エージェント サービスのアカウントの選択](https://msdn.microsoft.com/library/ms191543.aspx)」をご覧ください。  
  
        > [!IMPORTANT]  
        >  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、 **では** Local Service [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]アカウントはサポートしません。  
  
    -   [**このアカウント**]: ジョブがネットワーク上のリソース (アプリケーションリソースを含む) を必要とする場合は、このオプションを選択します。他の Windows アプリケーションログにイベントを転送する場合は、または、オペレーターに電子メールまたはポケットベルで通知する場合は、またはです。  
  
         このオプションを選択する場合:  
  
        1.  
  **[アカウント名]** ボックスに、SQL Server エージェントを実行するために使用するアカウントを入力します。 または、 **[参照]** をクリックして **[ユーザーまたはグループの選択]** ダイアログ ボックスを開き、使用するアカウントを選択します。  
  
        2.  
  **[パスワード]** ボックスに、アカウントのパスワードを入力します。 
  **[パスワードの確認入力]** ボックスに、パスワードを再度入力します。  
  
8.  **[OK]** をクリックします。  
  
9. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[閉じる]** ボタンをクリックします。  
  
  
