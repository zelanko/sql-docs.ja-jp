---
title: "sp_recompile (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_recompile_TSQL
- sp_recompile
dev_langs:
- TSQL
helpviewer_keywords:
- sp_recompile
ms.assetid: 6192ca87-febd-4075-8199-14b4fa609b8c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 200bf01ba1127281d5ff25b9c69f3616c4cf64bd
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="sprecompile-transact-sql"></a>sp_recompile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ストアド プロシージャ、トリガー、およびユーザー定義関数が次回実行時に再コンパイルされるようにします。 そのために、プロシージャ キャッシュから既存のプランを削除して、プロシージャまたはトリガーを次回実行するときに新しいプランが作成されるようにします。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] コレクションでは、SP:Recompile イベントではなく SP:CacheInsert イベントがログに記録されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
  
sp_recompile [ @objname = ] 'object'  
```  
  
## <a name="arguments"></a>引数  
 [ @objname=] '*オブジェクト*'  
 現在のデータベースにあるストアド プロシージャ、トリガー、テーブル、ビュー、またはユーザー定義関数の修飾名または非修飾名を指定します。 *オブジェクト*は**nvarchar (776)**、既定値はありません。 場合*オブジェクト*ストアド プロシージャ、トリガー、またはユーザー定義関数、ストアド プロシージャ、トリガーの名前を指定します。 または、次回実行する関数を再コンパイルされます。 場合*オブジェクト*テーブルまたはビュー、すべてのストアド プロシージャ、トリガーの名前を指定します。 または、次回実行されるテーブルまたはビューを参照するユーザー定義関数を再コンパイルされます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 0 以外の数値 (失敗)  
  
## <a name="remarks"></a>解説  
 sp_recompile は、現在のデータベース内でのみオブジェクトを検索します。  
  
 ストアド プロシージャ、トリガー、およびユーザー定義関数が使用するクエリは、コンパイル時にだけ最適化されます。 データベースにインデックスを追加したり、変更を加えたりすると、統計が変化するため、コンパイルされたストアド プロシージャ、トリガー、およびユーザー定義関数の効率が低下する場合があります。 そのテーブルに作用するストアド プロシージャやトリガーを再コンパイルすることにより、クエリを再び最適化できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動的にこれを行うことをお勧めときにストアド プロシージャ、トリガー、およびユーザー定義関数を再コンパイルします。  
  
## <a name="permissions"></a>アクセス許可  
 指定したオブジェクトに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`Customer` テーブルを対象とするストアド プロシージャ、トリガー、およびユーザー定義関数が次回実行時に再コンパイルされます。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_recompile N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
