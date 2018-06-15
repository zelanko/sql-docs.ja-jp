---
title: SQL Server、Memory Broker Clerks オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: abc1812029cdf51d829b6e15a4049d05a7ae5383
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950437"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server、Memory Broker Clerks オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
