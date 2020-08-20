---
description: MSdbms_datatype_mapping (Transact-SQL)
title: MSdbms_datatype_mapping (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bfdf9ab815a1623aa6c323c256b9f7a4d4e27263
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488797"
---
# <a name="msdbms_datatype_mapping-transact-sql"></a>MSdbms_datatype_mapping (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSdbms_datatype_mapping**テーブルには、ソースデータベース管理システム (DBMS) のデータ型から、マップ先 DBMS の1つ以上の特定のデータ型への許容データ型マッピングが含まれています。 このテーブルは **msdb** データベースに格納され、異種データベースレプリケーションに使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**datatype_mapping_id**|**int**|個々のデータ型マッピングを一意に識別します。|  
|**map_id**|**int**|変換元のデータ型を識別します。|  
|**dest_datatype_id**|**int**|変換先のデータ型を識別します。|  
|**dest_precision**|**bigint**|変換先のデータ型の有効桁数を定義します。値が NULL の場合、有効桁数は使用されず、値が **-1** の場合は、変換元のデータ型の有効桁数が使用されます。|  
|**dest_scale**|**int**|変換先のデータ型の小数点以下桁数を定義します。値が NULL の場合、小数点以下桁数は使用されません。値が **-1** の場合は、変換元のデータ型の小数点以下桁数が使用されます。|  
|**dest_length**|**bigint**|変換先のデータ型の長さを定義します。値が NULL の場合、長さは使用されません。値が **-1** の場合は、変換元のデータ型の長さが使用されます。|  
|**dest_nullable**|**bit**|マッピングの変換先列で NULL 値を許容するかどうかを示します。値が NULL の場合、この定義は必要ありません。|  
|**dest_createparams**|**int**|各データ型に適用できる長さ、有効桁数、および小数点以下桁数の組み合わせを記述するビットマップ。次のようなものが含まれます。<br /><br /> **0x1** = 有効桁数。<br /><br /> **0x2** = スケール。<br /><br /> **0x4** = 長さ。|  
  
## <a name="see-also"></a>参照  
 [異種データベース レプリケーション](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Oracle パブリッシャーのデータ型マッピングの指定](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
