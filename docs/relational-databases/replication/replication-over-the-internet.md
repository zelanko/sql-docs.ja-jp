---
title: "インターネット経由のレプリケーション | Microsoft Docs"
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
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
caps.latest.revision: "31"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 72e3ba0e441fc62d1f2e43adbc43ba73b4e6ddd8
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="replication-over-the-internet"></a>インターネット経由のレプリケーション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] インターネット経由でデータをレプリケートすると、リモートおよび未接続のユーザーが必要に応じて、インターネット接続を使用してデータにアクセスできます。 インターネット経由のデータのレプリケーションでは、以下を使用します。  
  
-   仮想プライベート ネットワーク (VPN)。 詳細については、「[Publish Data over the Internet Using VPN](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md)」 (VPN を使用したインターネット経由のデータのパブリッシュ) を参照してください。  
  
-   マージ レプリケーション用の Web 同期オプション。 詳細については、「 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)」を参照してください。  
  
 すべての種類の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションは VPN 経由でデータをレプリケートできますが、マージ レプリケーションを使用している場合は Web 同期を検討してください。  
  
  
