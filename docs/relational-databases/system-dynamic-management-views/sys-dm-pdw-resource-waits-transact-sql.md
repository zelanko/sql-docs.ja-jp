---
title: "sys.dm_pdw_resource_waits (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58705ccfce21ba368d7b9b587f5becffbe349888
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>sys.dm_pdw_resource_waits (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  表示情報をすべてのリソースの種類の待機[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|待機リスト内の要求の位置。|0 から始まる序数です。 これは、待機のすべてのエントリでない一意です。|  
|session_id|**nvarchar (32)**|待機状態が発生したセッションの ID。|Session_id を参照してください[sys.dm_pdw_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|型|**nvarchar (255)**|このエントリが表す待機の種類。|有効値は次のとおりです。<br /><br /> 接続<br /><br /> ローカル クエリの同時実行<br /><br /> 分散クエリの同時実行<br /><br /> DMS の同時実行<br /><br /> バックアップの同時実行|  
|object_type|**nvarchar (255)**|待機によって影響を受けるオブジェクトの型。|有効値は次のとおりです。<br /><br /> **オブジェクト**<br /><br /> **DATABASE**<br /><br /> **システム**<br /><br /> **SCHEMA**<br /><br /> **アプリケーション**|  
|object_name|**nvarchar (386)**|名前または待機の影響を受けたを指定したオブジェクトの GUID。|3 部構成の名前では、テーブルとビューが表示されます。<br /><br /> 4 部構成の名前は、インデックスと統計情報が表示されます。<br /><br /> 名前、プリンシパル、およびデータベースは、文字列名です。|  
|request_id|**nvarchar (32)**|待機状態が発生した要求の ID。|要求の QID 識別子です。<br /><br /> 読み込み要求の GUID 識別子。|  
|request_time|**datetime**|ロックまたはリソースが要求される時刻。||  
|acquire_time|**datetime**|これで、ロックまたはリソースが取得された時刻です。||  
|state|**nvarchar (50)**|待機状態の状態です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|待機中の項目の優先度。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|同時実行スロット (最大 32 個) の数がこの要求用に予約します。|1 – SmallRC の<br /><br /> 3 – MediumRC の<br /><br /> LargeRC の 7<br /><br /> XLargeRC の: 22|  
|resource_class|**nvarchar (20)**|この要求のリソース クラスです。|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
