---
title: workload_management_workload_classifier_details (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 3fbbc52f13bebbb46a3afc7d2dd450765d28a21a
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87393972"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>workload_management_workload_classifier_details (Transact-sql)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  各分類子の詳細を返します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|分類子の ID。  NULL 値は許可されません。|
|classifier_type|**sysname**|[Workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md)に参加しています。|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|分類子の値。 NULL 値は許可されません。||

## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。

## <a name="next-steps"></a>次のステップ
  
SQL Data Warehouse と並列データウェアハウスのすべてのカタログビューの一覧については、「 [SQL Data Warehouse および並列データウェアハウスのカタログビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)」を参照してください。 ワークロード分類子を作成するには、「[ワークロード分類子を作成](../../t-sql/statements/create-workload-classifier-transact-sql.md)する」を参照してください。 ワークロードの分類の詳細については、「SQL Data Warehouse[ワークロードの分類](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)と[ワークロードの重要度](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)」を参照してください。
