---
title: "[ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション) | Microsoft Docs"
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
  - "sql13.rep.p2pwizard.LRA.f1"
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# [ログ リーダー エージェントのセキュリティ] (ピア ツー ピア レプリケーション)
   **ログ リーダー エージェントのセキュリティ** ] ページを各ピアでログ リーダー エージェントが実行され、接続は、アカウントを指定することができます。 エージェントおよびレプリケーションのセキュリティのベスト プラクティスによって必要なアクセス許可については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md) と [レプリケーション セキュリティのベスト プラクティス](../../relational-databases/replication/security/replication-security-best-practices.md)します。  
  
> [!NOTE]  
>  トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。 データベースにログ リーダー エージェントが既に設定されている場合 (このウィザードを以前に実行したときのパブリケーション、または同じデータベースにある他のトランザクション パブリケーションで)、使用されている資格情報をこのウィザードで変更することはできません。 新しい資格情報を指定した場合は無視されます。 資格情報を変更するには、使用、 **パブリケーションのプロパティ** ] ダイアログ ボックス。 詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
## オプション  
 [プロパティ] ボタンをクリックして (**...**) にアクセスするには、各ピアの行で、 **ログ リーダー エージェントのセキュリティ** ] ダイアログ ボックス。 をクリックして **ヘルプ** 上、 **ログ リーダー エージェントのセキュリティ** をエージェントで使用されるアカウントに必要なアクセス許可の詳細については起動したダイアログ ボックス。  
  
 このダイアログ ボックスに設定値を入力すると、サブスクライバーへの接続情報がグリッドに表示されます。  
  
 **[パブリッシャーのエージェント]**  
 各ピア サーバー インスタンスの名前です。  
  
 **[ピア データベース]**  
 各ピアでパブリケーション データベースおよびサブスクリプション データベースとして機能するデータベースです。  
  
 **[ディストリビューターへの接続]**  
 ディストリビューターに接続するコンテキストを作成します。 コンテキストを使用して、ローカル ディストリビューターへの接続が常に作成、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、エージェントが実行するため、このフィールドは常に表示されている Windows アカウント **Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。  
  
 **[パブリッシャーへの接続]**  
 パブリッシャーへの接続が作成されるときのコンテキストです。 使用してパブリッシャーに接続を確立できる、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインまたはエージェントを実行する Windows アカウントのコンテキストを使用します。 フィールドには、次のいずれかが表示されます: **[ログイン '\< ログイン>'**, 、**Impersonate '\< ドメイン>\\< ログイン\>'** または **Impersonate '\< コンピューター>\\< ログイン\>'**します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してすべての接続が行われることをお勧めします。  
  
## 参照  
 [#40; (&)、ピア ツー ピア トポロジを管理します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  