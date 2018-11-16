---
title: SQL Server、Catalog Metadata オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 84a8e5324d5dcb1f2727fbc73d3a9c1f75fda618
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558369"
---
# <a name="sql-server-catalog-metadata-object"></a>SQLServer、Catalog Metadata オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**SQLServer:Catalog Metadata** パフォーマンス オブジェクトには、SQL Server のカタログ メタデータのカウンターが用意されています。

次の表では、SQL Server **Catalog Metadata** パフォーマンス オブジェクトについて説明します。


|**SQL Server Catalog Metadata カウンター**|[説明]|  
|-------------|-----------------|  
|**Cache Entries Count**|カタログ メタデータ キャッシュ内のエントリ数。|
|**Cache Entries Pinned Count**|固定されたカタログ メタデータ キャッシュのエントリ数。|
|**Cache Hit Ratio**|カタログ メタデータ キャッシュのヒット数と参照回数の比率。|
|**Cache Hit Ratio Base**|内部使用のみです。|

カウンターのインスタンスはデータベースごとに 1 つあります。

## <a name="see-also"></a>参照  
[リソースの利用状況の監視 (システム モニター)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
