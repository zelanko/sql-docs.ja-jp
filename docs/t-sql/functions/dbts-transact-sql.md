---
title: "@@DBTS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 4a90150c55cdeb89788fdb86faf8aef8a1efdcd2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のデータベースの現在の **timestamp** 型の値を返します。 この timestamp はデータベース内で一意になることが保証されます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>戻り値の型
**varbinary**
  
## <a name="remarks"></a>解説  
@@DBTS現在のデータベースの最後に使用されたタイムスタンプ値を返します。 **timestamp** 列を含む行を追加または更新するたびに、タイムスタンプの新しい値が生成されます。
  
@@DBTS関数は、トランザクション分離レベルの変更による影響ありません。
  
## <a name="examples"></a>使用例  
次の例は、現在を返して**タイムスタンプ**から、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>参照
[構成関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/configuration-functions-transact-sql.md)  
[カーソルの同時実行 &#40;ODBC"&"#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  

