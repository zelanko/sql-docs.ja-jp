---
title: 'レッスン 3: マージ パブリケーションへのサブスクリプションの同期 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 49008384-2c55-4080-a890-9bceb40e4d6d
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79b8774de74316a4595d7ebd028b9f2e853882bd
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="lesson-3-synchronizing-the-subscription-to-the-merge-publication"></a>レッスン 3:マージ パブリケーションへのサブスクリプションの同期
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このレッスンでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でマージ エージェントを起動して、サブスクリプションを初期化します。 この手順を使用して、パブリッシャーと同期することもできます。 このレッスンを始める前に、前のレッスンの「 [レッスン 2: マージ パブリケーションへのサブスクリプションの作成](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md)」を完了している必要があります。  
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>同期を開始しサブスクリプションを初期化するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続し、サーバー ノードを展開して、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル サブスクリプション]** フォルダーで、 **SalesOrdersReplica** データベースのサブスクリプションを右クリックし、 **[同期の状態の表示]**をクリックします。  
  
3.  **[開始]** をクリックして、サブスクリプションを初期化します。  
  
## <a name="next-steps"></a>Next Steps  
ここでは、マージ エージェントを実行し、同期の開始とサブスクリプションの初期化を行いました。 パブリッシャーまたはサブスクライバー側で、 **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルに対しデータの挿入、変更、削除を行い、ネットワーク接続が使用できるときにこの手順でパブリッシャーとサブスクライバーの間のデータを同期した後、もう一方のサーバーの **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルにクエリを実行すると、レプリケートされた変更を確認することができます。  
  
以上で、モバイル クライアントとの間のデータのレプリケーションに関するチュートリアルは完了です。 トランザクション レプリケーションを使用する類似のチュートリアルとして、「 [Tutorial: Replicating Data Between Continuously Connected Servers](../../relational-databases/replication/tutorial-replicating-data-between-continuously-connected-servers.md)」も参照してください。  
  
## <a name="see-also"></a>参照  
[スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[データベースの同期](../../relational-databases/replication/synchronize-data.md)  
[プル サブスクリプションの同期](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
