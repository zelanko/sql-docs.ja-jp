---
title: "[ログ リーダー エージェントのセキュリティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.security.LRA.f1"
helpviewer_keywords: 
  - "[ログ リーダー エージェントのセキュリティ] ダイアログ ボックス"
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# [ログ リーダー エージェントのセキュリティ]
   **ログ リーダー エージェントのセキュリティ** ] ダイアログ ボックスでは、指定することができます。  
  
-   ログ リーダー エージェントをディストリビューターで実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント。 エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。  
  
-   ログ リーダー エージェントがへの接続を作成するコンテキスト、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーです。 接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。  
  
    > [!NOTE]  
    >  パブリッシャーおよびディストリビューターが同じコンピューター上にある場合でも、ログ リーダー エージェントはパブリッシャーへの接続を作成します。 ログ リーダー エージェントはディストリビューターへの接続も作成します。これらの接続は必ず、エージェントが実行される Windows アカウントを借用して作成されます。  
  
     Oracle パブリッシャーに対してログ リーダー エージェントがパブリッシャーに接続するためのコンテキストの指定、 **パブリッシャーのプロパティ** ] ダイアログ ボックス (から利用可能な **ディストリビューターのプロパティ** ] ダイアログ ボックス)。 詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## オプション  
 **[プロセス アカウント]**  
 ログ リーダー エージェントをディストリビューターで実行する Windows アカウントを入力します。 最小値にする必要があります。 を指定する Windows アカウントのメンバーである、 **db_owner** ディストリビューション データベースの固定データベース ロール。  
  
 **パスワード** と **パスワードの確認入力**  
 Windows アカウントのパスワードを入力します。  
  
 **[パブリッシャーに接続]**  
 ログ リーダー エージェントは、パブリッシャーに接続で指定されたアカウントを偽装することによって作成するかどうかを選択して、 **プロセス アカウント** テキスト ボックスまたはを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 使用するのではなく、Windows アカウントの借用を選択することをお勧めする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。  
  
 Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続に使用するアカウントには少なくともメンバーであるは **db_owner** パブリケーション データベースの固定データベース ロール。  
  
## 参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  