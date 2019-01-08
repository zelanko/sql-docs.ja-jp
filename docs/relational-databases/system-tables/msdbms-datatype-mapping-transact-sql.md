---
title: MSdbms_datatype_mapping (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d513da9588b8ae8fb4f20ece11390c29d71bcf9
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52750097"
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype_mapping**テーブルには、マップ先 DBMS での 1 つまたは複数の特定のデータ型を元のデータベース管理システム (DBMS) でのデータ型から使用可能なデータ型のマッピングが含まれています。 このテーブルに格納されます、 **msdb**データベースにあり、異種データベース レプリケーションに使用します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|個々のデータ型マッピングを一意に識別します。|  
|**map_id**|**int**|マッピング元のデータ型を識別します。|  
|**dest_datatype_id**|**int**|マッピング先のデータ型を識別します。|  
|**dest_precision**|**bigint**|値が NULL の場合、有効桁数が使用されないことに、変換先のデータ型の有効桁数と値の定義 **-1**ソースのデータ型の有効桁数が使用されることを意味します。|  
|**dest_scale**|**int**|NULL の値は、小数点以下桁数が使用されていない場合、変換先のデータ型の小数点以下桁数の値を定義します **-1**ソースのデータ型の小数点以下桁数が使用されていることを意味します。|  
|**dest_length**|**bigint**|値が NULL の場合、長さが使用されないことに、変換先のデータ型の長さと値の定義 **-1**ソースのデータ型の長さを使用することを意味します。|  
|**dest_nullable**|**bit**|マッピングのマップ先列で NULL 値が許容されるかどうかを示します。値 NULL はこの定義が必要ではないことを示します。|  
|**dest_createparams**|**int**|各データ型に適用できる長さ、有効桁数、および小数点以下桁数の組み合わせを表すビットマップです。次のようになります。<br /><br /> **0x1** = 有効桁数。<br /><br /> **0x2**スケールを = です。<br /><br /> **0x4**長さを = です。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
