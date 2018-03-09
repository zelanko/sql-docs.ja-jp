---
title: "sp_updateextendedproperty (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/12/2016
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
- sp_updateextendedproperty_TSQL
- sp_updateextendedproperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updateextendedproperty
ms.assetid: 7f02360f-cb9e-48b4-b75f-29b4bc9ea304
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 284eb1e8d95ff94091df493048826e3a958ffb8c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spupdateextendedproperty-transact-sql"></a>sp_updateextendedproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  既存の拡張プロパティの値を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_updateextendedproperty  
    [ @name = ]{ 'property_name' }   
    [ , [ @value = ]{ 'value' }  
        [, [ @level0type = ]{ 'level0_object_type' }  
         , [ @level0name = ]{ 'level0_object_name' }  
              [, [ @level1type = ]{ 'level1_object_type' }  
               , [ @level1name = ]{ 'level1_object_name' }  
                     [, [ @level2type = ]{ 'level2_object_type' }  
                      , [ @level2name = ]{ 'level2_object_name' }  
                     ]  
              ]  
        ]  
    ]  
```  
  
## <a name="arguments"></a>引数  
 [ @name=] {'*property_name*'}  
 更新するプロパティの名前です。 *property_name*は**sysname**NULL にすることはできません。  
  
 [ @value=] {'*値*'}  
 プロパティに関連付ける値です。 *値*は**sql_variant**、既定値は NULL です。 サイズ*値*7,500 バイト以下ができない可能性があります。  
  
 [ @level0type=] {'*level0_object_type*'}  
 ユーザーまたはユーザーが定義した種類です。 *level0_object_type*は**varchar (128)**、既定値は NULL です。 有効な入力値は、アセンブリ、コントラクト、イベント通知、ファイル グループ、メッセージの種類、パーティション関数、パーティション構成、PLAN GUIDE、REMOTE SERVICE BINDING、ROUTE、スキーマ、サービス、ユーザー、トリガー、型、および NULL です。  
  
> [!IMPORTANT]  
>  USER および TYPE はレベル 0 の種類は、の将来のバージョンで削除される予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。 USER の代わりに、レベル 0 の種類として SCHEMA を使用してください。 TYPE については、レベル 0 の種類として SCHEMA、レベル 1 の種類として TYPE を使用してください。  
  
 [ @level0name=] {'*level0_object_name*'}  
 指定したレベル 1 のオブジェクトの種類の名前です。 *level0_object_name*は**sysname**既定値は NULL です。  
  
 [ @level1type=] {'*level1_object_type*'}  
 レベル 1 のオブジェクトの種類です。 *level1_object_type*は**varchar (128)**既定値は NULL です。 有効な値は、AGGREGATE、DEFAULT、FUNCTION、LOGICAL FILE NAME、PROCEDURE、QUEUE、RULE、SYNONYM、TABLE、TABLE_TYPE、TYPE、VIEW、XML SCHEMA COLLECTION、および NULL です。  
  
 [ @level1name=] {'*level1_object_name*'}  
 指定したレベル 1 のオブジェクトの種類の名前です。 *level1_object_name*は**sysname**既定値は NULL です。  
  
 [ @level2type=] {'*level2_object_type*'}  
 レベル 2 のオブジェクトの型です。 *level2_object_type*は**varchar (128)**既定値は NULL です。 有効な値は、COLUMN、CONSTRAINT、EVENT NOTIFICATION、INDEX、PARAMETER、TRIGGER、および NULL です。  
  
 [ @level2name=] {'*level2_object_name*'}  
 指定したレベル 2 のオブジェクトの種類の名前です。 *level2_object_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 内のオブジェクトの拡張プロパティを指定するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースは、次の 3 つのレベル (0、1、および 2) に分類されます。 レベル 0 は、最上位のレベルし、は、データベース スコープに含まれているオブジェクトとして定義します。 レベル 1 のオブジェクトはスキーマ スコープまたはユーザー スコープに含まれ、レベル 2 のオブジェクトはレベル 1 のオブジェクトに含まれます。 これら、どのレベルのオブジェクトに対しても、拡張プロパティを定義できます。 1 つのレベルにあるオブジェクトを参照する場合は、そのオブジェクトを所有または格納する上位レベルのオブジェクトの名前で修飾する必要があります。  
  
 指定する有効な*property_name*と*値*プロパティが更新されましたが、現在のデータベースに属するすべてのオブジェクトの種類および名前が null の場合。  
  
## <a name="permissions"></a>Permissions  
 固定データベース ロール db_owner および db_ddladmin のメンバーは、任意のオブジェクトの拡張プロパティを更新できます。ただし、例外として、db_ddladmin はデータベース自体、ユーザー、およびロールに対しては、プロパティを追加できません。  
  
 ユーザーは、自身が所有するオブジェクト、および ALTER 権限または CONTROL 権限を持つオブジェクトの拡張プロパティを更新できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-updating-an-extended-property-on-a-column"></a>A. 列の拡張プロパティを更新する  
 次の例は、プロパティの値を更新`Caption`列で`ID`表内`T1`です。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE T1 (id int , name char (20));  
GO  
EXEC sp_addextendedproperty   
    @name = N'Caption'  
    ,@value = N'Employee ID'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
--Update the extended property.  
EXEC sp_updateextendedproperty   
    @name = N'Caption'  
    ,@value = 'Employee ID must be unique.'  
    ,@level0type = N'Schema', @level0name = dbo  
    ,@level1type = N'Table',  @level1name = T1  
    ,@level2type = N'Column', @level2name = id;  
GO  
```  
  
### <a name="b-updating-an-extended-property-on-a-database"></a>B. データベースの拡張プロパティを更新する  
 次の例は最初に、拡張プロパティを作成、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベースとそのプロパティの値を更新します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_addextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample OLTP Database';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_updateextendedproperty   
@name = N'NewCaption', @value = 'AdventureWorks2012 Sample Database';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.fn_listextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sys.extended_properties &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)  
  
  
