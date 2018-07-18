---
title: サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴] (スナップショット サブスクリプション) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.pubtodist.snapshot.f1
ms.assetid: d3575964-f287-4bcf-8d2e-f81a33141b25
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 49686aebd062fc252399f09b1403515d851b3597
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37349643"
---
# <a name="subscription-distributor-to-subscriber-history-snapshot-subscription"></a>サブスクリプション、[ディストリビューターからサブスクライバーまでの履歴]\(スナップショット サブスクリプション)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[ディストリビューターからサブスクライバーまでの履歴]** タブでは、ステータス、履歴、情報メッセージ、およびすべてのエラー メッセージを含む、ディストリビューション エージェントの詳細情報が表示されます。  
  
## <a name="options"></a>および  
 表示するディストリビューション エージェントのセッションを **[表示]** メニューで選択した後、 **[ディストリビューション エージェントのセッション]** というラベルのグリッドで特定のセッションを選択します。 このセッションの詳細情報は、 **[選択されたセッションのアクション]** というラベルのグリッドに表示されます。 選択したセッションがエラーで終了した場合は、 **[選択されたセッションのエラーの詳細またはメッセージ]** というラベルのテキスト領域も表示されます。  
  
 **[表示]**  
 表示するディストリビューション エージェントのセッションを選択します。  
  
 **ステータス**  
 ディストリビューション エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [完了]  
  
-   [再試行中]  
  
-   実行中  
  
 **Start Time**  
 セッションの開始時刻です。  
  
 **[終了時刻]**  
 セッションの終了時刻です。 エージェントが停止していない場合は、このフィールドは空になっています。  
  
 **Duration**  
 このセッションでディストリビューション エージェントが実行された時間の合計です。 エージェントが現在実行中の場合、経過時間を表します。エージェントが終了している場合、セッションの合計時間を表します。  
  
 **エラー メッセージ**  
 セッションがエラーで終了した場合は、ディストリビューション エージェントによって記録された最新のエラー メッセージがこのフィールドに表示されます。 セッションがエラーで終了しなかった場合は、このフィールドは空白です。  
  
 **[動作メッセージ]**  
 選択したセッション中に、ディストリビューション エージェントによってログに記録された、すべての情報メッセージとエラー メッセージです。  
  
 **[動作時間]**  
 **[動作メッセージ]** 列で説明されたアクションが実行された時間です。  
  
 **[選択されたセッションのエラーの詳細またはメッセージ]**  
 選択したセッションの **[状態]** 列に **[エラー]** の値が表示されている場合にのみ表示されます。 このテキスト領域では、エラーの詳細情報とエラーの発生時に試行されたコマンドが表示されます。 エラーに関連する追加コンテンツへのリンクも含まれます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
