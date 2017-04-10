---
title: "システム モニターの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "システム モニター [SQL Server], 実行"
  - "Windows システム モニター [SQL Server], 実行"
  - "リモート プロシージャ コール [SQL Server]"
  - "Windows NT システム モニターの起動"
  - "RPC"
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# システム モニターの実行
  システム モニターは、リモート プロシージャ コール (RPC) を使用して Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報を収集します。 Microsoft Windows でシステム モニターを実行する権限が与えられているユーザーであれば、だれでもシステムをモニターを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を監視できます。  
  
> [!NOTE]  
>  システム モニターまたはパフォーマンス モニターを使用している場合は、Microsoft Windows 98 上で動作している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続することはできません。  
  
 その他のすべてのパフォーマンス監視ツールと同様に、システム モニターを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を監視する場合は、パフォーマンスのオーバーヘッドが生じるものと予想してください。 特定のインスタンスによる実際のオーバーヘッドは、ハードウェア プラットフォーム、カウンターの数、選択した更新間隔によって異なります。 ただし、システム モニターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に統合した場合は、パフォーマンスの低下を最小限に抑えるように設計されています。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パフォーマンス カウンターを選択してシステム モニター スナップインで監視を行う場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていなくてもカウンターが表示されます。  
  
 システム モニターを起動する方法については、「[システム モニターの起動&#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md)」をご覧ください。  
  
  