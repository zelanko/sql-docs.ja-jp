---
title: "SQLServer、Catalog Metadata オブジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQLServer:Catalog Metadata"
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
caps.latest.revision: 4
author: "dagiro"
ms.author: "v-dagir"
manager: "jhubbard"
caps.handback.revision: 4
---
# SQLServer、Catalog Metadata オブジェクト
**SQLServer:Catalog Metadata** パフォーマンス オブジェクトには、SQL Server のカタログ メタデータのカウンターが用意されています。

次の表では、SQL Server **Catalog Metadata** パフォーマンス オブジェクトについて説明します。


|**SQL Server Catalog Metadata カウンター**|Description|  
|-------------|-----------------|  
|**Cache Entries Count**|カタログ メタデータ キャッシュ内のエントリ数。|
|**Cache Entries Pinned Count**|固定されたカタログ メタデータ キャッシュのエントリ数。|
|**Cache Hit Ratio**|カタログ メタデータ キャッシュのヒット数と参照回数の比率。|
|**Cache Hit Ratio Base**|内部使用のみです。|

カウンターのインスタンスはデータベースごとに 1 つあります。

## 参照  
[リソースの利用状況の監視 (システム モニター)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)