---
title: sp_columns_ex (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_columns_ex
- sp_columns_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns_ex
ms.assetid: c12ef6df-58c6-4391-bbbf-683ea874bd81
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 034955aad1d0ad90f78b36704c6d202a23176ad2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spcolumnsex-transact-sql"></a>sp_columns_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したリンク サーバー テーブルに対し、1 列あたり 1 行の列情報を返します。 **sp_columns_ex**場合のみ、特定の列の列情報を返す*列*を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_columns_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_server =** ] **'***table_server***'**  
 列情報を返すリンク サーバーの名前を指定します。 *table_server*は**sysname**、既定値はありません。  
  
 [  **@table_name =** ] **'***table_name***'**  
 列情報を返すテーブルの名前を指定します。 *table_name*は**sysname**、既定値は NULL です。  
  
 [  **@table_schema =** ] **'***、table_schema、***'**  
 列情報を返すテーブルのスキーマ名を指定します。 *table_schema、*は**sysname**、既定値は NULL です。  
  
 [  **@table_catalog =** ] **'***table_catalog***'**  
 列情報を返すテーブルのカタログ名を指定します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@column_name =** ] **'***列***'**  
 情報を提供するデータベース列の名前を指定します。 *列*は**sysname**、既定値は NULL です。  
  
 [  **@ODBCVer =** ] **'***ODBCVer***'**  
 使用されている ODBC のバージョンです。 *ODBCVer*は**int**、既定値は 2 です。 既定値の 2 は ODBC Version 2 を示します。 有効な値は 2 または 3 です。 バージョン 2 と 3 の動作の相違については、ODBC の SQLColumns 仕様を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブルまたはビュー修飾子の名前。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子***.***所有者***.***名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]この列は、データベースの名前を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブルまたはビュー所有者の名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この列は、テーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブルまたはビューの名前。 このフィールドは常に値を返します。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 このフィールドは常に値を返します。|  
|**DATA_TYPE**|**smallint**|ODBC のデータ型を表す整数値。 ODBC のデータ型にマップできないデータ型の場合、この値は NULL になります。 ネイティブ データ型の名前が返されます、 **TYPE_NAME**列です。|  
|**TYPE_NAME**|**varchar (**13**)**|データ型を表す文字列。 基になる DBMS によって、このデータ型の名前が提供されます。|  
|**COLUMN_SIZE**|**int**|有効桁数です。 戻り値、**精度**列は 10 進数。|  
|**BUFFER_LENGTH 列**|**int**|データの転送サイズ。1|  
|**DECIMAL_DIGITS**|**smallint**|小数点より右側の桁数です。|  
|**NUM_PREC_RADIX**|**smallint**|数値型の基数。|  
|**NULLABLE**|**smallint**|NULL 値を許容するかどうかを示します。<br /><br /> 1 = NULL 値を許容します。<br /><br /> 0 = NULL 値を許容しません。|  
|**「解説」**|**varchar (**254**)**|このフィールドは常に NULL を返します。|  
|**COLUMN_DEF**|**varchar (**254**)**|列の既定値です。|  
|**SQL_DATA_TYPE**|**smallint**|記述子の TYPE フィールドでの SQL データ型の値です。 この列は、同じ、 **DATA_TYPE**列を除き、 **datetime**と sql-92**間隔**データ型。 この列は、常に値を返します。|  
|**SQL_DATETIME_SUB**|**smallint**|サブタイプ コード**datetime**と sql-92**間隔**データ型。 他のデータ型の場合、この列は NULL を返します。|  
|**CHAR_OCTET_LENGTH**|**int**|文字型または整数型の列の最大長 (バイト単位)。 他のすべてのデータ型では、この列は NULL を返します。|  
|**ORDINAL_POSITION**|**int**|テーブル内での列の序数。 テーブルの最初の列は 1 です。 この列は、常に値を返します。|  
|**IS_NULLABLE**|**varchar (**254**)**|テーブル内にある列の NULL 値の許容属性。 NULL 値の許容属性の検査は ISO の規則に従います。 ISO SQL に準拠している DBMS では、空文字列を返すことはできません。<br /><br /> YES = 列に NULL を含むことができます。<br /><br /> NO = 列に NULL を含むことができません。<br /><br /> NULL が許可されているかどうかがわからない列は、長さ 0 の文字列を返します。<br /><br /> この列が返される値と異なる値が返される、 **NULLABLE**列です。|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 拡張ストアド プロシージャで使用されるデータ型。|  
  
 1 詳細については、Microsoft ODBC のドキュメントを参照してください。  
  
## <a name="remarks"></a>解説  
 **sp_columns_ex**の COLUMNS 行セットをクエリすることによって実行される、 **IDBSchemaRowset**に対応する OLE DB プロバイダーのインターフェイス*table_server*です。 *Table_name*、 *、table_schema、*、 *table_catalog*、および*列*行を制限するには、このインターフェイスにパラメーターを渡す返されます。  
  
 **sp_columns_ex**設定の指定したリンク サーバーの OLE DB プロバイダーがの COLUMNS 行セットをサポートしていない場合、空の結果を返します、 **IDBSchemaRowset**インターフェイスです。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="remarks"></a>解説  
 **sp_columns_ex**区切られた識別子の要件に依存します。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、リンク サーバー `JobTitle` 上の [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにある、`HumanResources.Employee` テーブルの `Seattle1` 列のデータ型を返します。  
  
```  
EXEC sp_columns_ex 'Seattle1',   
   'Employee',   
   'HumanResources',   
   'AdventureWorks2012',   
   'JobTitle';  
```  
  
## <a name="see-also"></a>参照  
 [sp_catalogs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_foreignkeys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
