---
title: "インターネット経由のレプリケーションのセキュリティ | Microsoft Docs"
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
  - "セキュリティ [SQL Server レプリケーション], インターネット"
  - "インターネット [SQL Server レプリケーション], セキュリティ"
ms.assetid: 25b7af05-2721-4b24-9083-fb671e8bf4e0
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# インターネット経由のレプリケーションのセキュリティ
  インターネット経由のレプリケーションを利用すると、特にモバイルのサブスクライバーで必要とされるような柔軟性を実現できます。ただし、適切に構成して十分なセキュリティを確保する必要があります。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット経由で情報を安全に共有するための 2 つの手法のいずれかを使用して使用をお勧めします。  
  
-   仮想プライベート ネットワーク (VPN)  
  
-   マージ レプリケーション用の Web 同期オプション  
  
## 仮想プライベート ネットワーク  
 仮想プライベート ネットワークを使用すると、複数の層を使ったシンプルかつ安全な方法で、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデータをインターネット経由でレプリケートできます。 インターネットを介しての VPN 接続は、論理的にはサイト間のワイド エリア ネットワーク (WAN) リンクとして動作します。  
  
 これには、ユーザーがインターネットやなどのプロトコルを使用して他のパブリック ネットワークを介してトンネルを許可する [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Point-to-Point トンネリング プロトコル (PPTP) で使用できる、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows NT 4.0 または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2000 オペレーティング システム、またはレイヤー 2 トンネリング プロトコル (L2TP)、Windows 2000 オペレーティング システムで使用できます。 これにより、プライベート ネットワークとほぼ同等のセキュリティと機能が実現されます。  
  
 VPN の設定の詳細については、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のマニュアルを参照してください。  
  
## IIS による Web 同期  
 マージ レプリケーション用の Web 同期オプションを使用すると、HTTPS プロトコルを使用してデータをレプリケートできます。この方法は、ファイアウォール越しにデータをレプリケートする場合に便利です。 詳細については、次を参照してください。 [Web 同期の構成](../../../relational-databases/replication/configure-web-synchronization.md) と [Web 同期のセキュリティ アーキテクチャ](../../../relational-databases/replication/security/security-architecture-for-web-synchronization.md)します。  
  
## 参照  
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  