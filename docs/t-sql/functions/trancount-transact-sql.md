---
title: "@@TRANCOUNT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TRANCOUNT_TSQL'
- '@@TRANCOUNT'
dev_langs: TSQL
helpviewer_keywords:
- '@@TRANCOUNT function'
- number of active transactions
- connections [SQL Server], active transactions
- active transactions
ms.assetid: b2638410-e410-4bd0-9b54-90096182b2b6
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: d9b10f8a7a8f14745765f611bc9ae33f36e7ff0a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40trancount-transact-sql"></a>&#x40;&#x40;です。TRANCOUNT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の接続で実行された BEGIN TRANSACTION ステートメントの数を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
@@TRANCOUNT  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 BEGIN TRANSACTION ステートメントをインクリメント@TRANCOUNTを 1 つです。 ROLLBACK TRANSACTION デクリメント @@TRANCOUNT ROLLBACK TRANSACTION を除く、0 に*savepoint_name*、これには影響しません@TRANCOUNTです。 COMMIT TRANSACTION または COMMIT WORK をデクリメント@TRANCOUNTを 1 つです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-showing-the-effects-of-the-begin-and-commit-statements"></a>A. BEGIN ステートメントと COMMIT ステートメントの影響を確認する  
 次の例は、入れ子になっている効果を示しています。`BEGIN`と`COMMIT`ステートメントがある、`@@TRANCOUNT`変数。  
  
```  
PRINT @@TRANCOUNT  
--  The BEGIN TRAN statement will increment the  
--  transaction count by 1.  
BEGIN TRAN  
    PRINT @@TRANCOUNT  
    BEGIN TRAN  
        PRINT @@TRANCOUNT  
--  The COMMIT statement will decrement the transaction count by 1.  
    COMMIT  
    PRINT @@TRANCOUNT  
COMMIT  
PRINT @@TRANCOUNT  
--Results  
--0  
--1  
--2  
--1  
--0  
```  
  
### <a name="b-showing-the-effects-of-the-begin-and-rollback-statements"></a>B. BEGIN ステートメントと ROLLBACK ステートメントの影響を確認する  
 次の例は、入れ子になっている効果を示しています。`BEGIN TRAN`と`ROLLBACK`ステートメントがある、`@@TRANCOUNT`変数。  
  
```  
PRINT @@TRANCOUNT  
--  The BEGIN TRAN statement will increment the  
--  transaction count by 1.  
BEGIN TRAN  
    PRINT @@TRANCOUNT  
    BEGIN TRAN  
        PRINT @@TRANCOUNT  
--  The ROLLBACK statement will clear the @@TRANCOUNT variable  
--  to 0 because all active transactions will be rolled back.  
ROLLBACK  
PRINT @@TRANCOUNT  
--Results  
--0  
--1  
--2  
--0  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [システム関数 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
