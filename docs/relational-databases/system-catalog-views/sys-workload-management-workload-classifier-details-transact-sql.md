---
title: sys.workload_management_workload_classifier_details (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 05/01/2019
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
ms.openlocfilehash: f9314b9297af7e8156ed86b2bfa2dadd18896bb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061291"
---
# <a name="sysworkloadmanagementworkloadclassifierdetails-transact-sql"></a>sys.workload_management_workload_classifier_details (TRANSACT-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  各分類器の詳細を返します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|分類子の ID。 結合可能な[sys.workload_management_workload_classifiers](sys-workload-management-workload-classifiers-transact-sql.md)します。 NULL 値は許可されません。|
|classifier_type|**sysname**|分類が実行されているエンティティ。 NULL 値は許可されません。|メンバー名|
|classifier_value|**sysname**|分類子の値。 NULL 値は許可されません。||

## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。

## <a name="next-steps"></a>次のステップ
  
 SQL Data Warehouse と Parallel Data Warehouse のすべてのカタログ ビューの一覧は、次を参照してください。 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)します。 ワークロードの分類器を作成するを参照してください。[ワークロードの分類器を作成する](../../t-sql/statements/create-workload-classifier-transact-sql.md)します。 ワークロードの分類の詳細については、SQL Data Warehouse を参照してください[ワークロード分類](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)と[ワークロードの重要度。](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
