---
title: "sys.dm_tran_current_transaction (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_current_transaction
- sys.dm_tran_current_transaction_TSQL
- dm_tran_current_transaction_TSQL
- dm_tran_current_transaction
dev_langs: TSQL
helpviewer_keywords: sys.dm_tran_current_transaction dynamic management view
ms.assetid: 75d5697d-b390-4963-99b8-fa0b4244a40c
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 55c0179a2c589a8dad2d178693593a943adba445
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmtrancurrenttransaction-transact-sql"></a>sys.dm_tran_current_transaction (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のセッションにおけるトランザクションの状態情報を表す 1 行を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_tran_current_transaction**です。  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_tran_current_transaction  
```  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**transaction_id**|**bigint**|現在のスナップショットのトランザクション ID。|  
|**transaction_sequence_num**|**bigint**|レコード バージョンを生成するトランザクションのシーケンス番号。|  
|**transaction_is_snapshot**|**bit**|スナップショット分離の状態。 トランザクションがスナップショット分離に基づいて開始された場合、この値は 1 です。 それ以外の場合、値は 0 です。|  
|**first_snapshot_sequence_num**|**bigint**|スナップショットが取得されたときにアクティブになっていたトランザクションの、最小トランザクション シーケンス番号。 スナップショット トランザクションの実行時には、その時点でアクティブなすべてのトランザクションのスナップショットが取得されます。 スナップショット以外のトランザクションの場合、この列は 0 になります。|  
|**last_transaction_sequence_num**|**bigint**|グローバル シーケンス番号。 この値は、システムにより生成された最後のトランザクション シーケンス番号を表します。|  
|**first_useful_sequence_num**|**bigint**|グローバル シーケンス番号。 この値は、行バージョンをバージョン ストアに保持する必要があるトランザクションの、最も古いトランザクション シーケンス番号を表します。 これより前のトランザクションで作成された行バージョンは削除できます。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="examples"></a>使用例  
 次の例では、4 つの同時実行トランザクションが存在するテスト シナリオを使用します。これらのトランザクションはそれぞれトランザクション シーケンス番号 (XSN) で識別され、ALLOW_SNAPSHOT_ISOLATION オプションと READ_COMMITTED_SNAPSHOT オプションが ON に設定されているデータベース内で実行されます。 実行されるトランザクションは次のとおりです。  
  
-   XSN-57。SERIALIZABLE 分離での更新操作です。  
  
-   XSN-58 では、xsn-57 と同じです。  
  
-   XSN-59。スナップショット分離での選択操作です。  
  
-   Xsn-60 では、xsn-59 と同じです。  
  
 次のクエリは各トランザクションのスコープ内で実行されます。  
  
```  
SELECT   
    transaction_id  
   ,transaction_sequence_num  
   ,transaction_is_snapshot  
   ,first_snapshot_sequence_num  
   ,last_transaction_sequence_num  
   ,first_useful_sequence_num  
  FROM sys.dm_tran_current_transaction;  
```  
  
 ここでは、xsn-59 の結果です。  
  
```  
transaction_id       transaction_sequence_num transaction_is_snapshot  
-------------------- ------------------------ -----------------------  
9387                 59                       1                         
  
first_snapshot_sequence_num last_transaction_sequence_num  
--------------------------- -----------------------------  
57                               61                        
  
first_useful_sequence_num  
-------------------------  
57  
```  
  
 この出力は、XSN-59 がスナップショット トランザクションであり、最初のトランザクションとして XSN-57 を使用することと、XSN-57 が XSN-59 の開始時にアクティブであったことを示しています。 つまり、XSN-59 では、トランザクション シーケンス番号が XSN-57 より低いトランザクションによってコミットされたデータが読み取られます。  
  
 XSN-57 の結果を次に示します。  
  
```  
transaction_id       transaction_sequence_num transaction_is_snapshot  
-------------------- ------------------------ -----------------------  
9295                 57                       0  
  
first_snapshot_sequence_num last_transaction_sequence_num  
--------------------------- -----------------------------  
NULL                        61  
  
first_useful_sequence_num  
-------------------------  
57  
```  
  
 Xsn-57 がスナップショット トランザクションではないため`first_snapshot_sequence_num`は`NULL`します。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


