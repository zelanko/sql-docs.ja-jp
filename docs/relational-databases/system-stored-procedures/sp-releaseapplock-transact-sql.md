---
title: "sp_releaseapplock (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs: TSQL
helpviewer_keywords: sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65c9665e3733ad90d46a2576790953f6f8be9fb8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreleaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アプリケーション リソースのロックを解放します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ @Resource=] '*resource_name*'  
 クライアント アプリケーションによって指定されたロック リソース名を指定します。 アプリケーション側で、リソースが一意になるように管理しなければなりません。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は**nvarchar (255)**既定値はありません。 *resource_name*はバイナリ比較、つまり現在のデータベースの照合順序の設定に関係なく大文字小文字を区別します。  
  
 [ @LockOwner=] '*lock_owner*'  
 これは、ロックの所有者である、 *lock_owner*ロックが要求されたときの値します。 *lock_owner*は**nvarchar (32)**です。 値を指定できます**トランザクション**(既定) または**セッション**です。 ときに、 *lock_owner*値は**トランザクション**により、既定または明示的に指定すると、sp_getapplock 必要がありますから実行するトランザクション内で。  
  
 [ @DbPrincipal=] '*database_principal*'  
 データベース内のオブジェクトに対する権限を持つユーザー、ロール、またはアプリケーション ロールを指定します。 関数の呼び出し元のメンバーである必要があります*database_principal*、関数を呼び出すに dbo、または db_owner 固定データベース ロール。 既定値は public です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 \>= 0 (成功) または < 0 (失敗)  
  
|値|結果|  
|-----------|------------|  
|0|ロックの解放が正しく行われました。|  
|-999|パラメーターの検証エラーまたはその他の呼び出しエラーです。|  
  
## <a name="remarks"></a>解説  
 アプリケーションで、同じロック リソースに対して sp_getapplock が複数回呼び出される場合は、同じ回数だけ sp_releaseapplock を呼び出して、ロックを解放する必要があります。  
  
 何かの理由でサーバーがシャットダウンすると、ロックは解放されます。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、リソースの現在のトランザクションに関連付けられているロックを解放`Form1`で、`AdventureWorks2012`データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [APPLOCK_MODE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
