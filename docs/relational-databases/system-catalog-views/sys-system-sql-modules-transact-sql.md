---
title: system_sql_modules (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dd6f6d995fd1bbf4378525c2e767e0ce05bd908a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821339"
---
# <a name="syssystem_sql_modules-transact-sql"></a>system_sql_modules (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  SQL 言語定義モジュールを含むシステム オブジェクトごとに 1 行のデータを返します。 FN、IF、P、PC、TF、V 型のシステムオブジェクトには、SQL モジュールが関連付けられています。 親オブジェクトを識別するには、このビューを[system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)に結合します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|格納するオブジェクトのオブジェクト id 番号。データベース内で一意です。|  
|**カスタム**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。|  
|**uses_ansi_nulls**|**bit**|1 = モジュールは、の SET ANSI_NULLS データベースオプションを使用して作成されました。<br /><br /> 常に1を返します。|  
|**uses_quoted_identifier**|**bit**|1 = モジュールは、SET QUOTED_IDENTIFIER ON の状態で作成されました。<br /><br /> 常に1を返します。|  
|**is_schema_bound**|**bit**|0 = モジュールは、SCHEMABINDING オプションを使用して作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**uses_database_collation**|**bit**|0 = モジュールは、データベースの既定の照合順序に依存していません。<br /><br /> 常に 0 を返します。|  
|**is_recompiled**|**bit**|0 = プロシージャは、WITH RECOMPILE オプションを使って作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**null_on_null_input**|**bit**|0 = モジュールは、NULL 入力に対して NULL 出力を生成するために作成されませんでした。<br /><br /> 常に 0 を返します。|  
|**execute_as_principal_id**|**int**|常に NULL を返します|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [all_sql_modules &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
