---
title: インメモリ OLTP のメモリ管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d82f21fa-6be1-4723-a72e-f2526fafd1b6
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: 365d51004820d3b8c18a9f7667e1328d5bc10143
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076039"
---
# <a name="managing-memory-for-in-memory-oltp"></a>インメモリ OLTP のメモリ管理
  メモリ最適化テーブルでは、すべての行とインデックスをメモリ内に保持するために十分なメモリが必要です。 メモリは有限のリソースであるため、システム上のメモリ使用量を把握して管理することが重要です。 このセクションのトピックでは、一般的なメモリの使用量と管理シナリオについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|セクション|説明|  
|-------------|-----------------|  
|[メモリ最適化テーブルのメモリ必要量の推定](../relational-databases/in-memory-oltp/memory-optimized-tables.md)|テーブルに必要なメモリ量を推定します。|  
|[メモリ最適化テーブルを持つデータベースのリソース プールへのバインド](../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)|データベースをリソース プールにバインドする手順を示すチュートリアル。|  
|[メモリ使用量の監視とトラブルシューティング](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)|メモリ使用量を監視するために使用できるツール。 メモリ使用量が多くなりすぎた場合のトラブルシューティングについても説明します。|  
|[メモリ不足の問題の解決](../relational-databases/in-memory-oltp/resolve-out-of-memory-issues.md)|OOM (メモリ不足) 状態から回復する手順。|  
|[データベースの復元とリソース プールへのバインド](../relational-databases/in-memory-oltp/restore-a-database-and-bind-it-to-a-resource-pool.md)|[!INCLUDE[hek_2](../includes/hek-2-md.md)] データベースを復元して名前付きリソース プールにバインドする手順。|  
|[インメモリ OLTP ガベージ コレクション](../relational-databases/in-memory-oltp/in-memory-oltp-garbage-collection.md)|削除された行でのガベージ コレクションの動作に関する理解を深めることができます。|  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  