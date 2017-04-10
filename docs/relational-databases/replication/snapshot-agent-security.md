---
title: "[スナップショット エージェントのセキュリティ] | Microsoft Docs"
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
  - "sql13.rep.security.SSA.f1"
helpviewer_keywords: 
  - "[スナップショット エージェントのセキュリティ] ダイアログ ボックス"
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [スナップショット エージェントのセキュリティ]
   **スナップショット エージェントのセキュリティ** ] ダイアログ ボックスでは、指定することができます。  
  
-   ディストリビューターでスナップショット エージェントを実行するときに使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウント。 エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。  
  
-   スナップショット エージェントがへの接続を作成するコンテキスト、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーです。 接続は、Windows アカウントを借用して作成されるか、指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストで作成されます。  
  
    > [!NOTE]  
    >  パブリッシャーとディストリビューターが同じコンピューターに置かれている場合でも、スナップショット エージェントからパブリッシャーへの接続が作成されます。 スナップショット エージェントからディストリビューターへの接続も作成されます。これらの接続は常に、エージェントの実行に使用される Windows アカウントを借用して作成されます。  
  
     Oracle パブリッシャーに対してスナップショット エージェントがパブリッシャーに接続するためのコンテキストの指定、 **パブリッシャーのプロパティ** ] ダイアログ ボックス (から利用可能な **ディストリビューターのプロパティ** ] ダイアログ ボックス)。 詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## オプション  
 **[プロセス アカウント]**  
 ディストリビューターでスナップショット エージェントを実行するときに使用される  Windows アカウントを入力します。 指定する Windows アカウントは、次の条件を満たしている必要があります。  
  
-   最低のメンバーである、 **db_owner** ディストリビューション データベースの固定データベース ロール。  
  
-   スナップショット共有に対する書き込み権限がある。  
  
 **パスワード** と **パスワードの確認入力**  
 Windows アカウントのパスワードを入力します。  
  
 **[パブリッシャーに接続]**  
 スナップショット エージェントはで指定されたアカウントを偽装することによってパブリッシャーに接続を確立する必要があるかどうかを選択して、 **プロセス アカウント** テキスト ボックスまたはを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
 Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接続に使用するアカウントには少なくともメンバーであるは **db_owner** パブリケーション データベースの固定データベース ロール。  
  
## 参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  