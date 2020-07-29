---
title: SQL Server、Catalog Metadata オブジェクト | Microsoft Docs
description: SQL Server のカタログ メタデータのカウンターを提供する SQLServer:Catalog Metadata パフォーマンス オブジェクトについて説明します。
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 54beed996f87ad279ed097efe8e4a8ca9558634e
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458654"
---
# <a name="sql-server-catalog-metadata-object"></a>SQLServer、Catalog Metadata オブジェクト
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
**SQLServer:Catalog Metadata** パフォーマンス オブジェクトには、SQL Server のカタログ メタデータのカウンターが用意されています。

次の表では、SQL Server **Catalog Metadata** パフォーマンス オブジェクトについて説明します。


|**SQL Server Catalog Metadata カウンター**|説明|  
|-------------|-----------------|  
|**Cache Entries Count**|カタログ メタデータ キャッシュ内のエントリ数。|
|**Cache Entries Pinned Count**|固定されたカタログ メタデータ キャッシュのエントリ数。|
|**Cache Hit Ratio**|カタログ メタデータ キャッシュのヒット数と参照回数の比率。|
|**Cache Hit Ratio Base**|内部使用専用です。|

カウンターのインスタンスはデータベースごとに 1 つあります。

## <a name="see-also"></a>参照  
[リソースの利用状況の監視 (システム モニター)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
