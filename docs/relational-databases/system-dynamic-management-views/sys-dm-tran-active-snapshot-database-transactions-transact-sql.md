---
title: sys.dm_tran_active_snapshot_database_transactions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_active_snapshot_database_transactions_TSQL
- dm_tran_active_snapshot_database_transactions
- sys.dm_tran_active_snapshot_database_transactions
- dm_tran_active_snapshot_database_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_active_snapshot_database_transactions dynamic management view
ms.assetid: 55b83f9c-da10-4e65-9846-f4ef3c0c0f36
caps.latest.revision: 55
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 29e7ce6fb11c5d10378ed0ec2e905706837f5b3f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmtranactivesnapshotdatabasetransactions-transact-sql"></a>sys.dm_tran_active_snapshot_database_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、この動的管理ビューは、すべてのアクティブなトランザクションを生成するか可能性のある行のバージョンへのアクセスの仮想テーブルを返します。 トランザクションは、次の条件を 1 つ以上満たします。  
  
-   ALLOW_SNAPSHOT_ISOLATION データベース オプションと READ_COMMITTED_SNAPSHOT データベース オプションのいずれかまたは両方が ON に設定されている場合、  
  
    -   行のバージョン管理を使用するスナップショット分離レベルまたは READ COMMITTED 分離レベルで実行されているトランザクションごとに、1 行のデータが存在する。  
  
    -   現在のデータベースに行バージョンを作成するトランザクションごとに、1 行のデータが存在する。 たとえば、現在のデータベース内の行を更新または削除することによって行バージョンを生成するトランザクションがこれに該当します。  
  
-   トリガーが起動される場合、トリガーが実行されるトランザクションごとに 1 行のデータが存在する。  
  
-   オンライン インデックス処理中に、インデックスを作成しているトランザクションごとに 1 行のデータが存在する。  
  
-   複数のアクティブな結果セット (MARS) セッションが有効な場合、行バージョンにアクセスしているトランザクションごとに 1 行のデータが存在する。  
  
 この動的管理ビューにシステム トランザクションは含まれません。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_tran_active_snapshot_database_transactions**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_tran_active_snapshot_database_transactions  
```  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**transaction_id**|**bigint**|トランザクションに割り当てられている一意な識別番号。 トランザクション ID は、主にロック操作でトランザクションを識別するときに使用します。|  
|**transaction_sequence_num**|**bigint**|トランザクション シーケンス番号。 トランザクションの開始時に割り当てられた一意なシーケンス番号です。 バージョン レコードを生成せず、スナップショット スキャンを行わないトランザクションには、トランザクション シーケンス番号は割り当てられません。|  
|**commit_sequence_num**|**bigint**|トランザクションが完了 (コミットまたは停止) したことを示すシーケンス番号。 アクティブなトランザクションの場合、値は NULL になります。|  
|**is_snapshot**|**int**|0 = スナップショット分離トランザクションではありません。<br /><br /> 1 = スナップショット分離トランザクションです。|  
|**session_id**|**int**|トランザクションを開始したセッションの ID。|  
|**first_snapshot_sequence_num**|**bigint**|スナップショットが取得されたときにアクティブになっていたトランザクションの、最小トランザクション シーケンス番号。 スナップショット トランザクションの実行時には、その時点でアクティブなすべてのトランザクションのスナップショットが取得されます。 スナップショット以外のトランザクションの場合、この列は 0 になります。|  
|**max_version_chain_traversed**|**int**|トランザクション全体で一貫性のあるバージョンを検索するためにスキャンされるバージョン チェーンの最大長。|  
|**average_version_chain_traversed**|**real**|スキャンされるバージョン チェーン内の行バージョンの平均数。|  
|**elapsed_time_seconds**|**bigint**|トランザクションがトランザクション シーケンス番号を取得してからの経過時間。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="remarks"></a>解説  
 **sys.dm_tran_active_snapshot_database_transactions**トランザクション シーケンス番号 (XSN) が割り当てられているトランザクションを報告します。 XSN は、トランザクションが最初にバージョン ストアにアクセスしたときに割り当てられます。 行のバージョン管理を使用するスナップショット分離または READ COMMITTED 分離が有効なデータベースにおいて、XSN がトランザクションに割り当てられるときの例を次に示します。  
  
-   トランザクションが SERIALIZABLE 分離レベルで実行されている場合は、トランザクションで UPDATE 操作などのステートメントが最初に実行されるときに XSN が割り当てられ、これによって行バージョンが作成されます。  
  
-   トランザクションがスナップショット分離で実行されている場合は、SELECT 操作などの任意の DML (データ操作言語) ステートメントが実行されるときに XSN が割り当てられます。  
  
 トランザクション シーケンス番号は、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスでトランザクションが開始されるたびに増分されます。  
  
## <a name="examples"></a>使用例  
 次の例では、4 つの同時実行トランザクションが存在するテスト シナリオを使用します。これらのトランザクションはそれぞれトランザクション シーケンス番号 (XSN) で識別され、ALLOW_SNAPSHOT_ISOLATION オプションと READ_COMMITTED_SNAPSHOT オプションが ON に設定されているデータベース内で実行されます。 実行されるトランザクションは次のとおりです。  
  
-   XSN-57。SERIALIZABLE 分離での更新操作です。  
  
-   XSN-58 では、xsn-57 と同じです。  
  
-   Xsn-59 がスナップショット分離下で選択操作です。  
  
-   XSN-60。XSN-59 と同じです。  
  
 次のクエリを実行します。  
  
```  
SELECT   
    transaction_id,  
    transaction_sequence_num,  
    commit_sequence_num,  
    is_snapshot session_id,  
    first_snapshot_sequence_num,  
    max_version_chain_traversed,  
    average_version_chain_traversed,  
    elapsed_time_seconds  
  FROM sys.dm_tran_active_snapshot_database_transactions;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
transaction_id  transaction_sequence_num  commit_sequence_num  
--------------  ------------------------  -------------------  
9295            57                        NULL  
9324            58                        NULL  
9387            59                        NULL  
9400            60                        NULL  
  
is_snapshot  session_id   first_snapshot_sequence_num  
-----------  -----------  ---------------------------  
0            54           0  
0            53           0  
1            52           57  
1            51           57  
  
max_version_chain_traversed  average_version_chain_traversed  
---------------------------  -------------------------------  
0                            0  
0                            0  
1                            1  
1                            1  
  
elapsed_time_seconds  
--------------------  
419  
397  
359  
333  
```  
  
 次の情報を評価の結果を**sys.dm_tran_active_snapshot_database_transactions**:  
  
-   XSN-57: このトランザクションがスナップショット分離下で実行されていないため、`is_snapshot`値および`first_snapshot_sequence_num`は`0`します。 `transaction_sequence_num` 1 つまたは両方の ALLOW_SNAPSHOT_ISOLATION または READ_COMMITTED_SNAPSHOT データベース オプションが ON であるために、このトランザクションにトランザクション シーケンス番号が割り当てられたことを示します。  
  
-   XSN-58: このトランザクションはスナップショット分離で実行されていないので、XSN-57 と同じ説明が当てはまります。  
  
-   XSN-59: これは、スナップショット分離で実行されている最初のアクティブなトランザクションです。 によって示される、このトランザクションは、xsn-57 より前にコミット済みのデータを読み取る`first_snapshot_sequence_num`です。 このトランザクションの出力では、1 行にスキャンされるバージョン チェーンの最大長が `1` で、アクセスした行ごとに平均で `1` つのバージョンがスキャンされていることも示されています。 これは、トランザクション XSN-57、XSN-58、および XSN-60 では行が変更されずコミットされていないことを表します。  
  
-   XSN-60: これは、スナップショット分離で実行されている 2 番目のトランザクションです。 出力では、XSN-59 と同じ情報が示されます。  
  
## <a name="see-also"></a>参照  
 [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


