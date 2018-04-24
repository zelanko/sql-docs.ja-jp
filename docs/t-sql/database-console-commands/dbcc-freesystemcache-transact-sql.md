---
title: DBCC FREESYSTEMCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|database-console-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FREESYSTEMCACHE_TSQL
- DBCC_FREESYSTEMCACHE_TSQL
- DBCC FREESYSTEMCACHE
- FREESYSTEMCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- clearing unused cache entries
- DBCC FREESYSTEMCACHE statement
- unused cache entries
- releasing unused cache entries
- freeing unused cache entries
- cleaning unused cache entries
ms.assetid: 4b5c460b-e4ad-404a-b4ca-d65aba38ebbb
caps.latest.revision: 35
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8ea4e8c2c68785836c70cd8d36d59a4d14768088
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dbcc-freesystemcache-transact-sql"></a>DBCC FREESYSTEMCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

キャッシュ全体から未使用のすべてのキャッシュ エントリを解放します。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]では、未使用のキャッシュ エントリをバックグラウンドで事前にクリーンアップし、メモリを現在のエントリで使用できるようにします。 ただし、このコマンドを使用できるのは、キャッシュ全体または指定したリソース ガバナー プール キャッシュから未使用のキャッシュ エントリを手動で削除する場合です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
```sql
DBCC FREESYSTEMCACHE   
    ( 'ALL' [, pool_name ] )   
    [WITH   
    { [ MARK_IN_USE_FOR_REMOVAL ] , [ NO_INFOMSGS ]  }  
    ]  
```  
  
## <a name="arguments"></a>引数  
 ( 'ALL' [,*pool_name* ] )  
 ALL はサポートされるすべてのキャッシュを指定します。  
 *pool_name* は Resource Governor プール キャッシュを指定します。 このプールに関連付けられたエントリだけが解放されます。  
  
 MARK_IN_USE_FOR_REMOVAL  
 現在使用しているエントリが使用されなくなったら、それぞれのキャッシュから非同期に解放します。 DBCC FREESYSTEMCACHE WITH MARK_IN_USE_FOR_REMOVAL の実行後にキャッシュ内に作成された新しいエントリには影響ありません。  
  
 NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>Remarks  
DBCC FREESYSTEMCACHE を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのプラン キャッシュが消去されます。 プラン キャッシュが消去されると、後続のすべての実行プランが再コンパイルされ、場合によっては、クエリ パフォーマンスが一時的に急激に低下します。 プラン キャッシュ内のキャッシュストアが消去されるたびに、"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、'DBCC FREEPROCCACHE' 操作または 'DBCC FREESYSTEMCACHE' 操作により、'%s' キャッシュストア (プラン キャッシュの一部) のキャッシュストア フラッシュを %d 個検出しました。" という情報メッセージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに記録されます。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。

## <a name="result-sets"></a>結果セット  
DBCC FREESYSTEMCACHE は次のメッセージを返します。"DBCC の実行が完了しました。 DBCC がエラー メッセージを出力した場合は、システム管理者に相談してください。"
  
## <a name="permissions"></a>アクセス許可  
サーバーに対する ALTER SERVER STATE 権限が必要です。
  
## <a name="examples"></a>使用例  
  
### <a name="a-releasing-unused-cache-entries-from-a-resource-governor-pool-cache"></a>A. リソース ガバナー プール キャッシュから未使用のキャッシュ エントリを解放する  
次の例は、指定したリソース ガバナー リソース プール専用のキャッシュを消去する方法を示しています。
  
```sql
-- Clean all the caches with entries specific to the resource pool named "default".  
DBCC FREESYSTEMCACHE ('ALL', default);  
```  
  
### <a name="b-releasing-entries-from-their-respective-caches-after-they-become-unused"></a>B. エントリが使用されなくなったらそれぞれのキャッシュから解放する  
次の例では、MARK_IN_USE_FOR_REMOVAL 句を使用して、エントリが使用されなくなったら現在のすべてのキャッシュから解放します。
  
```sql
DBCC FREESYSTEMCACHE ('ALL') WITH MARK_IN_USE_FOR_REMOVAL;  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC FREEPROCCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freeproccache-transact-sql.md)  
[DBCC FREESESSIONCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-freesessioncache-transact-sql.md)  
[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)
  
  
