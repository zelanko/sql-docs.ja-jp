---
title: "[パブリケーションのプロパティ]、[エージェント セキュリティ] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.agentsecurity.f1"
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [パブリケーションのプロパティ]、[エージェント セキュリティ]
  **[パブリケーションのプロパティ]** ダイアログ ボックスの **[エージェント セキュリティ]** ページを使用すると、次のエージェントが実行されるアカウントの設定にアクセスし、レプリケーション トポロジのコンピューターへの接続を作成することができます。  
  
-   すべてのパブリケーションに対応する、スナップショット エージェント。  
  
-   すべてのトランザクション パブリケーションに対応する、ログ リーダー エージェント。 トランザクション レプリケーション用にパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントがあります。 ログ リーダー エージェントの設定を変更すると、データベース内のすべてのトランザクション パブリケーションに影響します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用) ディストリビューション データベースには、それぞれ 1 つのキュー リーダー エージェントがあります。 キュー リーダー エージェントの設定を変更すると、同じディストリビューション データベースを使用するキュー更新サブスクリプションを持つ、すべてのトランザクション パブリケーションに影響します。 キュー リーダー エージェントのセキュリティ設定の詳細については、次を参照してください。 [ビューとレプリケーションのセキュリティ設定の変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)します。  
  
 各エージェントに必要なセキュリティ設定および権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## オプション  
 **セキュリティ設定** または **エージェントを作成します。**  
 エージェント ジョブが作成されている場合はクリックして **セキュリティ設定** エージェントのセキュリティ設定を変更できるようにする] ダイアログ ボックスを表示します。 エージェント ジョブが作成されていない場合、 **[エージェントの作成]** をクリックしてエージェントの作成とセキュリティ設定を指定します。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  