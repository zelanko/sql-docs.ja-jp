---
title: SQL Server エージェントの構成 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c0e86dce851972eb31fa639ae36ff24078c8707a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640644"
---
# <a name="configure-sql-server-agent"></a>SQL Server エージェントの構成
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール中に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントのいくつかの構成オプションを指定する方法について説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの構成オプションの完全なセットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO)、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ストアド プロシージャでのみ使用できます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server エージェントを構成するには](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   ジョブ、オペレーター、警告、および **エージェント サービスを管理するには、** のオブジェクト エクスプローラーで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [SQL Server エージェント] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をクリックします。 ただし、オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   フェールオーバー クラスター インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスでは自動再起動を有効にしないでください。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **sysadmin** 固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-configure-sql-server-agent"></a>SQL Server エージェントを構成するには  
  
1.  **[スタート]** をクリックします。 **[スタート]**  メニューの **[コントロール パネル]** をクリックします。  
  
2.  [コントロール パネル] で、 **[システムとセキュリティ]** をクリックします。次に、 **[管理ツール]** をクリックし、 **[ローカル セキュリティ ポリシー]** を選択します。  
  
3.  [ローカル セキュリティ ポリシー] で、シェブロンをクリックして **[ローカル ポリシー]** フォルダーを展開し、 **[ユーザー権利の割り当て]** フォルダーをクリックします。  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での使用のために構成する権限を右クリックし、 **[プロパティ]** を選択します。  
  
5.  権限のプロパティ ダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの実行に使用するアカウントが表示されていることを確認します。 表示されていない場合は、 **[ユーザーまたはグループの追加]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの実行に使用するアカウントを **[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスに入力し、 **[OK]** をクリックします。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行するために追加するそれぞれの権限に対して、この操作を繰り返します。 完了したら、 **[OK]** をクリックします。  
  
