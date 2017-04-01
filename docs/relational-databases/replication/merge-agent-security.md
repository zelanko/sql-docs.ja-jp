---
title: "[マージ エージェント セキュリティ] | Microsoft Docs"
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
  - "sql13.rep.security.MA.f1"
helpviewer_keywords: 
  - "[マージ エージェント セキュリティ] ダイアログ ボックス"
ms.assetid: 9b86171a-4381-4b39-869a-cdc161e7cd15
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# [マージ エージェント セキュリティ]
  **[マージ エージェント セキュリティ]** ダイアログ ボックスを使用すると、マージ エージェントの実行に使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントを指定できます。 マージ エージェントは、プッシュ サブスクリプションの場合はディストリビューターで実行され、プル サブスクリプションの場合はサブスクライバーで実行されます。 エージェント プロセスがこのアカウントで実行されるため、Windows アカウントは *プロセス アカウント*とも呼ばれます。 ダイアログ ボックスで使用できる追加オプションは、次に示すアクセスの方法によって異なります。  
  
-   サブスクリプションの新規作成ウィザードからダイアログ ボックスを開いた場合は、マージ エージェントがプッシュ サブスクリプション用にサブスクライバーへの接続を作成するコンテキスト、またはプル サブスクリプション用にパブリッシャーおよびディストリビューターへの接続を作成するコンテキストを指定できます。 Windows アカウントを使用するか、指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントのコンテキストにより、接続を作成できます。  
  
-   ダイアログ ボックスにアクセスすると、 **サブスクリプションのプロパティ** ] ダイアログ ボックスで、マージ エージェントが、[プロパティ] をクリックして接続を作成するコンテキストを指定 (**...**) で、 **サブスクライバー接続** または **パブリッシャー接続** そのダイアログ ボックスの行。 アクセスの詳細については、 **サブスクリプションのプロパティ** ダイアログ ボックスを参照してください [プッシュ サブスクリプション プロパティの変更を表示および](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) とする方法: [ビューとプル サブスクリプションのプロパティの変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)します。  
  
 各アカウントに正しいパスワードが指定され、すべてのアカウントが有効である必要があります。 アカウントとパスワードは、エージェントが実行されるまで検証されません。  
  
## オプション  
 **[プロセス アカウント]**  
 マージ エージェントの実行に使用する Windows アカウントを入力します。  
  
-   プッシュ サブスクリプションでは、アカウントには次のことが必要です。  
  
    -   最低のメンバーである、 **db_owner** ディストリビューション データベースの固定データベース ロール。  
  
    -   PAL のメンバーである。  
  
    -   パブリケーション データベースのユーザーに関連付けられたログインである。  
  
    -   スナップショット共有の読み取り権限を持っている。  
  
-   プル サブスクリプションの場合、アカウントには少なくともメンバーであるは **db_owner** サブスクリプション データベースの固定データベース ロール。  
  
 接続を作成するときにプロセス アカウントを借用する場合、追加の権限が必要です。 **[パブリッシャーおよびディストリビューターに接続]** および **[サブスクライバーに接続]** を参照してください。  
  
 **プロセス アカウント** に対するプル サブスクリプションを指定できません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], のインスタンスで、マージ エージェントが実行されないので、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]です。  
  
 **パスワード** と **パスワードの確認**  
 Windows アカウントのパスワードを入力します。  
  
 **[パブリッシャーおよびディストリビューターに接続]**  
 プッシュ サブスクリプションの場合パブリッシャーおよびディストリビューターへの接続は常にで指定されたアカウントを借用して作成、 **プロセス アカウント** テキスト ボックスです。  
  
 プル サブスクリプションの場合、マージ エージェントでパブリケーションおよびディストリビューターへの接続を作成するには、 **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 使用するのではなく、Windows アカウントの借用を選択することをお勧めする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントです。  
  
 接続に使用する Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントには次のことが必要です。  
  
-   PAL のメンバーである。  
  
-   パブリケーション データベースのユーザーに関連付けられたログインである。  
  
-   ディストリビューション データベースのユーザー (ゲスト ユーザーでも可) に関連付けられたログインである。  
  
-   スナップショット共有の読み取り権限を持っている。  
  
 **[サブスクライバーに接続]**  
 プル サブスクリプションの場合、サブスクライバーへの接続は常にで指定されたアカウントを借用して作成、 **プロセス アカウント** テキスト ボックスです。  
  
 プッシュ サブスクリプションの場合、マージ エージェントでパブリケーションおよびディストリビューターへの接続を作成するには、 **[プロセス アカウント]** テキスト ボックスで指定されたアカウントを借用するか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントを使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用を選択した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとパスワードを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アカウントの使用ではなく、Windows アカウントの借用を選択することをお勧めします。  
  
 Windows アカウントまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーへの接続に使用するアカウントには少なくともメンバーであるは **db_owner** サブスクリプション データベースの固定データベース ロール。  
  
## 参照  
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  