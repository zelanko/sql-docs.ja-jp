---
title: sp_indexes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_indexes_TSQL
- sp_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexes
ms.assetid: 25469e72-9d95-463f-912a-193471c8f5e2
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bebd14116b2b8cea0c1f0836571c994ba3fbd340
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spindexes-transact-sql"></a>sp_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたリモート テーブルに関するインデックス情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_indexes [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_db' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @table_server=] '*table_server*'  
 実行しているリンク サーバーの名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]表の情報を要求しています。 *table_server*は**sysname**、既定値はありません。  
  
 [ @table_name=] '*table_name*'  
 インデックス情報を提供する対象のリモート テーブルの名前です。 *table_name*は**sysname**、既定値は NULL です。 NULL の場合、指定したデータベースのすべてのテーブルが返されます。  
  
 [ @table_schema=] '*、table_schema、*'  
 テーブルのスキーマを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境では、これはテーブル所有者に相当します。 *table_schema、*は**sysname**、既定値は NULL です。  
  
 [ @table_catalog=] '*table_db*'  
 対象となるデータベースの名前を指定*table_name*が存在します。 *table_db*は**sysname**、既定値は NULL です。 NULL の場合、 *table_db*の既定値は**マスター**です。  
  
 [ @index_name=] '*index_name*'  
 情報を要求する対象のインデックスの名前です。 *インデックス*は**sysname**、既定値は NULL です。  
  
 [ @is_unique=] '*is_unique*'  
 情報を返す対象のインデックスの種類です。 *is_unique*は**ビット**NULL の場合、既定値は次の値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|1|一意なインデックスに関する情報を返します。|  
|0|一意でないインデックスに関する情報を返します。|  
|NULL|すべてのインデックスに関する情報を返します。|  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|TABLE_CAT|**sysname**|指定したテーブルが存在するデータベースの名前です。|  
|TABLE_SCHEM|**sysname**|テーブルのスキーマです。|  
|TABLE_NAME|**sysname**|リモート テーブルの名前です。|  
|NON_UNIQUE|**smallint**|インデックスが一意であるかどうかを示します。<br /><br /> 0 = 一意<br /><br /> 1 = 一意ではない|  
|INDEX_QUALIFER|**sysname**|インデックス所有者の名前です。 DBMS 製品の中には、テーブル所有者以外のユーザーでもインデックスを作成できるものがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は常に、同じ**TABLE_NAME**です。|  
|INDEX_NAME|**sysname**|インデックスの名前です。|  
|TYPE|**smallint**|インデックスの種類です。<br /><br /> 0 = テーブルの統計<br /><br /> 1 = クラスター化<br /><br /> 2 = ハッシュ化<br /><br /> 3 = その他|  
|ORDINAL_POSITION|**int**|インデックス内での列の序数です。 インデックスの最初の列は 1 です。 この列は、常に値を返します。|  
|COLUMN_NAME|**sysname**|返される TABLE_NAME の各列に対応する列名です。|  
|ASC_OR_DESC|**varchar**|データを並べ替えるための照合順序です。<br /><br /> A = 昇順<br /><br /> D = 降順<br /><br /> NULL = 適用なし<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は常に A を返します。|  
|CARDINALITY|**int**|テーブル内の行数またはインデックス内の一意な値の個数です。|  
|PAGES|**int**|インデックスまたはテーブルを格納するページ数です。|  
|FILTER_CONDITION|**nvarchar (**4000**)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では値は返されません。|  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例からのすべてのインデックス情報を返します、`Employees`のテーブル、`AdventureWorks2012`上のデータベース、`Seattle1`リンク サーバー。  
  
```  
EXEC sp_indexes @table_server = 'Seattle1',   
   @table_name = 'Employee',   
   @table_schema = 'HumanResources',  
   @table_catalog = 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [分散クエリ ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_linkedservers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
