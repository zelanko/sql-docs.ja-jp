---
title: 'SQL Server: Cursor Manager by Type オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cab113ccef644267056edcc898412ba90fbc68c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37322342"
---
# <a name="sql-server-cursor-manager-by-type-object"></a>SQL Server: Cursor Manager by Type オブジェクト
  **SQLServer:Cursor Manager by Type** オブジェクトには、種類別にグループ化されたカーソルを監視するカウンターが用意されています。  
  
 次の表で、SQL Server **Cursor Manager by Type** カウンターについて説明します。  
  
|Cursor Manager by Type カウンター|説明|  
|-------------------------------------|-----------------|  
|**Active cursors**|アクティブなカーソルの数。|  
|**Cache Hit Ratio**|キャッシュ ヒットとキャッシュ参照の比率。|  
|**Cached Cursor Counts**|キャッシュ内の特定種類のカーソルの数。|  
|**Cursor Cache Use Count/sec**|キャッシュされている各種のカーソルが使用された時間。|  
|**Cursor memory usage**|カーソルによって消費されたメモリ量 (KB)。|  
|**Cursor Requests/sec**|サーバーが受け取った SQL カーソル要求の数。|  
|**Cursor worktable usage**|カーソルによって使用された作業テーブルの数。|  
|**Number of active cursor plans**|カーソル プランの数。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Cursor Manager のインスタンス|説明|  
|-----------------------------|-----------------|  
|**_Total**|すべてのカーソルに関する情報。|  
|**API Cursor**|API カーソルのみに関する情報。|  
|**TSQL Global Cursor**|[!INCLUDE[tsql](../../includes/tsql-md.md)] グローバル カーソルのみに関する情報。|  
|**TSQL Local Cursor**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ローカル カーソルのみに関する情報。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  
