---
title: sys.types (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- types
- types_TSQL
- sys.types_TSQL
- sys.types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.types catalog view
- table-valued parameters,sys.types
ms.assetid: a5dbc842-71a0-4f62-b5e0-f560a99b7f8c
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: aa880dfc74d2bccdcecacc6a303067fde38a5e87
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43097253"
---
# <a name="systypes-transact-sql"></a>sys.types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  システム型とユーザー定義の型ごとに 1 行のデータを格納します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|型名。 スキーマ内で一意です。|  
|**system_type_id**|**tinyint**|型の内部システム型の ID。|  
|**user_type_id**|**int**|型の ID。 データベース内で一意です。 システム データ型、 **user_type_id** = **system_type_id**します。|  
|**schema_id**|**int**|型が属するスキーマの ID。|  
|**principal_id**|**int**|所有者がスキーマの所有者と異なる場合、その所有者の ID。 既定では、スキーマに含まれるオブジェクトは、スキーマの所有者によって所有されます。 ただし、所有権を変更する ALTER AUTHORIZATION ステートメントを使用して、別の所有者を指定できます。<br /><br /> 別の所有者がいない場合は NULL になります。|  
|**max_length**|**smallint**|型のバイト単位で最大長。<br /><br /> -1 = 列のデータ型は**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**します。<br /><br /> **テキスト**、列、 **max_length**値は 16 になります。|  
|**有効桁数**|**tinyint**|型が数値型の場合の最大有効桁数。数値型以外の場合は 0 になります。|  
|**scale**|**tinyint**|型が数値型の場合の最大小数点以下桁数。数値型以外の場合は 0 になります。|  
|**collation_name**|**sysname**|型が文字型の場合の照合順序名。文字型以外の場合は NULL になります。|  
|**is_nullable**|**bit**|NULL 値を許容。|  
|**is_user_defined**|**bit**|1 = ユーザー定義の型。<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型。|  
|**is_assembly_type**|**bit**|1 = 型の実装は CLR アセンブリで定義。<br /><br /> 0 = 型はに基づいて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型。|  
|**default_object_id**|**int**|使用して、型にバインドされているスタンドアロンの既定の ID [sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)します。<br /><br /> 0 = 既定値は存在しません。|  
|**rule_object_id**|**int**|使用して、型にバインドされているスタンドアロン ルールの ID [sp_bindrule](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)します。<br /><br /> 0 = ルールは存在しません。|  
|**is_table_type**|**bit**|型がテーブルであることを示します。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [スカラー型カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
