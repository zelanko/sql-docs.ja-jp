---
title: SQL Server、Catalog Metadata オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0474646ae51a8fdabe6ff139c6eff1ec966f8d93
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158810"
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
