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
ms.topic: article
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f4d0b776422d9570b22e36382ebbc1c655c901e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075718"
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
  
  