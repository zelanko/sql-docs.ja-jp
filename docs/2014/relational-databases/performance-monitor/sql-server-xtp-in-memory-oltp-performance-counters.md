---
title: XTP (インメモリ OLTP) パフォーマンス カウンター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 747f49174ff7c67584816c7f4f0d160e00cde0c1
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43819768"
---
# <a name="xtp-in-memory-oltp-performance-counters"></a>XTP (インメモリ OLTP) パフォーマンス カウンター
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、パフォーマンス モニターがインメモリ OLTP のアクティビティを監視するために使用できるオブジェクトとカウンターが用意されています。  
  
##  <a name="SQLServerPOs"></a> XTP (インメモリ OLTP) パフォーマンス オブジェクト  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトについて説明します。  
  
|パフォーマンス オブジェクト|説明|  
|------------------------|-----------------|  
|[XTP Cursors](../cursors.md)|XTP Cursors パフォーマンス オブジェクトには、XTP エンジンの内部カーソルに関連するカウンターが含まれています。 カーソルは、低レベルの構成の処理に XTP エンジンの使用をブロックする[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 このため、通常はユーザー側でカーソルを直接管理することはありません。|  
|[XTP Garbage Collection](sql-server-xtp-garbage-collection.md)|XTP Garbage Collection パフォーマンス オブジェクトには、XTP エンジンのガベージ コレクターに関連するカウンターが含まれています。|  
|[XTP Phantom Processor](sql-server-xtp-phantom-processor.md)|XTP Phantom Processor パフォーマンス オブジェクトには、XTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。 このコンポーネントには、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。|  
|[XTP ストレージ](sql-server-xtp-storage.md)|XTP ストレージのパフォーマンス オブジェクトには、XTP ストレージに関連するカウンターが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|[XTP Transaction Log](sql-server-xtp-transaction-log.md)|XTP トランザクション ログ パフォーマンス オブジェクトには、XTP トランザクション ロギングに関連するカウンターが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|[XTP Transactions](sql-server-xtp-transactions.md)|XTP トランザクションのパフォーマンス オブジェクトには、XTP エンジン トランザクションに関連するカウンターが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
  
  
