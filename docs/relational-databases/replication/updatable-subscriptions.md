---
title: "[更新可能なサブスクリプション] | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.updatablesubscriptions.f1"
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# [更新可能なサブスクリプション]
  トランザクション レプリケーションでレプリケートされたデータを扱う、読み取り専用です。ただしでレプリケートされたデータを変更することができます、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 更新可能なサブスクリプションを使用してサブスクライバーです。 サブスクライバーでデータを変更する必要がある場合は、要件に応じて次のいずれかのオプションを選択してください。  
  
|更新可能なサブスクリプション タイプ|必要条件|  
|---------------------------------|------------------|  
|即時更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続します。|  
|キュー更新|サブスクライバーのデータを更新するために、パブリッシャーとサブスクライバーを接続する必要はありません。 更新をオフラインで実行し、後からパブリッシャーとサブスクライバーの間で同期させることができます。|  
  
## オプション  
 **[以下のサブスクライバーの変更内容をレプリケートします]**  
 チェック ボックスをオン、 **レプリケート** 変更を加えたりできるようにする、各サブスクライバーの列です。 サブスクライバーだけで、更新できるようにするドロップダウン リスト ボックスの中から適切なオプションを選択する、 **パブリッシャーでコミット** 列。  
  
-   即時更新サブスクリプションに対して **[変更を同時にコミットする]** を選択します。  
  
-   キュー更新サブスクリプションに対して **[変更をキューに登録し、可能な場合はコミット]** を選択します。  
  
## 参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  