---
title: sys.sql_modules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/09/2018
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
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4d87adebfb1b2800d95a36f06a66a0022a38b86f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syssqlmodules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  SQL 言語定義モジュールであるオブジェクトごとに行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ネイティブを含むユーザー定義のスカラー関数をコンパイルします。 種類が P、RF、V、TR、FN、IF、TF、および R のオブジェクトには、SQL モジュールが関連付けられています。 スタンドアロンの既定値である種類 D のオブジェクトにも、このビューで SQL モジュール定義が関連付けられています。 これらの型の説明は、次を参照してください。、**型**内の列、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューです。  
  
 詳しくは、「[インメモリ OLTP でのユーザー定義のスカラー関数](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md)」をご覧ください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このオブジェクトが属するオブジェクトの ID です。 データベース内で一意です。|  
|**definition**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。 使用してこの値を取得することも、 [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)組み込み関数。<br /><br /> NULL は、暗号化されていることを示します。|  
|**uses_ansi_nulls**|**bit**|モジュールは、SET ANSI_NULLS ON で作成されました。<br /><br /> ルールとデフォルトに対しては、常に 0 になります。|  
|**uses_quoted_identifier**|**bit**|モジュールは、SET QUOTED_IDENTIFIER ON で作成されました。|  
|**is_schema_bound**|**bit**|モジュールは SCHEMABINDING オプションを使用して作成されました。<br /><br /> ネイティブ コンパイル ストアド プロシージャでは、常に値 1 が含まれます。|  
|**uses_database_collation**|**bit**|スキーマ バインドのモジュール定義が適切な評価のためにデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 このような依存関係により、データベースの既定の照合順序は変更されないようになっています。|  
|**is_recompiled**|**bit**|プロシージャは WITH RECOMPILE オプションを使用して作成されました。|  
|**null_on_null_input**|**bit**|モジュールは、任意の NULL 入力上で NULL 出力を生成するように宣言されました。|  
|**execute_as_principal_id**|**Int**|EXECUTE AS データベース プリンシパルの ID です。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 場合は、指定されたプリンシパル ID EXECUTE AS SELF または EXECUTE AS\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
|**uses_native_compilation**|**bit**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]<br /><br /> 0 = ネイティブでコンパイルされていない<br /><br /> 1 = ネイティブでコンパイルされている<br /><br /> 既定値は 0 です。|  
  
## <a name="remarks"></a>解説  
 既定の制約、D 型のオブジェクトの SQL 式に存在、 [sys.default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)カタログ ビューです。 CHECK 制約、C の型のオブジェクトの SQL 式に存在、 [sys.check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)カタログ ビューです。  
  
 この情報が記載されています[sys.dm_db_uncontained_entities &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のデータベース内の各モジュールの名前、型、および定義を返します。  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
