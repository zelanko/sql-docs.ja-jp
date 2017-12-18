---
title: "サブスクリプションの初期化 | Microsoft Docs"
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
f1_keywords: sql13.rep.newsubwizard.initializesubscriptions.f1
ms.assetid: 7b170e4e-470d-4828-a9ed-7435b0b03514
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7207993940a0875513e095f61cb21be74d60ff87
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="initialize-subscriptions"></a>サブスクリプションの初期化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] レプリケートされたデータをサブスクライバーで受信するためには、あらかじめサブスクライバーを初期化する必要があります。 初期データセットは必要ありませんが、少なくともサブスクライバーは、レプリケートされたそれぞれのオブジェクトのスキーマと、レプリケーションに必要なメタデータ テーブルおよびプロシージャを持つ必要があります。  
  
## <a name="options"></a>オプション  
 **[サブスクリプションのプロパティ]**  
 初期データセットを必要とするそれぞれのサブスクライバーの **[初期化]** 列のチェック ボックスをオンにします。 チェック ボックスがオフの場合は、レプリケーション メタデータおよびプロシージャのみが初期化されます。 スナップショットを使用せずにサブスクリプションを初期化する方法については、「[Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」 (スナップショットを使用しないトランザクション サブスクリプションの初期化) を参照してください。  
  
 このウィザードが完了した後にマージ エージェントまたはディストリビューション エージェントによってスナップショット ファイルがサブスクライバーに転送されるようにするには、 **[次の場合に初期化]** 列のドロップダウン リストから **[今すぐ]** を選択します。 エージェントの次回の実行時にファイルが転送されるようにするには、 **[初回同期時]** を選択します。 **[今すぐ]** オプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]へのプル サブスクリプションに対して使用できません。 マージ エージェントおよびディストリビューション エージェントは、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]のインスタンス上で実行されません。したがって、サブスクリプションを別の方法で初期化する必要があります。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントの適切なジョブを開始するために、ウィザードによりディストリビューターへの接続が要求される場合があります。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
