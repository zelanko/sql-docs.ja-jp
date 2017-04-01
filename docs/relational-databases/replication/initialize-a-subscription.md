---
title: "サブスクリプションの初期化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット レプリケーション [SQL Server], サブスクリプションの初期化"
  - "トランザクション レプリケーション, サブスクリプションの初期化"
  - "サブスクリプションの初期化 [SQL Server レプリケーション]"
  - "サブスクリプション [SQL Server レプリケーション], 初期化"
  - "サブスクリプションの初期化 [SQL Server レプリケーション], サブスクリプションの初期化について"
  - "マージ レプリケーション [SQL Server レプリケーション], サブスクリプションの初期化"
ms.assetid: d6013845-cb7a-4203-8e21-edce32f1d330
caps.latest.revision: 32
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 32
---
# サブスクリプションの初期化
  レプリケーション トポロジ内の各サブスクライバーでは、初期化を行って、サブスクライブしているパブリケーション内の各アーティクルのスキーマ、およびストアド プロシージャ、トリガー、メタデータ テーブルなどの必要なレプリケーション オブジェクトをコピーする必要があります。 また、サブスクライバーは一般に初期データセットを受け取ります。 既定の初期化方法では、スキーマ、レプリケーション オブジェクト、データが含まれる完全なスナップショットを使用しますが、完全なスナップショットがなくてもパブリケーションを初期化することが可能です。  
  
 詳細については、次を参照してください。 [スナップショットを使用してサブスクリプションを初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md) と [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
  