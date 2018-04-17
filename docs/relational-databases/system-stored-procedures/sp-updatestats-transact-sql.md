---
title: sp_updatestats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0ba0a2d4ccfe5250e75b113acd3b407fc4b50c9b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内にあるすべてのユーザー定義テーブルと内部テーブルに対して UPDATE STATISTICS を実行します。  
  
 統計の更新の詳細については、次を参照してください。 [UPDATE STATISTICS &#40;TRANSACT-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)です。 統計の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="arguments"></a>引数  
 [ **@resample** =] **'resample'**  
 指定する**sp_updatestats**の RESAMPLE オプションを使用、 [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md)ステートメントです。 場合**'resample'**が指定されていない**sp_updatestats**既定のサンプリングを使用して統計を更新します。 **resample**は**varchar (8)**で、既定値は no です。  
  
## <a name="remarks"></a>解説  
 **sp_updatestats**データベース内のすべてのユーザー定義および内部テーブルに、ALL キーワードを指定することによって、統計を更新を実行します。 sp_updatestats は、その進行状況を示すメッセージが表示されます。 更新が完了すると、すべてのテーブルの統計が更新されたことをレポートします。  
  
 sp_updatestats は、無効化された非クラスター化インデックスの統計を更新しますが、無効化されたクラスター化インデックスの統計は更新しません。  
  
 ディスク ベース テーブルに対する**sp_updatestats**に基づいて統計を更新、 **modification_counter**内の情報、 **sys.dm_db_stats_properties**カタログ ビュー、少なくとも 1 つの行が変更されて統計を更新しています。 メモリ最適化テーブルの統計では、必ず実行するときに**sp_updatestats**です。 実行されません**sp_updatestats**以上必要です。  
  
 **sp_updatestats**ストアド プロシージャやその他のコンパイル済みコードの再コンパイルをトリガーすることができます。 ただし、 **sp_updatestats** 1 つのクエリ プランが参照されているテーブルおよびそのインデックスに対するだけの場合、再コンパイルをされない可能性があります。 このような場合は、統計が更新されても再コンパイルの必要はありません。  
  
 データベース互換性レベルが 90、実行の下で**sp_updatestats**は特定の統計に対する最新の NORECOMPUTE 設定は保持されません。 互換性レベルが 90 以上のデータベースは、sp_updatestats は特定の統計に対する最新の NORECOMPUTE オプションを保持します。 統計の更新の無効化および再有効化について詳しくは、「[統計](../../relational-databases/statistics/statistics.md)」をご覧ください。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **sysadmin**固定サーバー ロール、またはデータベースの所有権 (**dbo**)。  
  
## <a name="examples"></a>使用例  
 次の例のテーブルの統計を更新する、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE SET のオプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [システム ストアド プロシージャ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
