---
title: "SQL Server: Wait Statistics オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Wait Statistics object
- SQLServer:Wait Statistics
ms.assetid: cb7f917d-4291-4115-9b78-ee7692ebbb2d
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4c040fa96a905d3b9547163e1b75963b3ac28933
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-wait-statistics-object"></a>SQL Server: Wait Statistics オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **SQLServer:Wait Statistics** パフォーマンス オブジェクトには、待機状態に関する情報を報告するパフォーマンス カウンターが含まれています。  
  
 Wait Statistics オブジェクトに含まれるカウンターを次の表に示します。  
  
|SQL Server Wait Statistics カウンター|説明|  
|-----------------------------------------|-----------------|  
|**Lock waits**|ロックを待機しているプロセスの統計。|  
|**Log buffer waits**|ログ バッファーが使用可能になるのを待機しているプロセスの統計。|  
|**Log write waits**|ログ バッファーへの書き込みを待機しているプロセスの統計。|  
|**Memory grant queue waits**|メモリ許可が使用可能になるのを待機しているプロセスの統計。|  
|**Network IO waits**|ネットワーク I/O の待機に関する統計。|  
|**Non-Page latch waits**|ページ以外のラッチに関する統計。|  
|**Page IO latch waits**|ページ I/O ラッチに関する統計。|  
|**Page latch waits**|ページ ラッチに関する統計。I/O ラッチは含みません。|  
|**Thread-safe memory objects waits**|スレッドセーフなメモリ割り当てを待機しているプロセスの統計。|  
|**Transaction ownership waits**|トランザクションへのアクセスを同期するプロセスに関する統計。|  
|**Wait for the worker**|ワーカーが使用可能になるのを待機しているプロセスに関する統計。|  
|**Workspace synchronization waits**|ワークスペースへのアクセスを同期するプロセスに関する統計。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|アイテム|説明|  
|----------|-----------------|  
|**平均待機時間 (ミリ秒)**|選択した待機の種類の平均時間。|  
|**1 秒あたりの累積待機時間 (ミリ秒)**|選択した待機の種類の 1 秒あたりに集計された待機時間。|  
|**待機中**|次の種類で現在待機しているプロセスの数。|  
|**1 秒あたりに開始された待機回数**|選択した待機の種類の 1 秒あたりに開始された待機の回数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
