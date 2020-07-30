---
title: dm_pdw_nodes_exec_sql_text (Transact-sql) |Microsoft Docs
description: 指定された sql_handle によって識別される SQL バッチのテキストを返す動的管理ビュー。
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: dcfa1bf254bc60ee1bd2c65ddb813851d0bd369e
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394322"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>pdw_nodes_dm_exec_sql_text (Transact-sql)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

指定された*sql_handle*によって識別される SQL バッチのテキストを返します。 このテーブル値関数は、システム関数 **fn_get_sql** に代わるものです。  
   
## <a name="table-returned"></a>返されたテーブル  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|ノードに関連付けられている一意の数値 ID。|
|**dbid**|**smallint**|データベースの ID。<br /><br /> 計画外および準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。|  
|**objectid**|**int**|オブジェクトの ID。<br /><br /> アドホック SQL ステートメントおよび準備された SQL ステートメントの場合は NULL になります。|  
|**number**|**smallint**|番号付きストアド プロシージャの場合、ストアド プロシージャの番号。 詳細については、「 [sys. numbered_procedures &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md)」を参照してください。<br /><br /> アドホック SQL ステートメントおよび準備された SQL ステートメントの場合は NULL になります。|  
|**暗号**|**bit**|1: SQL テキストは暗号化されています。<br /><br /> 0: SQL テキストは暗号化されていません。|  
|**text**|**nvarchar(max)**|SQL クエリのテキスト。<br /><br /> 暗号化されているオブジェクトの場合は NULL になります。|  

## <a name="remarks"></a>解説  
[Dm_exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15)適用される同じコメント。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する**sysadmin**サーバーロールまたは権限が必要 `VIEW SERVER STATE` です。  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>次のステップ
 開発に関するその他のヒントについては、[SQL Data Warehouse の開発の概要](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop)に関する記事をご覧ください。