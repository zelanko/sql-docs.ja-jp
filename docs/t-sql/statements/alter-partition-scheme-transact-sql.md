---
title: "パーティション構成を変更 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION SCHEME
- ALTER_PARTITION_SCHEME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- ALTER PARTITION SCHEME statement
- partition schemes [SQL Server], modifying
- modifying partition schemes
- adding filegroups
- NEXT USED filegroups
ms.assetid: f01d6880-9800-4cfb-8d11-d4be21efc8ca
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 16b15945c8e6f56621516f16707d61be908e9972
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-partition-scheme-transact-sql"></a>ALTER PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パーティション構成にファイル グループを追加したり、パーティション構成の NEXT USED ファイル グループの指定を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER PARTITION SCHEME partition_scheme_name   
NEXT USED [ filegroup_name ] [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_scheme_name*  
 変更するパーティション構成の名前を指定します。  
  
 *filegroup_name*  
 パーティション構成により、NEXT USED とマークされるファイル グループを指定します。 ファイル グループを使用して作成される新しいパーティションを受け取ります。 つまり、 [ALTER PARTITION FUNCTION](../../t-sql/statements/alter-partition-function-transact-sql.md)ステートメントです。  
  
 パーティション構成では、1 つのファイル グループのみを NEXT USED として指定できます。 これには空でないファイル グループを指定できます。 場合*filegroup_name*が指定されていると、現在は NEXT USED ファイル グループはマークされていない*filegroup_name* NEXT USED とマークされます。 場合*filegroup_name*を指定すると、NEXT USED プロパティを含むファイル グループが既に存在して、NEXT USED プロパティでは、既存のファイル グループから転送*filegroup_name*です。  
  
 場合*filegroup_name*が指定されていない、NEXT USED プロパティを含むファイル グループが既に存在して、そのファイル グループが NEXT USED ファイル グループがないように、NEXT USED 状態を失う*partition_scheme_name*.  
  
 場合*filegroup_name*が指定されていない、NEXT USED ファイル グループはマークされていないと、ALTER PARTITION SCHEME で警告が返されます。  
  
## <a name="remarks"></a>解説  
 ALTER PARTITION SCHEME の対象となるファイル グループは、オンラインになっている必要があります。  
  
## <a name="permissions"></a>Permissions  
 次の権限を使って ALTER PARTITION SCHEME を実行できます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   パーティション構成が作成されたデータベースに対する CONTROL または ALTER 権限。  
  
-   パーティション構成が作成されたデータベースのサーバーに対する CONTROL SERVER または ALTER ANY DATABASE 権限。  
  
## <a name="examples"></a>使用例  
 次の例では、パーティション構成`MyRangePS1`とファイル グループ`test5fg`現在のデータベースに存在します。  
  
```  
ALTER PARTITION SCHEME MyRangePS1  
NEXT USED test5fg;  
```  
  
 ファイル グループ`test5fg`パーティション テーブルまたはインデックスを ALTER PARTITION FUNCTION ステートメントの結果としての追加パーティションが表示されます。  
  
## <a name="see-also"></a>参照  
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.partition_schemes と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [sys.data_spaces と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
