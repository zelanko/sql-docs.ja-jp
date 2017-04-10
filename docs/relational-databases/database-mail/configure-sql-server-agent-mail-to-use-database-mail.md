---
title: "データベース メールを使用するように SQL Server エージェント メールを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベース メール [SQL Server], SQL Server エージェント メール"
  - "SQL Server エージェント メール"
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# データベース メールを使用するように SQL Server エージェント メールを構成する
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の通知と警告をデータベース メールを使用して送信するように [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エージェントを構成する方法について説明します。  データベース メール機能を有効にして構成する方法の詳細については、「[データベース メールの構成](../../relational-databases/database-mail/configure-database-mail.md)」を参照してください。  [!INCLUDE[tsql](../../includes/tsql-md.md)] の使用例については、「[データベース メール プロファイルの作成](../../relational-databases/database-mail/create-a-database-mail-profile.md)」をご覧ください。
  
-   **作業を開始する準備:**  
  
-   [前提条件](#Prerequisites)  
  
-   [セキュリティ](#Security)  
  
-   [SQL Server Management Studio でデータベース メールを使用するように SQL Server エージェントを構成するには](#SSMSProcedure)  
  
-   [フォロー アップ タスク](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   [データベース メールを有効にします](../../relational-databases/database-mail/configure-database-mail.md)。  
  
-    使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントの[データベース メール アカウントを作成](../../relational-databases/database-mail/create-a-database-mail-account.md)します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントで使用する[データベース メール プロファイルを作成](../../relational-databases/database-mail/create-a-database-mail-profile.md)し、ユーザーを **msdb** データベースの **DatabaseMailUserRole** に追加します。  
  
-   作成したプロファイルを **msdb** データベースの既定のプロファイルに設定します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 プロファイル アカウントを作成し、ストアド プロシージャを実行するユーザーは、sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **データベース メールを使用するように SQL Server エージェントを構成するには**  
  
-   オブジェクト エクスプローラーで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを展開します。  
  
-   **[SQL Server エージェント]** を右クリックし、**[プロパティ]** をクリックします。  
  
-   **[警告システム]**をクリックします。  
  
-   **[メール プロファイルを有効にする]**チェック ボックスをオンにします。  
  
-   **[メール システム]** ボックスの一覧で、 **[データベース メール]**を選択します。  
  
-   **[メール プロファイル]**ボックスの一覧で、データベース メールのメール プロファイルを選択します。  
  
-   SQL Server エージェントを再起動します。  
  
##  <a name="Follow_Up"></a> フォロー アップ タスク  
 警告および通知を送信できるようにエージェントを構成するには、次のタスクが必要となります。  
  
-   [警告](../../ssms/agent/alerts.md)  
  
     特定のデータベース イベントまたはオペレーティング システムの状態がオペレーターに通知されるように、警告を構成できます。  
  
-   [演算子](../../ssms/agent/operators.md)  
  
     オペレーターとは、電子通知を受け取ることのできる人またはグループの別名です。  
  
  