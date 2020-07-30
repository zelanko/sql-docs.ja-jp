---
title: dm_pdw_nodes_exec_query_statistics_xml (Transact-sql) |Microsoft Docs
description: インフライト要求のクエリ実行プランを返す動的管理ビュー。 この DMV を使用すると、一時的な統計情報を含む showplan XML を取得できます。
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
ms.openlocfilehash: 0fea3a43ccf786d5ebc6f9c19acb977097bea1e4
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394337"
---
# <a name="dm_pdw_nodes_exec_query_statistics_xml-transact-sql"></a>dm_pdw_nodes_exec_query_statistics_xml (Transact-sql)
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

インフライト要求のクエリ実行プランを返します。 この DMV を使用すると、一時的な統計情報を含む showplan XML を取得できます。

## <a name="table-returned"></a>返されたテーブル

|列名|データ型|説明|  
|-----------------|---------------|-----------------|
|node_id|**int**|ノードに関連付けられている一意の数値 ID。|
|session_id|**smallint**|セッションの ID。 NULL 値は許可されません。|
|request_id|**int**|要求の ID。 NULL 値は許可されません。|
|sql_handle|**varbinary(64)**|クエリが含まれているバッチまたはストアドプロシージャを一意に識別するトークンです。 NULL 値は許可されます。|
|plan_handle|**varbinary(64)**|現在実行中のバッチのクエリ実行プランを一意に識別するトークンです。 NULL 値は許可されます。|
|query_plan|**xml**|部分統計を含む*plan_handle*で指定されたクエリ実行プランのランタイム Showplan 表現を格納します。 プラン表示は XML 形式です。 アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、ストアド プロシージャ コール、ユーザー定義関数コールなどを含むバッチごとに、1 つのプランが生成されます。 NULL 値は許可されます。|

## <a name="remarks"></a>解説
[Dm_exec_query_statistics_xml](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql?view=sql-server-ver15)適用される同じコメント。   

## <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  

## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

 ## <a name="next-steps"></a>次のステップ
 開発に関するその他のヒントについては、[SQL Data Warehouse の開発の概要](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop)に関する記事をご覧ください。

