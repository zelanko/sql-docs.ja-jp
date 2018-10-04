---
title: MSmerge_partition_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b0b9f18377de89f6cf607f9aaab6c294f4a716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846570"
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_partition_groups**テーブルでは、それぞれ特定のデータベースでパーティションを事前計算済みの 1 行が格納されます。 一覧されている列に加えて、パラメーター化された行フィルターで使用される関数ごとに 1 列のデータがこのテーブルに追加されます。 たとえば、という名前の列**HOST_NAME**フィルターを使用している場合に、テーブルに追加、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)関数。 このパブリッシャーと同期された関数値の一意のセットごとに 1 行のデータが格納されます。 これらすべての関数について、まったく同じ値と同期しているサブスクライバーが 2 つ以上あれば、このテーブル内の同じ行を共有し、パーティション ID も同じになります。このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|事前計算済みパーティションの一意な ID 番号を示す ID 列です。|  
|**publication_number**|**smallint**|格納されているパブリケーションの番号**sysmergepublications**します。|  
|**maxgen_whenadded**|**bigint**|このテーブルに行が挿入される時点で、パブリッシャーで把握している最も古い generation 値です。|  
|**using_partition_groups**|**bit**|事前計算済みパーティションを使用するパブリケーションにパーティションが属するかどうかを示します。次の値のいずれかになります。<br /><br /> **0** = パブリケーションは事前計算済みパーティションを使用しません。<br /><br /> **1**パブリケーションは事前計算済みパーティションを =<br /><br /> 詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。|  
|**HOST_NAME**|**nvarchar(128)**|パラメーター化された行フィルターを使用してパーティションを生成するときに提供される値です。 詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
