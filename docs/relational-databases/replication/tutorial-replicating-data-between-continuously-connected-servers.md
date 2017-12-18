---
title: "チュートリアル: 常時接続サーバー間でのデータのレプリケーション | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 256985a9c23bca91449dc5880e184d80a0e73d45
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>チュートリアル : 常時接続サーバー間でのデータのレプリケーション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] レプリケーションは、常時接続サーバー間でデータを移動する際の問題を解決する有効なソリューションです。 レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。 このチュートリアルでは、常時接続サーバー間にレプリケーション トポロジを設定する方法を学習します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、トランザクション レプリケーションによって 1 つのデータベースから別のデータベースにデータをパブリッシュする方法を学習します。 最初のレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使ってパブリケーションを作成する方法を学習し、 後のレッスンでは、サブスクリプションを作成および検証する方法と、待機時間を計測する方法を学習します。  
  
## <a name="requirements"></a>必要条件  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 このチュートリアルを学習するには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
このチュートリアルを使用するには、システムに次のコンポーネント必要です。  
  
-   パブリッシャー サーバー側 (レプリケーション元) :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のエディション。ただし、Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) と [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます (これらのエディションはレプリケーションのパブリッシャーとして使用できません)。  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] サンプル データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。  
  
-   サブスクライバー サーバー側 (レプリケーション先) :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のエディション。ただし、 [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] は、トランザクション レプリケーションのサブスクライバーとして使用できません。  
  
    > [!NOTE]  
    > 既定では、レプリケーションは [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] にインストールされません。  
  
> [!NOTE]  
> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、固定サーバー ロール **sysadmin** のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。  
  
**このチュートリアルの推定所要時間: 30 分。**  
  
## <a name="lessons-in-this-tutorial"></a>このチュートリアルで行うレッスン  
  
-   [レッスン 1 : トランザクション レプリケーションを使用したデータのパブリッシュ](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [レッスン 2 : トランザクション パブリケーションへのサブスクリプションの作成](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [レッスン 3 : サブスクリプションの検証と待機時間の計測](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
[チュートリアルを開始する](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md)  
  
## <a name="see-also"></a>参照  
[レプリケーションのプログラミング概念](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  
