---
title: "SQL Server エージェントの構成 | Microsoft Docs"
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
- SQL Server Agent, configuring
- accounts [SQL Server], SQL Server Agent
- SQL Server Agent, permissions
- security [SQL Server], SQL Server Agent
ms.assetid: 2e361a62-9e92-4fcd-80d7-d6960f127900
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e433dd732e153213da84aa9a1444f9255cc5a4d5
ms.lasthandoff: 04/11/2017

---
# <a name="configure-sql-server-agent"></a>SQL Server エージェントの構成
このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインストール中に [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]エージェントのいくつかの構成オプションを指定する方法について説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの構成オプションの完全なセットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 管理オブジェクト (SMO)、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ストアド プロシージャでのみ使用できます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   [SQL Server エージェントを構成するには](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   ジョブ、オペレーター、警告、および **エージェント サービスを管理するには、** のオブジェクト エクスプローラーで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [SQL Server エージェント] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] をクリックします。 ただし、オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
-   フェールオーバー クラスター インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] サービスまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスでは自動再起動を有効にしないでください。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの機能を実行するには、 **の** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]固定サーバー ロールのメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントに必要な Windows 権限の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 」および「 [Windows サービス アカウントと権限の構成](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)」を参照してください。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-configure-sql-server-agent"></a>SQL Server エージェントを構成するには  
  
1.  **[スタート]** をクリックします。 **[スタート]**  メニューの **[コントロール パネル]**をクリックします。  
  
2.  [コントロール パネル] で、 **[システムとセキュリティ]**をクリックします。次に、 **[管理ツール]**をクリックし、 **[ローカル セキュリティ ポリシー]**を選択します。  
  
3.  [ローカル セキュリティ ポリシー] で、シェブロンをクリックして **[ローカル ポリシー]** フォルダーを展開し、 **[ユーザー権利の割り当て]** フォルダーをクリックします。  
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] での使用のために構成する権限を右クリックし、 **[プロパティ]**を選択します。  
  
5.  権限のプロパティ ダイアログ ボックスで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの実行に使用するアカウントが表示されていることを確認します。 表示されていない場合は、 **[ユーザーまたはグループの追加]**をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの実行に使用するアカウントを **[ユーザー、コンピューター、サービス アカウント、またはグループの選択]** ダイアログ ボックスに入力し、 **[OK]**をクリックします。  
  
6.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントで実行するために追加するそれぞれの権限に対して、この操作を繰り返します。 完了したら、 **[OK]**をクリックします。  
  

