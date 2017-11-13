---
title: "レプリケーションの種類 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e73bdd657a12e4eda65ce7cc16f2e9d139ce9913
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="types-of-replication"></a>レプリケーションの種類
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、以下の種類のレプリケーションを分散アプリケーションで利用できます。  
  
-   トランザクション レプリケーション。 詳細については、「[Transactional Replication](../../relational-databases/replication/transactional/transactional-replication.md)」 (トランザクション レプリケーション) を参照してください。  
  
-   マージ レプリケーション。 詳細については、「[Merge Replication](../../relational-databases/replication/merge/merge-replication.md)」 (マージ レプリケーション) をご覧ください。  
  
-   スナップショット レプリケーション。 詳細については、「[Snapshot Replication](../../relational-databases/replication/snapshot-replication.md)」 (スナップショット レプリケーション) をご覧ください。  
  
 アプリケーションで使用するレプリケーションの種類は、物理的なレプリケーション環境、レプリケートするデータの種類と量、データをサブスクライバーで更新するかどうかなどの、さまざまな要因によって異なります。 物理環境には、レプリケーションに関係するコンピューターの数と場所、これらのコンピューターがクライアント (ワークステーション、ラップトップ、またはハンドヘルド デバイス) なのかサーバーなのか、などが含まれます。  
  
 どの種類のレプリケーションも、通常、パブリッシュされたオブジェクトをパブリッシャーとサブスクライバー間で初期同期することから始まります。 初期同期は、 *スナップショット*を使用したレプリケーションで実行できます。スナップショットは、パブリケーションで指定されたすべてのオブジェクトおよびデータのコピーです。 作成されたスナップショットはサブスクライバーに配信されます。 アプリケーションによっては、スナップショット レプリケーションのみで十分なこともあります。 スナップショット レプリケーションだけでは不十分なアプリケーションでは、その後行われたデータ変更が、一定期間にわたって増分としてサブスクライバーに渡されることが重要です。 また、アプリケーションによっては、サブスクライバーからパブリッシャーに変更を送り返す必要もあります。 トランザクション レプリケーションおよびマージ レプリケーションには、このような種類のアプリケーション用のオプションがあります。  
  
 スナップショット レプリケーションでは、データの変更は追跡されず、スナップショットが適用されるたびに、既存のデータがすべて上書きされます。 トランザクション レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] トランザクション ログを使用して変更が追跡され、マージ レプリケーションでは、トリガーとメタデータ テーブルを使用して変更が追跡されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  

