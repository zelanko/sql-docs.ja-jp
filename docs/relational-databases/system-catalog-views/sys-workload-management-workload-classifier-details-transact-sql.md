---
description: sys.workload_management_workload_classifier_details (Transact-sql)
title: sys.workload_management_workload_classifier_details (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: 2135b567509ef9df5f3c8df7a317a9ea45b92ec7
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006418"
---
# <a name="sysworkload_management_workload_classifier_details-transact-sql"></a>sys.workload_management_workload_classifier_details (Transact-sql)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  各分類子の詳細を返します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|分類子の ID。  NULL 値は許可されません。|
|classifier_type|**sysname**|[Sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md)に参加できます。|`membername`</br>`wlm_label`</br>`wlm_context`</br>`start_time`</br>`end_time`|
|classifier_value|**sysname**|分類子の値。 NULL 値は許可されません。||

## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。

## <a name="next-steps"></a>次の手順
  
Azure Synapse Analytics と Parallel Data Warehouse のすべてのカタログビューの一覧については、「 [SQL Data Warehouse および並列データウェアハウスのカタログビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)」を参照してください。 ワークロード分類子を作成するには、「 [ワークロード分類子を作成](../../t-sql/statements/create-workload-classifier-transact-sql.md)する」を参照してください。 ワークロードの分類の詳細については、「Azure Synapse Analytics の[ワークロードの分類](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)と[ワークロードの重要度](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)」を参照してください。
