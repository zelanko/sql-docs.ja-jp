---
title: "[エージェント セキュリティ] (パブリケーションの新規作成ウィザード) | Microsoft Docs"
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
  - "sql13.rep.agentsecurity.articles.f1"
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# [エージェント セキュリティ] (パブリケーションの新規作成ウィザード)
   **エージェントのセキュリティ** ] ページで、エージェントの実行や、レプリケーション トポロジ内のコンピューターへの接続を作成するアカウントを指定できます。  
  
-   すべてのパブリケーションに対応する、スナップショット エージェント。  
  
-   すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。  
  
-   更新可能なサブスクリプションを許容するトランザクション パブリケーションに対応する、キュー リーダー エージェント。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を指定した場合、このエージェントのエージェント ジョブが作成された **更新可能なサブスクリプションを含むトランザクション パブリケーション** 上、 **パブリケーションの種類** ] ページで、使用する更新可能なサブスクリプションの種類に関係なく。 更新可能なサブスクリプションの詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
 エージェントおよびレプリケーションのセキュリティのベスト プラクティスに必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md) と [レプリケーション セキュリティのベスト プラクティス](../../relational-databases/replication/security/replication-security-best-practices.md)します。  
  
## オプション  
 **スナップショット エージェント**  
 すべてのパブリケーションで表示されます。 クリックして **セキュリティ設定** でセキュリティ設定を指定する、 **スナップショット エージェントのセキュリティ** ] ダイアログ ボックス。  
  
 クリックして **ヘルプ** で、 **スナップショット エージェントのセキュリティ** 詳細については、スナップショット エージェントによって使用されるアカウントに必要なアクセス許可] ダイアログ ボックス。  
  
 **ログ リーダー エージェント (Log Reader Agent)**  
 すべてのトランザクション パブリケーションで表示されます。 クリックして **セキュリティ設定** でセキュリティ設定を指定する、 **ログ リーダー エージェントのセキュリティ** ] ダイアログ ボックス。  
  
 をクリックして **ヘルプ** 上、 **ログ リーダー エージェントのセキュリティ** 、ログ リーダー エージェントで使用されるアカウントに必要なアクセス許可についての詳細] ダイアログ ボックス。  
  
> [!NOTE]  
>  トランザクション レプリケーションを使用してパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントが存在します。 データベースにトランザクション パブリケーションが既に存在している場合、セキュリティ設定は読み取り専用になります。 設定を変更することができます、 **パブリケーションのプロパティ** ] ダイアログ ボックスで、変更、データベース内のすべてのトランザクション パブリケーションに影響します。  
  
 **キュー リーダー エージェント (Queue Reader Agent)**  
 更新可能なサブスクリプションを許容するトランザクション パブリケーションで表示されます。 クリックして **セキュリティ設定** でセキュリティ設定を指定する、 **キュー リーダー エージェントのセキュリティ** ] ダイアログ ボックス。 このウィザードが完了すると、キュー更新サブスクリプションを作成するかどうかには関係なく、キュー リーダー エージェント ジョブが作成されます。 キュー更新サブスクリプションを作成しない場合には、このジョブを無効にできます。 ジョブを右クリックして (名前の形式: *[\< パブリッシャー>] です。 \< 整数>*。) で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント **ジョブ** フォルダー、およびクリック **を無効にする**です。  
  
 をクリックして **ヘルプ** 上、 **キュー リーダー エージェントのセキュリティ** キュー リーダー エージェントによって使用されるアカウントに必要なアクセス許可についての詳細] ダイアログ ボックス。  
  
> [!NOTE]  
>  ディストリビューション データベース (および、それを使用するすべてのパブリッシャー) には、それぞれに対応するキュー リーダー エージェントが 1 つずつ存在します。 指定されたディストリビューション データベースを使用するパブリッシャーのいずれかに、キュー更新サブスクリプションを許容するトランザクション パブリケーションが既に存在する場合、セキュリティ設定は読み取り専用になります。 されるキュー リーダー エージェントが実行され、接続にアカウントを変更することができます、 **ディストリビューターのプロパティ** ] ダイアログ ボックスで、変更がディストリビューション データベースを使用するすべてのパブリッシャーのパブリケーションに影響します。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [トランザクション パブリケーションの更新可能なサブスクリプションの作成](https://msdn.microsoft.com/library/mt740635.aspx)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [レプリケーションのログインとパスワードを管理します。](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  