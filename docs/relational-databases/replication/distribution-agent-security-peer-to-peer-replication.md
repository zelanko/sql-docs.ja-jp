---
title: "[ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs"
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
  - "sql13.rep.p2pwizard.DA.f1"
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# [ディストリビューション エージェント セキュリティ] (ピア ツー ピア レプリケーション)
   **ディストリビューション エージェント セキュリティ** ] ページでは、するディストリビューション エージェントが実行され、ピア ツー ピア トポロジでは、コンピューターへの接続は、アカウントを指定することができます。 エージェントおよびレプリケーションのセキュリティのベスト プラクティスによって必要なアクセス許可については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md) と [レプリケーション セキュリティのベスト プラクティス](../../relational-databases/replication/security/replication-security-best-practices.md)します。  
  
> [!NOTE]  
>  サブスクリプションのディストリビューション エージェントが、このウィザードの以前の実行で既に構成されている場合、使用される資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、使用、 **サブスクリプションのプロパティ** ] ダイアログ ボックス。 詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
## オプション  
 [プロパティ] ボタンをクリックして (**...**) にアクセスするには、各サブスクライバーの行で、 **ディストリビューション エージェント セキュリティ** ] ダイアログ ボックス。 をクリックして **ヘルプ** で、 **ディストリビューション エージェント セキュリティ** ] ダイアログ ボックスのエージェントで使用されるアカウントに必要なアクセス許可の詳細については、起動します。  
  
 ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。  
  
 **[サブスクライバーのエージェント]**  
 各ピアの名前です。  
  
 **[ピア データベース]**  
 パブリケーション データ ベースとサブスクリプション データベースの両方に使用できるピアのデータベースです。  
  
 **[ディストリビューターへの接続]**  
 ディストリビューターに接続するコンテキストを作成します。 ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。 (ローカル接続はディストリビューターへの接続) プッシュ サブスクリプションを作成するため、このフィールドは常に表示: **Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。  
  
 **[サブスクライバーへの接続]**  
 サブスクライバーに接続するコンテキストを作成します。 接続は、エージェントが実行する Windows アカウントのコンテキストの使用、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストによって作成できます。 フィールドには、次のいずれかが表示されます: **[ログイン '\< ログイン>'**, 、**Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してすべての接続が行われることをお勧めします。  
  
## 参照  
 [#40; (&)、ピア ツー ピア トポロジを管理します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  