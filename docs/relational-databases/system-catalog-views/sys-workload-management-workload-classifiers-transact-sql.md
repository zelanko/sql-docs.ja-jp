---
title: sys.workload_management_workload_classifiers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2019
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 3b023654728375aee76bfb0c4434a8413dc81e7d
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582565"
---
# <a name="sysworkloadmanagementworkloadclassifiers-transact-sql-preview"></a>sys.workload_management_workload_classifiers (TRANSACT-SQL) (プレビュー)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

> [!Note]
> ワークロードの分類は、SQL Data Warehouse Gen2 のプレビューで使用できます。 ワークロード管理の分類と重要度のプレビューは 2019 年 4 月 9 日、またはそれ以降のリリース日でビルドです。  ユーザーは、ワークロード管理のテストの前にこの日付よりもビルドの使用を避ける必要があります。  ビルドがワークロードの管理ができるかどうかを決定、実行 select @@version SQL Data Warehouse インスタンスに接続されている場合。

 ワークロードの分類子の詳細を返します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|分類器の一意の ID。 値が許容されません。||
group_name|**sysname**|分類器は、ワークロード グループの名前が割り当てられます。 NULL 値は許可されません。 |静的リソース クラス</br>staticrc10</br>staticrc20</br>staticrc30</br>staticrc40</br>staticrc50</br>staticrc60</br>staticrc70</br>staticrc80 </br> </br>動的リソース クラス</br>smallrc</br>mediumrc</br>largerc</br>xlargerc|
NAME|**sysname**|分類子の名前です。 インスタンスに対して一意である必要があります。 NULL 値は許可されません。||
|importance|**sysname**|このワークロード グループと共有リソースのワークロード グループ間での要求の相対的な重要度です。  分類子で指定された重要度は、ワークロード グループの重要度の設定をオーバーライドします。|低、below_normal、normal、しなく、高 |
|create_time|**datetime**|分類子が作成された時刻。 NULL 値は許可されません。||
modify_time|**datetime**|分類子の最終変更時刻。 NULL 値は許可されません。||
is_enabled|**bit**|分類子が有効か無効かどうかが表示されます。 既定で有効です。 NULL 値は許可されません。|0 = 分類子が有効になっていません </br> 1 = 分類子が有効になっています。|
|&nbsp;||||
  
## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。

## <a name="next-steps"></a>次のステップ

 SQL Data Warehouse と Parallel Data Warehouse のすべてのカタログ ビューの一覧は、次を参照してください。 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)します。 ワークロードの分類器を作成するを参照してください。[ワークロードの分類器を作成する](../../t-sql/statements/create-workload-classifier-transact-sql.md)します。 ワークロードの分類の詳細については、次を参照してください[SQL データ ウェアハウス ワークロードの分類。](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
