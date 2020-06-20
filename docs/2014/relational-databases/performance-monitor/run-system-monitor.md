---
title: システム モニターの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dd0baf32402d69e36dc5120d0259b2f8d689897
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84998218"
---
# <a name="run-system-monitor"></a>システム モニターの実行
  システム モニターは、リモート プロシージャ コール (RPC) を使用して Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から情報を収集します。 Microsoft Windows でシステム モニターを実行する権限が与えられているユーザーであれば、だれでもシステムをモニターを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を監視できます。  
  
> [!NOTE]  
>  システム モニターまたはパフォーマンス モニターを使用している場合は、Microsoft Windows 98 上で動作している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続することはできません。  
  
 その他のすべてのパフォーマンス監視ツールと同様に、システム モニターを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を監視する場合は、パフォーマンスのオーバーヘッドが生じるものと予想してください。 特定のインスタンスによる実際のオーバーヘッドは、ハードウェア プラットフォーム、カウンターの数、選択した更新間隔によって異なります。 ただし、システム モニターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に統合した場合は、パフォーマンスの低下を最小限に抑えるように設計されています。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パフォーマンス カウンターを選択してシステム モニター スナップインで監視を行う場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されていなくてもカウンターが表示されます。  
  
 システム モニターを起動する方法については、「[システム モニターの起動&#40;Windows&#41;](../performance/start-system-monitor-windows.md)」をご覧ください。  
  
  
