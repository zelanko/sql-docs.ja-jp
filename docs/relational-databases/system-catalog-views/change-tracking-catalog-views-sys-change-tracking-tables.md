---
title: "sys.change_tracking_tables (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- change_tracking_tables_TSQL
- sys.change_tracking_tables
- change_tracking_tables
- sys.change_tracking_tables_TSQL
dev_langs: TSQL
helpviewer_keywords:
- change tracking [SQL Server], sys.change_tracking_tables
- sys.change_tracking_tables
ms.assetid: 97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b
caps.latest.revision: "13"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a921017fae8b8ec70c04787a8327c9389df23f3f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="change-tracking-catalog-views---syschangetrackingtables"></a>変更の追跡カタログ ビューでは、sys.change_tracking_tables
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  変更の追跡が有効な現在のデータベース内のテーブルごとに 1 行のデータを返します。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|変更ジャーナルを持つテーブルの ID。 テーブルは、変更の追跡が現在無効になっている場合でも、変更ジャーナルを持つことができます。<br /><br /> テーブル ID はデータベース内で一意です。|  
|is_track_columns_updated_on|**bit**|テーブルに対する変更の追跡の現在の状態。<br /><br /> 0 = OFF<br /><br /> 1 = ON |  
|begin_version|**bigint**|テーブルに対する変更の追跡を開始したときのデータベースのバージョン。 通常、このバージョンは変更の追跡が有効にされた日時を示します。ただし、テーブルが切り捨てられると、この値はリセットされます。|  
|cleanup_version|**bigint**|クリーンアップによって変更追跡情報が削除された可能性がある最大バージョン。|  
|min_valid_version|**bigint**|テーブルで使用できる変更追跡情報の有効な最小バージョン。<br /><br /> この行に関連付けられているテーブルから変更を取得する場合、last_sync_version には、この列に表示されるバージョンと同じ値か、それよりも大きい値を指定する必要があります。 詳細については、次を参照してください。 [CHANGE_TRACKING_MIN_VALID_VERSION (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md).|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [変更の追跡カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
