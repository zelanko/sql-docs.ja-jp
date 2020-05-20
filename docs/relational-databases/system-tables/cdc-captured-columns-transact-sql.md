---
title: cdc. captured_columns (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.captured_columns
- cdc.captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.captured_columns
ms.assetid: 7bb4d408-d764-4ef6-802c-f271c8d39c2a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1a635ab2284a413fb3a4cf9e11b9f40e0369f958
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832446"
---
# <a name="cdccaptured_columns-transact-sql"></a>cdc.captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キャプチャインスタンスで追跡されている列ごとに1行の値を返します。 既定では、ソーステーブルのすべての列がキャプチャされます。 ただし、列リストを指定することで、ソース テーブルでの変更データ キャプチャが有効になっているときに列を含めたり除外したりできます。 詳細については、「 [sys. sp_cdc_enable_table &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)」を参照してください。  
  
 **システムテーブルに対して直接クエリを実行しない**ことをお勧めします。 代わりに、 [sp_cdc_get_source_columns](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)ストアドプロシージャを実行します。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|キャプチャされた列が属するソーステーブルの ID。|  
|**column_name**|**sysname**|キャプチャされた列の名前です。|  
|**column_id**|**int**|ソーステーブル内のキャプチャされた列の ID。|  
|**column_type**|**sysname**|キャプチャされた列の種類。|  
|**column_ordinal**|**int**|変更テーブル内の列の序数 (1 から始まる)。 変更テーブル内のメタデータ列は除外されます。 最初にキャプチャされた列には、序数1が割り当てられます。|  
|**is_computed**|**bit**|キャプチャされた列がソーステーブル内の計算列であることを示します。|  
  
## <a name="see-also"></a>参照  
 [cdc. change_tables &#40;Transact-sql&#41;](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
