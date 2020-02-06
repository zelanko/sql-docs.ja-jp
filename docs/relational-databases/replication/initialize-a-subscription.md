---
title: サブスクリプションの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 742b29d53d917308b97d5b6935ed6aa0c0cba462
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287959"
---
# <a name="initialize-a-subscription"></a>サブスクリプションの初期化
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  レプリケーション トポロジ内の各サブスクライバーでは、初期化を行って、サブスクライブしているパブリケーション内の各アーティクルのスキーマ、およびストアド プロシージャ、トリガー、メタデータ テーブルなどの必要なレプリケーション オブジェクトをコピーする必要があります。 また、サブスクライバーは一般に初期データセットを受け取ります。 既定の初期化方法では、スキーマ、レプリケーション オブジェクト、データが含まれる完全なスナップショットを使用しますが、完全なスナップショットがなくてもパブリケーションを初期化することが可能です。  
  
 詳細については、「 [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) 」および「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。  
  
  
