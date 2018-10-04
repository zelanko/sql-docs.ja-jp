---
title: sp_dropextendedproperty (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproperty_TSQL
- sp_dropextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproperty
ms.assetid: 4851865a-86ca-4823-991a-182dd1934075
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e01b14407198ed88654527bd247a116c200fb1e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627430"
---
# <a name="spdropextendedproperty-transact-sql"></a>sp_dropextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存の拡張プロパティを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropextendedproperty   
    [ @name = ] { 'property_name' }  
      [ , [ @level0type = ] { 'level0_object_type' }   
        , [ @level0name = ] { 'level0_object_name' }   
            [ , [ @level1type = ] { 'level1_object_type' }   
              , [ @level1name = ] { 'level1_object_name' }   
                [ , [ @level2type = ] { 'level2_object_type' }   
                  , [ @level2name = ] { 'level2_object_name' }   
                ]   
            ]   
        ]   
    ]   
```  
  
## <a name="arguments"></a>引数  
 [ @name=] {'*property_name*'}  
 削除するプロパティの名前です。 *property_name*は**sysname** NULL にすることはできません。  
  
 [ @level0type=] {'*level0_object_type*'}  
 指定したレベル 0 のオブジェクトの種類の名前です。 *level0_object_type*は**varchar (128)**、既定値は NULL です。  
  
 有効な値は、ASSEMBLY、CONTRACT、EVENT NOTIFICATION、FILEGROUP、MESSAGE TYPE、PARTITION FUNCTION、PARTITION SCHEME、REMOTE SERVICE BINDING、ROUTE、SCHEMA、SERVICE、USER、TRIGGER、TYPE、および NULL です。  
  
> [!IMPORTANT]  
>  USER および TYPE はレベル 0 の種類は、の将来のバージョンで削除される予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。 USER の代わりに、レベル 0 の種類として SCHEMA を使用してください。 TYPE については、レベル 0 の種類として SCHEMA、レベル 1 の種類として TYPE を使用してください。  
  
 [ @level0name=] {'*level0_object_name*'}  
 指定したレベル 0 のオブジェクトの種類の名前です。 *level0_object_name*は**sysname**既定値は NULL です。  
  
 [ @level1type=] {'*level1_object_type*'}  
 レベル 1 のオブジェクトの種類です。 *level1_object_type*は**varchar (128)** 既定値は NULL です。 有効な値は、AGGREGATE、DEFAULT、FUNCTION、LOGICAL FILE NAME、PROCEDURE、QUEUE、RULE、SYNONYM、TABLE、TABLE_TYPE、TYPE、VIEW、XML SCHEMA COLLECTION、および NULL です。  
  
 [ @level1name=] {'*level1_object_name*'}  
 指定したレベル 1 のオブジェクトの種類の名前です。 *level1_object_name*は**sysname**既定値は NULL です。  
  
 [ @level2type=] {'*level2_object_type*'}  
 レベル 2 のオブジェクトの型です。 *level2_object_type*は**varchar (128)** 既定値は NULL です。 有効な値は、COLUMN、CONSTRAINT、EVENT NOTIFICATION、INDEX、PARAMETER、TRIGGER、および NULL です。  
  
 [ @level2name=] {'*level2_object_name*'}  
 指定したレベル 2 のオブジェクトの種類の名前です。 *level2_object_name*は**sysname**既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 内のオブジェクトの拡張プロパティを指定するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース 3 つのレベルに分類されます。 0、1、および 2 です。 レベル 0 は、最上位のレベルし、データベース スコープに含まれるオブジェクトとして定義されます。 レベル 1 のオブジェクトはスキーマ スコープまたはユーザー スコープに含まれ、レベル 2 のオブジェクトはレベル 1 のオブジェクトに含まれます。 これら、どのレベルのオブジェクトに対しても、拡張プロパティを定義できます。 あるレベルのオブジェクトを参照する場合は、その上位レベルにあるすべてのオブジェクトの種類と名前で修飾する必要があります。  
  
 指定する有効な*property_name*プロパティが削除されるか、すべてのオブジェクトの種類および名前が null と、プロパティは、現在のデータベースに存在するかどうか。 このトピックの例 B を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 固定データベース ロール db_owner および db_ddladmin のメンバーは、任意のオブジェクトの拡張プロパティを削除できます。ただし、例外として、db_ddladmin はデータベース自体、ユーザー、およびロールに対しては、プロパティを追加できません。  
  
 ユーザーは、自身が所有するオブジェクト、および ALTER 権限または CONTROL 権限を持つオブジェクトの拡張プロパティを削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-an-extended-property-on-a-column"></a>A. 列の拡張プロパティを削除する  
 次の例では、スキーマ `caption` に含まれるテーブル `id` 内の列 `T1` からプロパティ `dbo` を削除します。  
  
```  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
     @name = 'caption'   
    ,@value = 'Employee ID'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
EXEC sp_dropextendedproperty   
     @name = 'caption'   
    ,@level0type = 'schema'   
    ,@level0name = dbo  
    ,@level1type = 'table'  
    ,@level1name = 'T1'  
    ,@level2type = 'column'  
    ,@level2name = id;  
GO  
DROP TABLE T1;  
GO  
```  
  
### <a name="b-dropping-an-extended-property-on-a-database"></a>B. データベースの拡張プロパティを削除する  
 次の例では、という名前のプロパティを削除する`MS_Description`から、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベース。 これはデータベース自体のプロパティであり、オブジェクトの種類および名前は指定しません。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_dropextendedproperty   
@name = N'MS_Description';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
