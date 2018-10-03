---
title: MSdbms_map (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSdbms_map
- MSdbms_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_map system table
ms.assetid: df67e691-3a50-450a-99c5-8c4a041749ae
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a718cd7130e13ed5e9afddadddf7c1b5e3ee0ccf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832960"
---
# <a name="msdbmsmap-transact-sql"></a>MSdbms_map (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_map**テーブルには、元とコピー先の DBMS の組の既定の変換先データ型の情報へのリンクだけでなく、ソース データの型情報が含まれています。 このテーブルに格納されます、 **msdb**データベース、異種パブリッシングに使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**map_id**|**int**|データ型マッピングの一意識別子。|  
|**src_dbms_id**|**int**|指定することで、マップ元 DBMS を識別します。 その**dbms_id**で、 [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md)テーブル。|  
|**dest_dbms_id**|**int**|指定することで、マップ先 DBMS を識別します。 その**dbms_id**で、 [MSdbms](../../relational-databases/system-tables/msdbms-transact-sql.md)テーブル。|  
|**src_datatype_id**|**int**|識別、 **datatype_id**から、 [MSdbms_datatype](../../relational-databases/system-tables/msdbms-datatype-transact-sql.md)テーブルのソース データの種類。|  
|**src_len_min**|**bigint**|マップ元 DBMS におけるデータ型の最小の長さ。値 NULL は長さが使用されないことを示します。|  
|**src_len_max**|**bigint**|マップ元 DBMS におけるデータ型の最大の長さ。値 NULL は長さが使用されないことを示します。|  
|**src_prec_min**|**bigint**|マップ元 DBMS におけるデータ型の最小有効桁数。値 NULL は有効桁数が使用されないことを示します。|  
|**src_prec_max**|**bigint**|マップ元 DBMS におけるデータ型の最大有効桁数。値 NULL は有効桁数が使用されないことを示します。|  
|**src_scale_min**|**int**|マップ元 DBMS におけるデータ型の最小小数点以下桁数。値 NULL は小数点以下桁数が使用されないことを示します。|  
|**src_scale_max**|**int**|マップ元 DBMS におけるデータ型の最大小数点以下桁数。値 NULL は小数点以下桁数が使用されないことを示します。|  
|**src_nullable**|**bit**|マッピングのマップ先列で NULL 値が許容されるかどうかを示します。値 NULL はこの定義が必要ではないことを示します。|  
|**default_datatype_mapping_id**|**int**|指定することで、既定のデータ型マッピングを識別します。 その**map_id**テーブル[MSdbms_datatype_mapping](../../relational-databases/system-tables/msdbms-datatype-mapping-transact-sql.md)します。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
