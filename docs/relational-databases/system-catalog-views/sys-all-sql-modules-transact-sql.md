---
title: "sys.all_sql_modules (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- all_sql_modules_TSQL
- sys.all_sql_modules
- all_sql_modules
- sys.all_sql_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_sql_modules catalog view
ms.assetid: 7477a3fe-afb3-44c8-bb2c-c6e1d9bdee6f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3dd4ffb3ff3362ca918d97432f56ff97471d26c7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysallsqlmodules-transact-sql"></a>sys.all_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  和集合を返します**sys.sql_modules**と**sys.system_sql_modules**です。  
  
 このビューでは、各ネイティブ コンパイル、スカラー ユーザー定義関数の行を返します。 詳細については、次を参照してください。 [scalar user-defined 関数は、インメモリ OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このオブジェクトが属するオブジェクトの ID です。 データベース内で一意です。|  
|**定義**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。<br /><br /> NULL = 暗号化されている|  
|**uses_ansi_nulls**|**bit**|モジュールは、SET ANSI_NULLS ON で作成されました。|  
|**uses_quoted_identifier**|**bit**|モジュールは、SET QUOTED_IDENTIFIER ON で作成されました。|  
|**is_schema_bound**|**bit**|モジュールは、SCHEMABINDING オプションで作成されました。|  
|**uses_database_collation**|**bit**|スキーマ バインドのモジュール定義が適切な評価のためにデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 この依存性によって、データベースの既定の照合順序が変更されるのを防ぐことができます。|  
|**is_recompiled**|**bit**|手順は、WITH RECOMPILE オプションを使用して作成されました。|  
|**null_on_null_input**|**bit**|モジュールは、任意の NULL 入力上で NULL 出力を生成するように宣言されました。|  
|**execute_as_principal_id**|**int**|EXECUTE AS データベース プリンシパルの ID です。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 場合は、指定されたプリンシパル ID EXECUTE AS SELF または EXECUTE AS\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
|**uses_native_compilation**|bit|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 = ネイティブでコンパイルされていない<br /><br /> 1 = ネイティブでコンパイルされている<br /><br /> 既定値は 0 です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.system_sql_modules &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-system-sql-modules-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
