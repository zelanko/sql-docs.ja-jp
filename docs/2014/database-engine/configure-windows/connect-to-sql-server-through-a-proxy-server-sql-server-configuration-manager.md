---
title: プロキシ サーバー (SQL Server 構成マネージャー) を介して SQL Server への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1eb07c9e7b17caa4498ab8ddbc70388ae8a8cebc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178727"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>プロキシ サーバーを介して SQL Server に接続する方法 (SQL Server 構成マネージャー)
  このトピックでは、SQL Server 構成マネージャーを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でプロキシ サーバーを介して SQL Server に接続する方法について説明します。 リモート WinSock (RWS) 経由でリモートで受信待ちするには、受信待ちするノード アドレスがローカル アドレス テーブル (LAT) のエントリの範囲外になるように、プロキシ サーバーに対して LAT を定義します。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Microsoft Proxy Server を介して SQL Server に接続できるようにするには  
  
1.  「[特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](configure-a-server-to-listen-on-a-specific-tcp-port.md)」の手順に従い、[!INCLUDE[ssDE](../../includes/ssde-md.md)] で使用される TCP/IP ポートを判断するか、任意のポートを使用するように [!INCLUDE[ssDE](../../includes/ssde-md.md)] を構成します。  
  
2.  プロキシ サーバーで、プロキシ サーバー用のローカル アドレス テーブル (LAT) を定義し、受信待ちするノード アドレスが LAT エントリの範囲外になるようにします。 詳細については、プロキシ サーバーのマニュアルを参照してください。  
  
  