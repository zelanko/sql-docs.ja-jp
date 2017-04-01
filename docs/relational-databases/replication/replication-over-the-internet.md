---
title: "インターネット経由のレプリケーション | Microsoft Docs"
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
  - "Web パブリッシュ [SQL Server レプリケーション], Web パブリッシュについて"
  - "Web パブリッシュ [SQL Server レプリケーション]"
  - "インターネット [SQL Server レプリケーション]"
  - "インターネット [SQL Server レプリケーション], パブリッシュ"
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# インターネット経由のレプリケーション
  インターネット経由でデータをレプリケートすると、リモートおよび未接続のユーザーが必要に応じて、インターネット接続を使用してデータにアクセスできます。 インターネット経由のデータのレプリケーションでは、以下を使用します。  
  
-   仮想プライベート ネットワーク (VPN)。 詳細については、次を参照してください。 [インターネットを使用して VPN 経由でデータを発行](../../relational-databases/replication/publish-data-over-the-internet-using-vpn.md)します。  
  
-   マージ レプリケーション用の Web 同期オプション。 詳細については、次を参照してください。 [マージ レプリケーション用に Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)します。  
  
 すべての種類の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションは、VPN 経由でデータをレプリケートすることができますが、マージ レプリケーションを使用している場合は、Web 同期を検討する必要があります。  
  
  