---
title: "チュートリアル : 常時接続サーバー間でのデータのレプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "チュートリアル [SQL Server レプリケーション]"
  - "レプリケーション [SQL Server], チュートリアル"
  - "ウィザード [SQL Server レプリケーション]"
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# チュートリアル : 常時接続サーバー間でのデータのレプリケーション
レプリケーションは、常時接続サーバー間でデータを移動する際の問題を解決する有効なソリューションです。 レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。 このチュートリアルでは、常時接続サーバー間にレプリケーション トポロジを設定する方法を学習します。  
  
## 学習する内容  
このチュートリアルでは、トランザクション レプリケーションによって 1 つのデータベースから別のデータベースにデータをパブリッシュする方法を学習します。 最初のレッスンでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使ってパブリケーションを作成する方法を学習し、 後のレッスンでは、サブスクリプションを作成および検証する方法と、待機時間を計測する方法を学習します。  
  
## 必要条件  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 このチュートリアルを学習するには、前のチュートリアル「[レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
このチュートリアルを使用するには、システムに次のコンポーネント必要です。  
  
-   パブリッシャー サーバー側 (レプリケーション元) :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のエディション。ただし、Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) と [!INCLUDE[ssEW](../../includes/ssew-md.md)] は除きます  (これらのエディションはレプリケーションのパブリッシャーとして使用できません)。  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] サンプル データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。  
  
-   サブスクライバー サーバー側 (レプリケーション先) :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のエディション。ただし、[!INCLUDE[ssEW](../../includes/ssew-md.md)] は除きます。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] は、トランザクション レプリケーションのサブスクライバーとして使用できません。  
  
    > [!NOTE]  
    > 既定では、レプリケーションは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] にインストールされません。  
  
> [!NOTE]  
> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、固定サーバー ロール **sysadmin** のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。  
  
**このチュートリアルの推定所要時間: 30 分。**  
  
## このチュートリアルで行うレッスン  
  
-   [レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [レッスン 3 : サブスクリプションの検証と待機時間の計測](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
[チュートリアルを開始する](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
## 参照  
[レプリケーションのプログラミング概念](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  
