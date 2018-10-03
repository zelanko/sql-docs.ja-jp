---
title: sys.dm_tran_transactions_snapshot (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_transactions_snapshot
- dm_tran_transactions_snapshot
- sys.dm_tran_transactions_snapshot_TSQL
- dm_tran_transactions_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_transactions_snapshot dynamic management view
ms.assetid: 03f64883-07ad-4092-8be0-31973348c647
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d24ed8e2fdcf3a9475f999bf127eae3e8553dc86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704330"
---
# <a name="sysdmtrantransactionssnapshot-transact-sql"></a>sys.dm_tran_transactions_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  仮想テーブルを返します、 **sequence_number**の各スナップショット トランザクションときにアクティブなトランザクションを開始します。 このビューで返される情報を基に、次のことを確認できます。  
  
-   現在アクティブなスナップショット トランザクションの数。  
  
-   特定のスナップショット トランザクションで無視されるデータ変更。 スナップショット トランザクションの開始時にアクティブ状態にあったトランザクションによって行われるすべてのデータ変更は、そのトランザクションのコミット後も、スナップショット トランザクションでは無視されます。  
  
 たとえば、次の出力から**sys.dm_tran_transactions_snapshot**:  
  
```  
transaction_sequence_num snapshot_id snapshot_sequence_num  
------------------------ ----------- ---------------------  
59                       0           57  
59                       0           58  
60                       0           57  
60                       0           58  
60                       0           59  
60                       3           57  
60                       3           58  
60                       3           59  
60                       3           60  
```  
  
 `transaction_sequence_num` 列は、現在のスナップショット トランザクションのトランザクション シーケンス番号 (XSN) です。 2 つの出力を示しています。`59`と`60`します。 `snapshot_sequence_num` 列は、各スナップショット トランザクションの開始時にアクティブ状態にあったトランザクションのトランザクション シーケンス番号です。  
  
 この出力では、2 つのアクティブなスナップショット トランザクション (XSN-57 および XSN-58) の実行中に、スナップショット トランザクション XSN-59 が開始したことが示されています。 XSN-57 または XSN-58 でデータ変更が行われた場合、XSN-59 では変更が無視され、行バージョン管理によってトランザクション全体で一貫性のあるデータベース ビューが維持されます。  
  
 スナップショット トランザクション XSN-60 では、XSN-57 と XSN-58 だけでなく XSN-59 によって行われたデータ変更も無視されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_tran_transactions_snapshot  
```  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**transaction_sequence_num**|**bigint**|スナップショット トランザクションのトランザクション シーケンス番号 (XSN)。|  
|**snapshot_id**|**int**|それぞれのスナップショット ID[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、read committed を使用して開始行のバージョン管理します。 この ID を使用して、トランザクション全体で一貫性のあるデータベース ビューを生成し、行バージョンを使用する READ COMMITTED で実行される各クエリをサポートできます。|  
|**snapshot_sequence_num**|**bigint**|スナップショット トランザクションが開始したときに有効となっていたトランザクション シーケンス番号。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="remarks"></a>コメント  
 スナップショット トランザクションの開始時に、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の時点でアクティブになっているトランザクションがすべて記録します。 **sys.dm_tran_transactions_snapshot**すべての現在アクティブなスナップショット トランザクションは、この情報を報告します。  
  
 各トランザクションは、トランザクションの開始時に割り当てられたトランザクション シーケンス番号によって識別されます。 トランザクションは、BEGIN TRANSACTION または BEGIN WORK ステートメントが実行されたときに開始されますが、 トランザクション シーケンス番号は、BEGIN TRANSACTION または BEGIN WORK ステートメントの後、最初にデータにアクセスする [!INCLUDE[ssDE](../../includes/ssde-md.md)] ステートメントが実行されたときに[!INCLUDE[tsql](../../includes/tsql-md.md)]によって割り当てられます。 トランザクション シーケンス番号は 1 ずつ増加します。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

