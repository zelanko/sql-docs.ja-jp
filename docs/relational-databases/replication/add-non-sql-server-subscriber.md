---
title: "[SQL Server 以外のサブスクライバーの追加] | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.addnonsqlsubscriber.f1"
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# [SQL Server 以外のサブスクライバーの追加]
  レプリケーションでは、Oracle サブスクライバーと IBM DB2 のサブスクライバーのスナップショット パブリケーションおよびトランザクション パブリケーションに対するプッシュ サブスクリプションの作成をサポートします。  
  
## オプション  
 **[追加するサブスクライバーの種類]**  
 Oracle サブスクライバーまたは IBM DB2 サブスクライバーを選択します。 これらのサブスクリプション会員のサポートの詳細については、次を参照してください。 [非 SQL Server サブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。  
  
 **[データ ソース名]**  
 ネットワーク上のデータベースを探すために使用される名前です。 レプリケーションは、ログイン、パスワード、および任意の接続オプションで指定すると組み合わせて、データ ソース名を使用して、データベースの接続文字列を生成、 **ディストリビューション エージェント セキュリティ** このウィザードのページです。  
  
> [!NOTE]  
>  データ ソース名と接続文字列はにより検証されず [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューション エージェントがサブスクリプションを初期化しようとするまでです。  
  
## 参照  
 [Create a Subscription for a Non-SQL Server Subscriber](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  