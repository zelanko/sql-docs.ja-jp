---
title: "SQL Server、Catalog Metadata オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 
author: dagiro
ms.author: v-dagir
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86913554f86a9965906d37f8a7ff683570dfb8ad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-catalog-metadata-object"></a>SQLServer、Catalog Metadata オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **SQLServer:Catalog Metadata** パフォーマンス オブジェクトには、SQL Server のカタログ メタデータのカウンターが用意されています。

次の表では、SQL Server **Catalog Metadata** パフォーマンス オブジェクトについて説明します。


|**SQL Server Catalog Metadata カウンター**|Description|  
|-------------|-----------------|  
|**Cache Entries Count**|カタログ メタデータ キャッシュ内のエントリ数。|
|**Cache Entries Pinned Count**|固定されたカタログ メタデータ キャッシュのエントリ数。|
|**Cache Hit Ratio**|カタログ メタデータ キャッシュのヒット数と参照回数の比率。|
|**Cache Hit Ratio Base**|内部使用のみです。|

カウンターのインスタンスはデータベースごとに 1 つあります。

## <a name="see-also"></a>参照  
[リソースの利用状況の監視 (システム モニター)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
