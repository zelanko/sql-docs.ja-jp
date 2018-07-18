---
title: sp_polybase_leave_group (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: polybase
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
caps.latest.revision: 11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8ad3a202ff910d19ea70192eb9cc5e114a8a4cb9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984211"
---
# <a name="sppolybaseleavegroup-transact-sql"></a>sp_polybase_leave_group (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  スケール アウト計算 PolyBase グループからは、SQL Server のインスタンスを削除します。 
 
 SQL Server インスタンスが必要、 [PolyBase ガイド](../../relational-databases/polybase/polybase-guide.md)機能をインストールします。  PolyBase では、Hadoop と Azure blob ストレージなどの SQL Server 以外のデータ ソースの統合を使用できます。 参照してください[sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 コンピューティング ノードは、グループからのみ削除できます。  
  
 ストアド プロシージャを実行すた後には、コンピューターに PolyBase エンジンと PolyBase データ移動のサービスを再起動します。 確認するヘッド ノードで次の DMV を実行する: **sys.dm_exec_compute_nodes**します。  
  
## <a name="example"></a>例  
 例では、PolyBase グループから、現在のコンピューターを削除します。  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>参照  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
