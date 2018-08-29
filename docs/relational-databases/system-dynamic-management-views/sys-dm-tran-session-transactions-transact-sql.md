---
title: sys.dm_tran_session_transactions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_tran_session_transactions
- sys.dm_tran_session_transactions
- sys.dm_tran_session_transactions_TSQL
- dm_tran_session_transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_session_transactions dynamic management view
ms.assetid: c7157491-58c2-49fe-87d7-0c9723113adf
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9994ce833a06fa42585a0eae8539308abc3393e5
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43078955"
---
# <a name="sysdmtransessiontransactions-transact-sql"></a>sys.dm_tran_session_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  関連付けられたトランザクションとセッションの相関関係情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_tran_session_transactions**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_id|**int**|トランザクションを実行中のセッションの ID。|  
|transaction_id|**bigint**|トランザクションの ID。|  
|transaction_descriptor|**binary(8)**|使用されるトランザクション識別子[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ドライバーと通信するとき。|  
|enlist_count|**int**|トランザクションで処理中のセッション内にあるアクティブな要求数。|  
|is_user_transaction|**bit**|1 = ユーザーの要求によって開始されたトランザクション。<br /><br /> 0 = システム トランザクション。|  
|is_local|**bit**|1 = ローカル トランザクション。<br /><br /> 0 = 分散トランザクション、または参加しているバインドされたセッションのトランザクション。|  
|is_enlisted|**bit**|1 = 参加している分散トランザクション。<br /><br /> 0 = 参加している分散トランザクションではない。|  
|is_bound|**bit**|1 = トランザクションは、バインドされたセッションを介したセッションでアクティブです。<br /><br /> 0 = トランザクションは、バインドされたセッションを介したセッションでアクティブではありません。|  
|open_transaction_count||各セッションの開いているトランザクションの数。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="remarks"></a>コメント  
 バインドされたセッションと分散トランザクションを使用すると、1 つ以上のセッションでトランザクションを実行できます。 このような場合、sys.dm_tran_session_transactions では、同じ transaction_id を持つ複数の行が表示されます。つまり、トランザクションが実行中のセッションごとに 1 行ずつ表示されます。  
  
 複数のアクティブな結果セット (MARS) を使用する自動コミット モードで複数の要求を実行すると、1 つのセッションに複数のアクティブなトランザクションを含めることができます。 このような場合、sys.dm_tran_session_transactions では、同じ session_id を持つ複数の行が表示されます。つまり、そのセッションで実行中のトランザクションごとに 1 行ずつ表示されます。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


