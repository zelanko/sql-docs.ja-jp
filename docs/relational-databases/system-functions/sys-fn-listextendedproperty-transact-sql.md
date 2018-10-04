---
title: sys.fn_listextendedproperty (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_listextendedproperty
- fn_listextendedproperty_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_listextendedproperty function
- displaying extended properties
- database extended properties [SQL Server]
- viewing extended properties
- column extended properties [SQL Server]
- sys.fn_listextendedproperties function
- database objects [SQL Server], extended properties
- extended properties [SQL Server], columns
- table extended properties [SQL Server]
ms.assetid: 59bbb91f-a277-4a35-803e-dcb91e847a49
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 98cde3ea4c7150afd3eb2b547e73cf1b7f88e613
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792295"
---
# <a name="sysfnlistextendedproperty-transact-sql"></a>sys.fn_listextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース オブジェクトの拡張プロパティの値を返します。  
 
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_listextendedproperty (   
    { default | 'property_name' | NULL }   
  , { default | 'level0_object_type' | NULL }   
  , { default | 'level0_object_name' | NULL }   
  , { default | 'level1_object_type' | NULL }   
  , { default | 'level1_object_name' | NULL }   
  , { default | 'level2_object_type' | NULL }   
  , { default | 'level2_object_name' | NULL }   
  )   
```  
  
## <a name="arguments"></a>引数  
 { default | '*property_name*' | NULL}  
 プロパティ名を指定します。 *property_name*は**sysname**します。 有効な値は、default、NULL、またはプロパティ名です。  
  
 { default | '*level0_object_type*' | NULL}  
 ユーザーまたはユーザーが定義した種類です。 *level0_object_type*は**varchar (128)**、既定値は NULL です。 有効な値は、ASSEMBLY、CONTRACT、EVENT NOTIFICATION、FILEGROUP、MESSAGE TYPE、PARTITION FUNCTION、PARTITION SCHEME、REMOTE SERVICE BINDING、ROUTE、SCHEMA、SERVICE、TRIGGER、TYPE、USER、および NULL です。  
  
> [!IMPORTANT]  
>  USER および TYPE はレベル 0 の種類は、の将来のバージョンで削除される予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。 USER の代わりに、レベル 0 の種類として SCHEMA を使用してください。 TYPE については、レベル 0 の種類として SCHEMA、レベル 1 の種類として TYPE を使用してください。  
  
 { default | '*level0_object_name*' | NULL }  
 指定したレベル 0 のオブジェクトの種類の名前です。 *level0_object_name*は**sysname**既定値は NULL です。 有効な値は、default、NULL、またはオブジェクト名です。  
  
 { default | '*level1_object_type*' | NULL }  
 レベル 1 のオブジェクトの種類です。 *level1_object_type*は**varchar (128)** 既定値は NULL です。 有効な値は、AGGREGATE、DEFAULT、FUNCTION、LOGICAL FILE NAME、PROCEDURE、QUEUE、RULE、SYNONYM、TABLE、TYPE、VIEW、XML SCHEMA COLLECTION、および NULL です。  
  
> [!NOTE]  
>  default は NULL に相当し、'default' はオブジェクトの種類の DEFAULT に相当します。  
  
 {default | '*level1_object_name*' |NULL }  
 指定したレベル 1 のオブジェクトの種類の名前です。 *level1_object_name*は**sysname**既定値は NULL です。 有効な値は、default、NULL、またはオブジェクト名です。  
  
 { default | '*level2_object_type*' |NULL }  
 レベル 2 のオブジェクトの型です。 *level2_object_type*は**varchar (128)** 既定値は NULL です。 有効な値は、DEFAULT、default (NULL に相当します)、または NULL です。 有効な入力*level2_object_type*は列、制約、EVENT NOTIFICATION、インデックス、パラメーター、トリガー、および NULL です。  
  
 { default | '*level2_object_name*' |NULL }  
 指定したレベル 2 のオブジェクトの種類の名前です。 *level2_object_name*は**sysname**既定値は NULL です。 有効な値は、default、NULL、またはオブジェクト名です。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の表は、fn_listextendedproperty が返すテーブルの形式です。  
  
|列名|データ型|  
|-----------------|---------------|  
|objtype|**sysname**|  
|objname|**sysname**|  
|NAME|**sysname**|  
|value|**sql_variant**|  
  
 返されたテーブルが空の場合は、目的のオブジェクトに拡張プロパティがないか、またはユーザーがそのオブジェクトの拡張プロパティを一覧表示する権限を持っていないことを意味します。 データベース自体の拡張プロパティを返す場合、objtype および objname 列は NULL になります。  
  
## <a name="remarks"></a>コメント  
 場合の値は、 *property_name*が NULL または既定では、fn_listextendedproperty は指定したオブジェクトのすべてのプロパティを返します。  
  
 指定されたオブジェクトの種類に対応するオブジェクト名の値が NULL または default である場合、fn_listextendedproperty は指定された種類のすべてのオブジェクトの、すべての拡張プロパティを返します。  
  
 オブジェクトは、レベルによって区別されます。レベル 0 が最上位で、レベル 2 が最下位です。 下位レベルであるレベル 1 または 2 のオブジェクトの種類および名前を指定する場合、親オブジェクトの種類と名前を、NULL または default 以外の値で指定する必要があります。 それ以外の場合は、空のセットを返します。  
  
 **objname** latin1_general_ci_ai に固定します。 ただし、回避できますこの比較での照合順序をオーバーライドすることで。  
  
```  
SELECT o.[object_id] AS 'table_id', o.[name] 'table_name',  
0 AS 'column_order', NULL AS 'column_name', NULL AS 'column_datatype',  
NULL AS 'column_length', Cast(e.value AS varchar(500)) AS 'column_description'  
FROM AdventureWorks.sys.objects AS o  
LEFT JOIN sys.fn_listextendedproperty(N'MS_Description', N'user',N'HumanResources',N'table', N'Employee', null, default) AS e  
    ON o.name = e.objname COLLATE SQL_Latin1_General_CP1_CI_AS  
WHERE o.name = 'Employee';  
```  
  
## <a name="permissions"></a>アクセス許可  
 オブジェクトの拡張プロパティを一覧表示する権限は、オブジェクトの種類によって異なります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. データベースの拡張プロパティを表示する  
 次の例では、データベース オブジェクト自体のすべての拡張プロパティを表示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty(default, default, default, default, default, default, default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype    objname     name            value`  
  
 `---------  ---------   -----------     ----------------------------`  
  
 `NULL       NULL        MS_Description  AdventureWorks2008 Sample OLTP Database`  
  
 `(1 row(s) affected)`  
  
### <a name="b-displaying-extended-properties-on-all-columns-in-a-table"></a>B. テーブル内のすべての列の拡張プロパティを表示する  
 次の例では、列の拡張プロパティを一覧表示、`ScrapReason`テーブル。 これは、スキーマに含まれている`Production`します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Production', 'table', 'ScrapReason', 'column', default);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `objtype objname      name            value`  
  
 `------- -----------  -------------   ------------------------`  
  
 `COLUMN ScrapReasonID MS_Description  Primary key for ScrapReason records.`  
  
 `COLUMN Name          MS_Description  Failure description.`  
  
 `COLUMN ModifiedDate  MS_Description  Date the record was last updated.`  
  
 `(3 row(s) affected)`  
  
### <a name="c-displaying-extended-properties-on-all-tables-in-a-schema"></a>C. スキーマ内のすべてのテーブルの拡張プロパティを表示する  
 次の例に含まれているすべてのテーブルの拡張プロパティを一覧表示、`Sales`スキーマ。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT objtype, objname, name, value  
FROM fn_listextendedproperty (NULL, 'schema', 'Sales', 'table', default, NULL, NULL);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_addextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
