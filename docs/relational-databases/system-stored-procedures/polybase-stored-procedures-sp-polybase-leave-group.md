---
title: sp_polybase_leave_group (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30370777811d51970ec94647715395285ad9c86f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sppolybaseleavegroup-transact-sql"></a>sp_polybase_leave_group (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  スケール アウト計算 PolyBase グループからは、SQL Server のインスタンスを削除します。 
 
 SQL Server のインスタンスが必要、 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)機能がインストールされています。  PolyBase では、Hadoop と Azure blob ストレージなどの SQL Server 以外のデータ ソースの統合を使用できます。 関連項目[sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>権限  
 CONTROL SERVER 権限が必要です。  
  
## <a name="remarks"></a>解説  
 コンピューティング ノードは、グループからのみ削除できます。  
  
 ストアド プロシージャを実行すた後には、コンピューターに PolyBase エンジンと PolyBase データ移動のサービスを再起動します。 確認するヘッド ノードで次の DMV を実行します。 **sys.dm_exec_compute_nodes**です。  
  
## <a name="example"></a>例  
 例では、PolyBase グループから、現在のコンピューターを削除します。  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>参照  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
