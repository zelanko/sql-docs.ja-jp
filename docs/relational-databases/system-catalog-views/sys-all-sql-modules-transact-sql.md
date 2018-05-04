---
title: sys.all_sql_modules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dadaa0ebaffbc284d61d5a1a1a13e028fd6ac57f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysallsqlmodules-transact-sql"></a>sys.all_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  和集合を返します**sys.sql_modules**と**sys.system_sql_modules**です。  
  
 このビューでは、各ネイティブ コンパイル、スカラー ユーザー定義関数の行を返します。 詳しくは、「[インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)」をご覧ください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このオブジェクトが属するオブジェクトの ID です。 データベース内で一意です。|  
|**definition**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。<br /><br /> NULL = 暗号化されている|  
|**uses_ansi_nulls**|**bit**|モジュールは、SET ANSI_NULLS ON で作成されました。|  
|**uses_quoted_identifier**|**bit**|モジュールは、SET QUOTED_IDENTIFIER ON で作成されました。|  
|**is_schema_bound**|**bit**|モジュールは、SCHEMABINDING オプションで作成されました。|  
|**uses_database_collation**|**bit**|スキーマ バインドのモジュール定義が適切な評価のためにデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 この依存性によって、データベースの既定の照合順序が変更されるのを防ぐことができます。|  
|**is_recompiled**|**bit**|手順は、WITH RECOMPILE オプションを使用して作成されました。|  
|**null_on_null_input**|**bit**|モジュールは、任意の NULL 入力上で NULL 出力を生成するように宣言されました。|  
|**execute_as_principal_id**|**int**|EXECUTE AS データベース プリンシパルの ID です。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 場合は、指定されたプリンシパル ID EXECUTE AS SELF または EXECUTE AS\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
|**uses_native_compilation**|bit|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 0 = ネイティブでコンパイルされていない<br /><br /> 1 = ネイティブでコンパイルされている<br /><br /> 既定値は 0 です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.system_sql_modules &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-sql-modules-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
