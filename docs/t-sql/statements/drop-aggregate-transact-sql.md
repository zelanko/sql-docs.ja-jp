---
title: "DROP AGGREGATE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AGGREGATE_TSQL
- DROP AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- aggregate functions [SQL Server], removing
- removing user-defined functions
- dropping user-defined functions
- user-defined functions [CLR integration]
- deleting user-defined functions
- DROP AGGREGATE statement
ms.assetid: 84ffc4e7-c451-4f1f-9a67-7fc3a120e53f
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a9fcab3dc576f15110bed8c1c82271731f326280
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義集計関数を現在のデータベースから削除します。 ユーザー定義集計関数を使用して作成された[CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、集計を削除します。  
  
 *schema_name*  
 ユーザー定義集計関数が所属しているスキーマの名前です。  
  
 *aggregate_name*  
 削除するユーザー定義集計関数の名前です。  
  
## <a name="remarks"></a>解説  
 削除対象のユーザー定義集計関数を参照するスキーマ バインドで作成された、ビュー、関数、またはストアド プロシージャが存在する場合は、DROP AGGREGATE は実行されません。  
  
## <a name="permissions"></a>Permissions  
 DROP AGGREGATE を実行するには、少なくとも、ユーザー定義集計関数が属するスキーマに対する ALTER 権限か、集計関数自体に対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、集計関数 `Concatenate` を削除します。  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>参照  
 [集計 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [ユーザー定義集計の作成](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  

