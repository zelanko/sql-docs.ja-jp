---
title: "VPN を使用したインターネット経由のデータのパブリッシュ | Microsoft Docs"
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
  - "VPN [SQL Server レプリケーション]"
  - "Web 公開 [SQL Server レプリケーション], VPN"
  - "インターネット [SQL Server レプリケーション], VPN"
ms.assetid: 9ffb6546-9973-4574-aaa0-8fe0017e3601
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# VPN を使用したインターネット経由のデータのパブリッシュ
  仮想プライベート ネットワーク (VPN) 技術を使用すると、自宅、支店、リモート クライアント、および他社で作業しているユーザーが安全な通信を維持しながらインターネット経由で企業ネットワークに接続できます。 ユーザーは、ローカル エリア ネットワーク (LAN) 上にいる場合と同じように Windows 認証を使用できます。 すべての種類の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションは、VPN 経由でデータをレプリケートできますが、Web 同期が、VPN の必要性がなくなるため、マージ レプリケーションを使用している場合は、Web 同期の使用を検討します。 詳細については、次を参照してください。 [マージ レプリケーション用に Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)します。  
  
 VPN にはクライアント ソフトウェアが含まれているので、コンピューターはインターネットを介して (場合によってはイントラネットも介して)、専用のコンピューターまたはサーバー内のソフトウェアに接続できます。 ユーザー認証方式に加えて、オプションで接続の両端に暗号化が使用されます。 インターネットを介しての VPN 接続は、論理的にはサイト間のワイド エリア ネットワーク (WAN) リンクとして動作します。  
  
 VPN は、別のネットワークを使用して、ネットワークのコンポーネントに接続します。 接続するには、ユーザーは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Point-to-Point トンネリング プロトコル (PPTP) またはレイヤー 2 トンネリング プロトコル (L2TP) などのプロトコルを使用して、インターネットまたは別のパブリック ネットワークを経由したトンネリングを行います。 以前はプライベート ネットワークでのみ実現されていたセキュリティと機能が、この環境でも同じように実現されます。 PPTP は、Microsoft Windows NT version 4.0 で使用できると [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 (以降) のオペレーティング システムです。L2TP は、以降 Windows 2000 で利用できます。  
  
 ユーザーには、インターネットの中間のルーティング インフラストラクチャは見えず、データが専用のプライベート リンクを経由して送信されているように感じられます。 ユーザーにとっては、VPN によってユーザーのコンピューターと企業のサーバー間がポイント ツー ポイントで接続されているのと同様になります。  
  
 リモート クライアントが VPN を使用して接続するように構成され、インターネットにアクセスし、企業 LAN にログインした後は、そのリモート クライアントが LAN に直接接続しているのと同じようにレプリケーションを構成できます。 セキュリティを確保するため、VPN 経由で接続しているユーザーと LAN で直接接続しているユーザーには別々のネットワーク リソースを提供することができます。  
  
 VPN の設定の詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のマニュアルを参照してください。  
  
## 参照  
 [インターネット経由のレプリケーション](../../relational-databases/replication/replication-over-the-internet.md)  
  
  