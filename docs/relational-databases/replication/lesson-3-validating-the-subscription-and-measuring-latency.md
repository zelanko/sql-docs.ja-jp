---
title: "レッスン 3 : サブスクリプションの検証と待機時間の計測 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
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
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02e559d21156340da4527e2915e62efc4205eb19
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>レッスン 3 : サブスクリプションの検証と待機時間の計測
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] このレッスンでは、トレーサー トークンを使用して、変更がサブスクライバーにレプリケートされているかどうかを検証し、待機時間を計測します。待機時間とは、パブリッシャーで加えられた変更がサブスクライバーに反映されるまでの所用時間です。 このレッスンを始める前に、前のレッスンの [「レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成」](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-transactional-publication.md)を完了している必要があります。  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>トレーサー トークンを挿入してトークンの情報を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、 **[レプリケーション モニターの起動]**をクリックします。  
  
    レプリケーション モニターが起動します。  
  
2.  左ペインでパブリッシャー グループを展開し、パブリッシャー インスタンスを展開して、 **[AdvWorksProductTrans]** パブリケーションをクリックします。  
  
3.  **[トレーサー トークン]** タブをクリックします。  
  
4.  **[トレーサーの挿入]**をクリックします。  
  
5.  **[パブリッシャーからディストリビューターまで]**列、 **[ディストリビューターからサブスクライバーまで]**列、および **[合計待機時間]**列で、トレーサー トークンの経過時間を表示します。 **[保留中]** と表示された場合は、トークンが特定のポイントに到達していないことを示します。  
  
## <a name="next-steps"></a>Next Steps  
このレッスンでは、トレーサー トークンを使用して、データの変更がパブリッシャーからスクライバへレプリケートされているかどうかを検証しました。 パブリッシャー側の **Product** テーブルに対してデータの挿入、更新、または削除を行い、レプリケーション後、サブスクライバー側の **Product** テーブルをクエリすることもできます。  
  
チュートリアル「常時接続サーバー間でのデータのレプリケーション」はこれで完了です。 マージ レプリケーションを使用する類似のチュートリアルについては、 [「チュートリアル: モバイル クライアントとの間のデータのレプリケーション」](../../relational-databases/replication/tutorial-replicating-data-with-mobile-clients.md)を参照してください。  
  
## <a name="see-also"></a>参照  
[Measure Latency and Validate Connections for Transactional Replication](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
  
