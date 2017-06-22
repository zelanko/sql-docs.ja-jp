---
title: "SQL Server、Memory Broker Clerks オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7cf0f0a0d8ef7f7e8dec4a7a743dbc25bc98bb8d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server、Memory Broker Clerks オブジェクト
**SQLServer:Memory Broker Clerks** パフォーマンス オブジェクトは、Memory Broker Clerk に関する統計情報のカウンターを提供します。

次の表では、SQL Server の **Memory Broker Clerks** パフォーマンス オブジェクトについて説明します。

|**SQL Server Memory Broker Clerks のカウンター**|Description|  
|-------------|-----------------|  
|**内部の利点**|エントリ数負荷に対するメモリの内部値 (ミリ秒/ページ/ミリ秒単位) に 100 億を掛けて小数点以下を切り捨てたもの。|
|**Memory Broker Clerk のサイズ**|Clerk のサイズ (ページ単位)。|
|**定期的な削除 (ページ)**|前回の定期的な削除によって Broker Clerk から削除されたページ数。|
|**メモリ不足による削除 (ページ/秒)**|メモリ不足によって Broker Clerk から削除された 1 秒あたりのページ数。|
|**シミュレーションの利点**|Clerk に対するメモリの値 (ミリ秒/ページ/ミリ秒単位) に 100 億を掛けて小数点以下を切り捨てたもの。|
|**シミュレーションのサイズ**|クラーク シミュレーションの現在のサイズ (ページ単位)。|

バッファー プールと列ストア オブジェクト プールのカウンターのインスタンスがあります。

## <a name="see-also"></a>参照  
[リソースの利用状況の監視 (システム モニター)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
