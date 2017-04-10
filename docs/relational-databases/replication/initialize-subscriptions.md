---
title: "サブスクリプションの初期化 | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.initializesubscriptions.f1"
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# サブスクリプションの初期化
  レプリケートされたデータをサブスクライバーで受信するためには、あらかじめサブスクライバーを初期化する必要があります。 初期データセットは必要ありませんが、少なくともサブスクライバーは、レプリケートされたそれぞれのオブジェクトのスキーマと、レプリケーションに必要なメタデータ テーブルおよびプロシージャを持つ必要があります。  
  
## オプション  
 **[サブスクリプションのプロパティ]**  
 チェック ボックスをオン、 **初期化** 、初期のデータ セットを必要とすると、各サブスクライバーの列です。 チェック ボックスがオフの場合は、レプリケーション メタデータおよびプロシージャのみが初期化されます。 スナップショットを使用しないサブスクリプションの初期化の詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
 選択 **すぐに** でドロップダウン リスト ボックスから、 **場合に初期化** このウィザードを完了した後にスナップショットをサブスクライバーにファイルをマージ エージェントまたはディストリビューション エージェント転送列です。 エージェントの次回の実行時にファイルが転送されるようにするには、 **[初回同期時]** を選択します。  **[今すぐ]** オプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]へのプル サブスクリプションに対して使用できません。 マージ エージェントおよびディストリビューション エージェントは、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のインスタンス上で実行されません。したがって、サブスクリプションを別の方法で初期化する必要があります。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。  
  
## 参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  