---
title: SQL Server エージェントサービスの SQL Server エイリアスを設定します (SQL Server Management Studio)。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- aliases [SQL Server], creating
- SQL Server Agent, aliases
ms.assetid: 02d6295d-ab52-44f0-8f1b-f3910a507d8f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 752796caafa86ece1b471beb25a77ea381497409
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774412"
---
# <a name="set-a-sql-server-alias-for-the-sql-server-agent-service-sql-server-management-studio"></a>Set a SQL Server Alias for the SQL Server Agent Service (SQL Server Management Studio)
  このトピックでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]を使用[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]してに接続するために使用するエージェントの別名を設定する方法について説明します。 既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスは、追加のクライアント構成を必要としない動的サーバー名を使用することによって、名前付きパイプを経由して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。 既定のネットワーク転送を使用しない場合、または、代替の名前付きパイプを使用して受信待ちする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続する場合は、サーバー接続の別名を設定する必要があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   [SQL Server Management Studio を使用して SQL Server エージェント サービスの SQL Server 別名を設定する方法](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のローカル インスタンスを参照する別名を選択しないと、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェントは正常に機能しません。  
  
-   オブジェクト エクスプローラーに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ノードが表示されるのは、このノードの使用権限がある場合に限られます。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントの機能を実行するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]固定サーバー ロールの **sysadmin** のメンバーであるアカウントの資格情報を使用するように構成する必要があります。 このアカウントには、次の Windows 権限が必要です。  
  
-   サービスとしてログオン (SeServiceLogonRight)  
  
-   プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)  
  
-   スキャン チェックを行わない (SeChangeNotifyPrivilege)  
  
-   プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)  
  
 エージェントサービスアカウントに必要な Windows アクセス許可の詳細については、「 [SQL Server エージェントサービスのアカウントの選択](../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)」および「 [windows サービスアカウントとアクセス許可の構成](configure-windows/configure-windows-service-accounts-and-permissions.md)」を参照してください。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-set-a-sql-server-alias-for-the-sql-server-agent-service"></a>SQL Server エージェント サービスの SQL Server 別名を設定する方法  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスに接続して、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  [ **SQL Server エージェントのプロパティ**_server_name_ ] ダイアログボックスの [**ページの選択**] で、[**接続**] を選択します。  
  
4.  **[別名ローカル ホスト サーバー]** ボックスに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントが接続するサーバーの別名を入力します。  
  
5.  **[OK]** をクリックします。  
  
  
