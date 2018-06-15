---
title: MSdbms_datatype_mapping (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdbms_datatype_mapping_TSQL
- MSdbms_datatype_mapping
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype_mapping system table
ms.assetid: 13289a0b-dfb0-4771-ad80-4c5f83cded99
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 69bc82596929c5ba42c7f67b63c8c57b56cb3561
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33004749"
---
# <a name="msdbmsdatatypemapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdbms_datatype_mapping**テーブルには、マップ先 DBMS での 1 つまたは複数の特定のデータ型を元のデータベース管理システム (DBMS) でのデータ型から、許容されるデータ型のマッピングが含まれています。 次の表は、 **msdb**データベースにあり、異種データベース レプリケーションに使用します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|個々のデータ型マッピングを一意に識別します。|  
|**map_id**|**int**|マッピング元のデータ型を識別します。|  
|**dest_datatype_id**|**int**|マッピング先のデータ型を識別します。|  
|**dest_precision**|**bigint**|ターゲットの場所、値は NULL では、有効桁数が使用されないことを意味、データ型の有効桁数の値を定義 **-1**ソースのデータ型の有効桁数が使用されることを意味します。|  
|**dest_scale**|**int**|ここで、値は NULL は小数点以下桁数が使用されていないことを意味、先のデータ型の小数点以下桁数の値を定義 **-1**ソースのデータ型の小数点以下桁数が使用されていることを意味します。|  
|**dest_length**|**bigint**|ここで、値は NULL は長さが使用されないことを意味、先のデータ型の長さとの値を定義 **-1**ソースのデータ型の長さを使用することを意味します。|  
|**dest_nullable**|**bit**|マッピングのマップ先列で NULL 値が許容されるかどうかを示します。値 NULL はこの定義が必要ではないことを示します。|  
|**dest_createparams**|**int**|各データ型に適用できる長さ、有効桁数、および小数点以下桁数の組み合わせを表すビットマップです。次のようになります。<br /><br /> **0x1**有効桁数を = です。<br /><br /> **0x2**スケールを = です。<br /><br /> **0x4**長さを = です。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングを指定します。](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
