---
title: dm_pdw_nodes_exec_query_plan (Transact-sql) |Microsoft Docs
description: プランハンドルで指定されたバッチのプラン表示を XML 形式で返す動的管理ビュー。 プラン ハンドルで指定するプランは、キャッシュ内のもの、または現在実行中のものを指定できます。
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
ms.openlocfilehash: 96b499ea5bc38d2a4cf9c380116108009ea46086
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "73145637"
---
# <a name="syspdw_nodes_dm_exec_query_plan-transact-sql"></a>pdw_nodes_dm_exec_query_plan (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

プラン ハンドルで指定されたバッチのプラン表示を XML 形式で返します。 プラン ハンドルで指定するプランは、キャッシュ内のもの、または現在実行中のものを指定できます。  

## <a name="table-returned"></a>返されたテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|ノードに関連付けられている一意の数値 ID。| 
|**dbid**|**smallint**|このプランに対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコンパイルされたときに有効であったコンテキスト データベースの ID。 計画外および準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。<br /><br /> NULL 値は許可されます。|  
|**objectid**|**int**|ストアド プロシージャやユーザー定義関数など、クエリ プランのオブジェクトの ID。 アドホック バッチおよび準備されたバッチの場合、この列の値は **NULL** です。<br /><br /> NULL 値は許可されます。|  
|**number**|**smallint**|ストアド プロシージャに付けられた番号 (整数)。 アドホック バッチおよび準備されたバッチの場合、この列の値は **NULL** です。<br /><br /> NULL 値は許可されます。| 
|**暗号**|**bit**|対応するプロシージャが暗号化されているかどうか。<br /><br /> 0 = 暗号化されていない<br /><br /> 1 = 暗号化されている<br /><br /> NULL 値は許可されません。|  
|**query_plan**|**xml**|*Plan_handle*で指定されたクエリ実行プランのコンパイル時のプラン表示表現を格納します。 プラン表示は XML 形式です。 アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、ストアド プロシージャ コール、ユーザー定義関数コールなどを含むバッチごとに、1 つのプランが生成されます。<br /><br /> NULL 値は許可されます。|  
  
## <a name="remarks"></a>Remarks  
[Dm_exec_query_plan](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql?view=sql-server-ver15)適用される同じコメント。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する**sysadmin**サーバー `VIEW SERVER STATE`ロールまたは権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>次のステップ
 開発に関するその他のヒントについては、[SQL Data Warehouse の開発の概要](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop)に関する記事をご覧ください。