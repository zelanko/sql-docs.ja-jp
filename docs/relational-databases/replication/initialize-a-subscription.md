---
title: "サブスクリプションの初期化 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb6afeb29ea5a834ae67e9521f690fba748c7c68
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="initialize-a-subscription"></a>サブスクリプションの初期化
  レプリケーション トポロジ内の各サブスクライバーでは、初期化を行って、サブスクライブしているパブリケーション内の各アーティクルのスキーマ、およびストアド プロシージャ、トリガー、メタデータ テーブルなどの必要なレプリケーション オブジェクトをコピーする必要があります。 また、サブスクライバーは一般に初期データセットを受け取ります。 既定の初期化方法では、スキーマ、レプリケーション オブジェクト、データが含まれる完全なスナップショットを使用しますが、完全なスナップショットがなくてもパブリケーションを初期化することが可能です。  
  
 詳細については、「 [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) 」および「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。  
  
  

