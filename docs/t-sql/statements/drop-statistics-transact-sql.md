---
title: "DROP STATISTICS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/22/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP STATISTICS
- DROP_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing statistics
- column statistics [SQL Server]
- DROP STATISTICS statement
- deleting statistics
- dropping statistics
- table statistics [SQL Server]
- statistical information [SQL Server], removing
ms.assetid: 222806b7-4e45-445b-8cd0-bd5461f3ca4a
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 39d639b9d2ea2fc43cfd8389113ae7dad5611cc1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-statistics-transact-sql"></a>DROP STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースの指定されたテーブル内で、複数のコレクションの統計を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP STATISTICS table.statistics_name | view.statistics_name [ ,...n ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP STATISTICS [ schema_name . ] table_name.statistics_name   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *テーブル* | *ビュー*  
 統計を削除する対象となるターゲット テーブルまたはインデックス付きビューの名前です。 テーブルとビューの名前は、規則に従う必要があります[データベース識別子](../../relational-databases/databases/database-identifiers.md)です。 テーブルまたはビューの所有者名の指定は省略可能です。  
  
 *statistics_name*  
 削除する統計グループの名前です。 統計の名前は、識別子の規則に従っている必要があります。  
  
## <a name="remarks"></a>解説  
 統計を削除するときは注意が必要です。 統計を削除すると、クエリ オプティマイザーによって選択された実行プランに影響することがあります。  
  
 インデックスの統計を DROP STATISTICS で削除することはできません。 インデックスが存在する限り、統計は維持されます。  
  
 統計情報の表示の詳細については、次を参照してください。 [DBCC SHOW_STATISTICS & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 テーブルまたはビューに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-statistics-from-a-table"></a>A. テーブルの統計を削除します。  
 次の例では、2 つのテーブルの統計グループ (コレクション) を削除します。 `VendorCredit`の統計グループ (コレクション)、`Vendor`テーブルおよび`CustomerTotal`の統計情報 (コレクション)、`SalesOrderHeader`テーブルを削除します。  
  
```  
-- Create the statistics groups.  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS VendorCredit  
    ON Purchasing.Vendor (Name, CreditRating)  
    WITH SAMPLE 50 PERCENT  
CREATE STATISTICS CustomerTotal  
    ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
    WITH FULLSCAN;  
GO  
DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-dropping-statistics-from-a-table"></a>B. テーブルの統計を削除します。  
 次の例では、削除、`CustomerStats1`テーブルから統計`Customer`です。  
  
```  
DROP STATISTICS Customer.CustomerStats1;  
DROP STATISTICS dbo.Customer.CustomerStats1;  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [sys.stats_columns & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sp_autostats & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
  
  



