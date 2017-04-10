---
title: "レプリケーションの種類 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レプリケーション [SQL Server], 種類"
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# レプリケーションの種類
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次の種類の分散アプリケーションで使用するレプリケーションを提供します。  
  
-   トランザクション レプリケーション。 詳細については、次を参照してください。 [トランザクション レプリケーション](../../relational-databases/replication/transactional/transactional-replication.md)します。  
  
-   マージ レプリケーション。 詳細については、次を参照してください。 [マージ レプリケーション](../../relational-databases/replication/merge/merge-replication.md)します。  
  
-   スナップショット レプリケーション。 詳細については、次を参照してください。 [スナップショット レプリケーション](../../relational-databases/replication/snapshot-replication.md)します。  
  
 アプリケーションで使用するレプリケーションの種類は、物理的なレプリケーション環境、レプリケートするデータの種類と量、データをサブスクライバーで更新するかどうかなどの、さまざまな要因によって異なります。 物理環境には、レプリケーションに関係するコンピューターの数と場所、これらのコンピューターがクライアント (ワークステーション、ラップトップ、またはハンドヘルド デバイス) なのかサーバーなのか、などが含まれます。  
  
 どの種類のレプリケーションも、通常、パブリッシュされたオブジェクトをパブリッシャーとサブスクライバー間で初期同期することから始まります。 この最初の同期とレプリケーションが実行できる、 *スナップショット*, 、すべてのオブジェクトと、パブリケーションで指定されたデータのコピーであります。 作成されたスナップショットはサブスクライバーに配信されます。 アプリケーションによっては、スナップショット レプリケーションのみで十分なこともあります。 スナップショット レプリケーションだけでは不十分なアプリケーションでは、その後行われたデータ変更が、一定期間にわたって増分としてサブスクライバーに渡されることが重要です。 また、アプリケーションによっては、サブスクライバーからパブリッシャーに変更を送り返す必要もあります。 トランザクション レプリケーションおよびマージ レプリケーションには、このような種類のアプリケーション用のオプションがあります。  
  
 スナップショット レプリケーションでは、データの変更は追跡されず、スナップショットが適用されるたびに、既存のデータがすべて上書きされます。 トランザクション レプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクション ログを使用して変更が追跡され、マージ レプリケーションでは、トリガーとメタデータ テーブルを使用して変更が追跡されます。  
  
## 参照  
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  