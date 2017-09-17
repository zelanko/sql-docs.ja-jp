---
title: "SET LOCK_TIMEOUT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOCK_TIMEOUT_TSQL
- SET_LOCK_TIMEOUT_TSQL
- SET LOCK_TIMEOUT
- LOCK_TIMEOUT
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- releasing locks
- LOCK_TIMEOUT option
- SET LOCK_TIMEOUT statement
- locking [SQL Server], time-outs
- wait time for lock releases [SQL Server]
ms.assetid: dd0c389e-956d-435e-bf71-e16624a0a215
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 754242a86367b07b98caa9f70f457b70d0840075
ms.openlocfilehash: 3de86c7f33afd6e708ad8e773470ec650e092d2c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="set-locktimeout-transact-sql"></a>SET LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ロックを解除するため、ステートメントが待機するミリ秒数を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET LOCK_TIMEOUT timeout_period  
```  
  
## <a name="arguments"></a>引数  
 *timeout_period*  
 前に渡されるミリ秒数[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ロック エラーが返されます。 値が -1 (既定値) の場合は、タイムアウトは設定されず、無期限に待機することになります。  
  
 ロックの待ち時間がタイムアウト値を超えると、エラーが返されます。 値が 0 の場合は、待ち時間はなく、ロックがかかるとすぐにメッセージが返されます。  
  
## <a name="remarks"></a>解説  
 この設定には、接続の開始時に -1 が割り当てられます。 この値が変更されると、その接続の残りの期間については、新しい設定が適用されます。  
  
 SET LOCK_TIMEOUT は、解析時ではなく実行時に設定されます。  
  
 SET オプションの代わりに READPAST ロック ヒントを使用できます。  
  
 CREATE DATABASE、ALTER DATABASE、および DROP DATABASE ステートメントでは、SET LOCK_TIMEOUT の設定は無視されます。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-set-the-lock-timeout-to-1800-milliseconds"></a>A: ロックのタイムアウトを 1,800 ミリ秒に設定します。  
 次の例では、ロックのタイムアウト値を設定`1800`(ミリ秒)。  
  
```sql  
SET LOCK_TIMEOUT 1800;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-set-the-lock-timeout-to-wait-forever-for-a-lock-to-be-released"></a>B. ロックが解放されるを無限に待機するロックのタイムアウトを設定します。  
 次の例では、無期限に待機し、無期限にロックのタイムアウトを設定します。 これは、各接続の先頭には既に設定されている既定の動作です。  
  
```sql  
SET LOCK_TIMEOUT -1;  
```  
  
 次の例では、ロックのタイムアウト値を設定`1800`(ミリ秒)。 このリリースで[!INCLUDE[ssDW](../../includes/ssdw-md.md)]ステートメントを正常に解析されますが、1800 値を無視するは、および引き続き既定の動作を使用します。  
  
```sql  
SET LOCK_TIMEOUT 1800;  
```  
  
## <a name="see-also"></a>参照  
 [@@LOCK_TIMEOUT &#40;Transact-SQL&#41;](../../t-sql/functions/lock-timeout-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  


