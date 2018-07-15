---
title: sys.dm_pdw_request_steps (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/01/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5a6fbf843d3a9aca9172a5ab6ea828a0c0b0a40a
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926843"
---
# <a name="sysdmpdwrequeststeps-transact-sql"></a>sys.dm_pdw_request_steps (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  特定の要求を作成またはでクエリするすべてのステップに関する情報を保持[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]します。 これには、クエリのステップごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|request_id と step_index は、このビューのキーを構成します。<br /><br /> 要求に関連付けられている一意の数値 id です。|Request_id 内を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|step_index|**int**|request_id と step_index は、このビューのキーを構成します。<br /><br /> この手順の要求を構成する手順のシーケンス内の位置。|ステップを含む要求に対して (n 1) に 0 を返します。|  
|operation_type|**nvarchar(35)**|この手順で表される操作の種類。|**DMS のクエリ プランの操作:** 'ReturnOperation'、'PartitionMoveOperation'、'MoveOperation'、'BroadcastMoveOperation'、'ShuffleMoveOperation'、'TrimMoveOperation'、'CopyOperation'、'DistributeReplicatedTableMoveOperation'<br /><br /> **SQL クエリ プランの操作:** 'OnOperation'、'RemoteOperation'<br /><br /> **その他のクエリ プランの操作:** 'MetaDataCreateOperation'、'RandomIDOperation'<br /><br /> **読み取りの外部の処理:** 'HadoopShuffleOperation'、'HadoopRoundRobinOperation'、'HadoopBroadcastOperation'<br /><br /> **MapReduce の外部の処理:** 'HadoopJobOperation'、'HdfsDeleteOperation'<br /><br /> **書き込みのための外部の処理:** 'ExternalExportDistributedOperation'、'ExternalExportReplicatedOperation'、'ExternalExportControlOperation'<br /><br /> 詳細についてを参照してください「についてのクエリ プラン」、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]します。|  
|distribution_type|**nvarchar(32)**|この手順が使用される分布の型。|'AllNodes'、'AllDistributions'、'AllComputeNodes'、'ComputeNode'、'配布'、'SubsetNodes'、'SubsetDistributions'、'指定されていません'|  
|location_type|**nvarchar(32)**|ステップが実行されています。|' Compute'、'コントロール'、'DMS'|  
|status|**nvarchar(32)**|この手順の状態です。|保留中、実行中、完了、失敗、UndoFailed、PendingCancel、キャンセル、元に戻す、中止されました|  
|error_id|**nvarchar(36)**|存在する場合は、このステップに関連付けられているエラーの一意の id。|Error_id を参照してください。 [sys.dm_pdw_errors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)します。 エラーが発生していない場合は NULL です。|  
|start_time|**datetime**|ステップの実行開始時刻。|小さいまたは現在の時刻と等しい、大きいか等しい end_compile_time が、この手順が属している、クエリのです。 クエリの詳細については、次を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|end_time|**datetime**|このステップ実行を完了したが取り消された場合、または失敗したの時間です。|小さいまたは現在の時刻に等しいと大きいか等しい start_time します。 手順については、現在実行中に NULL を設定するか、キューに登録します。|  
|total_elapsed_time|**int**|クエリのステップが実行された、ミリ秒単位で時間の合計サイズ。|0 ～ start_time と end_time の間の違いです。 手順についてはキューに置かれた 0 を返します。<br /><br /> Total_elapsed_time では、整数の最大値を超えると、total_elapsed_time 引き続き、最大値になります。 この状態が「、最大値を超過しました」警告を生成します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|row_count|**bigint**|行の合計数は、変更されたか、この要求によって返されます。|変更またはデータを返すしていないするステップの 0 を返します。 影響を受ける行の数をそれ以外の場合です。|  
|command|**nvarchar (4000)**|このステップのコマンドの完全なテキストを保持します。|ステップの任意の有効な要求文字列。 操作の種類 MetaDataCreateOperation の時に NULL です。 4,000 文字より長い場合に切り捨てられます。|  
  
 このビューで保持される最大行数については、システム ビューの最大値、「最小値と最大値」セクションを参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]します。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
