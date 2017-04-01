---
title: "[&lt;AgentName&gt; エージェント セキュリティ] | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.agentnameagentsecurity.f1"
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# [&lt;AgentName&gt; エージェント セキュリティ]
   **\< AgentName> エージェントのセキュリティ** ] ページでは、アカウントを指定できます。 ディストリビューション エージェント (トランザクションまたはスナップショット レプリケーションの場合) またはマージ エージェント (マージ レプリケーション) を実行し、レプリケーション トポロジ内のコンピューターへの接続を作成します。 エージェントおよびレプリケーションのセキュリティのベスト プラクティスによって必要なアクセス許可については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md) と [レプリケーション セキュリティのベスト プラクティス](../../relational-databases/replication/security/replication-security-best-practices.md)します。  
  
## オプション  
 プロパティ] をクリックします。 (**...**) にアクセスするには、各サブスクライバーの行で、 **ディストリビューション エージェント セキュリティ** または **マージ エージェント セキュリティ** ] ダイアログ ボックス。 クリックして **ヘルプ** ダイアログで、エージェントで使用されるアカウントに必要なアクセス許可の詳細については、起動します。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **[サブスクライバーのエージェント]**  
 各サブスクライバーの名前です。  
  
 **[ディストリビューターへの接続]**  
 トランザクション レプリケーションおよびスナップショット レプリケーションに表示されます。 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションの場合、ローカル接続は、ディストリビューターへの接続は常にこのフィールドを表示します。 **Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'** プッシュ サブスクリプションの場合。  
  
-   プル サブスクリプションの場合、接続できることものコンテキストで、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインします。 フィールドには、次のいずれかが表示されます: **[ログイン '\< ログイン>'**, 、**Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してすべての接続が行われることをお勧めします。  
  
 **[パブリッシャーおよびディストリビューターへの接続]**  
 マージ レプリケーションの場合に表示されます。 パブリッシャーおよびディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プッシュ サブスクリプションの場合、ローカル接続はパブリッシャーおよびディストリビューターへの接続をこのフィールドは常に表示されます: **Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'** プッシュ サブスクリプションの場合。  
  
-   プル サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、次のいずれかが表示されます: **[ログイン '\< ログイン>'**, 、**Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してすべての接続が行われることをお勧めします。  
  
 **[サブスクライバーへの接続]**  
 サブスクライバーに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。  
  
-   プル サブスクリプションの場合、ローカル接続は、サブスクライバーへの接続は常にこのフィールドを表示します。 **Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'** プッシュ サブスクリプションの場合。  
  
-   プッシュ サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。 フィールドには、次のいずれかが表示されます: **[ログイン '\< ログイン>'**, 、**Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してすべての接続が行われることをお勧めします。  
  
## 参照  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  