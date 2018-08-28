---
title: サブスクリプションの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], initializing subscriptions
- transactional replication, initializing subscriptions
- initializing subscriptions [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], about initializing subscriptions
- merge replication [SQL Server replication], initializing subscriptions
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 65badf0b8339157a25b0a757052b423c6b149f99
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43096919"
---
# <a name="initialize-a-subscription"></a>サブスクリプションの初期化
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  レプリケーション トポロジ内の各サブスクライバーでは、初期化を行って、サブスクライブしているパブリケーション内の各アーティクルのスキーマ、およびストアド プロシージャ、トリガー、メタデータ テーブルなどの必要なレプリケーション オブジェクトをコピーする必要があります。 また、サブスクライバーは一般に初期データセットを受け取ります。 既定の初期化方法では、スキーマ、レプリケーション オブジェクト、データが含まれる完全なスナップショットを使用しますが、完全なスナップショットがなくてもパブリケーションを初期化することが可能です。  
  
 詳細については、「 [Initialize a Subscription with a Snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) 」および「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)」を参照してください。  
  
  
