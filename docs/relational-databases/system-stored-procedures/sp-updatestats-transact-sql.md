---
title: sp_updatestats (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: cd4eada4db6af75ad794efdba231407b23f79354
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560582"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内にあるすべてのユーザー定義テーブルと内部テーブルに対して UPDATE STATISTICS を実行します。  
  
 統計の更新の詳細についてを参照してください[統計の更新&#40;Transact SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)。 統計の詳細については、「[統計](../../relational-databases/statistics/statistics.md)」を参照してください。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="arguments"></a>引数  
 [ **@resample** =] **'を ' リサンプル**  
 指定する**sp_updatestats**のリサンプリング オプションが使用されます、[統計の更新](../../t-sql/statements/update-statistics-transact-sql.md)ステートメントです。 場合 **'リサンプル'** が指定されていない、 **sp_updatestats**既定のサンプリングを使用して統計情報を更新します。 **リサンプル**、 **varchar(8)** を既定値は [いいえ]  
  
## <a name="remarks"></a>コメント  
 **sp_updatestats**データベース内のすべてのユーザー定義および内部テーブルのすべてのキーワードを指定することで、統計の更新を実行します。 sp_updatestats は、その進行状況を示すメッセージが表示されます。 更新が完了すると、すべてのテーブルの統計が更新されたことをレポートします。  
  
 sp_updatestats は、無効化された非クラスター化インデックスの統計を更新しますが、無効化されたクラスター化インデックスの統計は更新しません。  
  
 ディスク ・ ベースのテーブルでは、 **sp_updatestats**に基づく統計情報を更新、 **modification_counter**内の情報、 **sys.dm_db_stats_properties**カタログを表示、少なくとも 1 つの行が変更されている統計情報を更新しています。 実行するときに、テーブルのメモリの最適化に関する統計情報が常に更新される**sp_updatestats**。 実行されません**sp_updatestats**以上必要です。  
  
 **sp_updatestats**ストアド プロシージャやその他のコンパイル済みコードの再コンパイルをトリガーすることができます。 ただし、 **sp_updatestats**だけ 1 つのクエリ プランが参照しているテーブルとそれらのインデックスの使用可能な再コンパイルする必要を発生可能性があります。 このような場合は、統計が更新されても再コンパイルの必要はありません。  
  
 データベース互換性レベルが 90 を実行する次の**sp_updatestats**特定の統計情報を最新の変更の設定は保持されません。 互換性レベルが 90 以上のデータベースは、sp_updatestats は特定の統計に対する最新の NORECOMPUTE オプションを保持します。 統計の更新の無効化および再有効化について詳しくは、「[統計](../../relational-databases/statistics/statistics.md)」をご覧ください。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **sysadmin**固定サーバー ロール、またはデータベースの所有権 (**dbo**)。  
  
## <a name="examples"></a>使用例  
 内のテーブルの統計情報を更新する例を次の[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [システム ストアド プロシージャ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
