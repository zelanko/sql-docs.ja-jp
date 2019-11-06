---
title: sys.system_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_columns_TSQL
- system_columns
- sys.system_columns
- sys.system_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_columns catalog view
ms.assetid: 4ab1d48a-d57a-4e76-a08c-9627eeaf4588
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd94f90a823ba57910809a54aed470ddd0bb0010
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108857"
---
# <a name="syssystemcolumns-transact-sql"></a>sys.system_columns (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  列を持つシステム オブジェクトの列ごとに 1 行のデータを保持します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列が属するオブジェクトの ID です。|  
|**name**|**sysname**|列の名前です。 オブジェクト内で一意です。|  
|**column_id**|**int**|列の ID です。 オブジェクト内で一意です。<br /><br /> 列 ID は連続した値にならないことがあります。|  
|**system_type_id**|**tinyint**|列のシステム型の ID|  
|**user_type_id**|**int**|ユーザーが定義した列の型の ID です。<br /><br /> 型の名前を返すには、この列で [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログ ビューに結合します。|  
|**max_length**|**smallint**|列のバイト単位で最大長。<br /><br /> -1 = 列のデータ型は**varchar (max)** 、 **nvarchar (max)** 、 **varbinary (max)** 、または**xml**します。<br /><br /> **テキスト**、列、 **max_length**値は 16 かによって設定された値になります**sp_tableoption** 'text in row' です。|  
|**有効桁数 (precision)**|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、0 です。|  
|**scale**|**tinyint**|数値ベースの場合、列の小数点以下桁数それ以外の場合、0 を返します。|  
|**collation_name**|**sysname**|文字ベースの場合は、列の照合順序の名前です。それ以外の場合は、NULL です。|  
|**is_nullable**|**bit**|1 = 列で NULL 値を使用できます。|  
|**is_ansi_padded**|**bit**|1 = 文字、バイナリ、またはバリアントの場合、列で ANSI_PADDING ON 動作を使用します。<br /><br /> 0 = 列は文字、バイナリ、またはバリアントではありません。|  
|**is_rowguidcol**|**bit**|1 = 列は宣言された ROWGUIDCOL です。|  
|**is_identity**|**bit**|1 = 列は id 値。|  
|**is_computed**|**bit**|1 = 列は計算列です。|  
|**is_filestream**|**bit**|1 = filestream 記憶域を使用する列が宣言されました。|  
|**is_replicated**|**bit**|1 = 列はレプリケートされています。|  
|**is_non_sql_subscribed**|**bit**|1 = 列には、非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。|  
|**is_merge_published**|**bit**|1 = 列はマージ パブリッシュされています。|  
|**is_dts_replicated**|**bit**|1 = 列は [!INCLUDE[ssIS](../../includes/ssis-md.md)] を使用してレプリケートされています。|  
|**is_xml_document**|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = 内容がドキュメント フラグメント、または列のデータ型でない**xml**します。|  
|**xml_collection_id**|**int**|列のデータ型がの場合は 0 以外**xml** XML が型指定されたとします。 この値は、列の検証 XML スキーマ名前空間を含むコレクションの ID です。<br /><br /> 0 = いいえの XML スキーマ コレクションです。|  
|**default_object_id**|**int**|スタンドアロンであるかどうかにかかわらず、既定のオブジェクトの ID [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)、または、インラインの列レベルの既定の制約。 **Parent_object_id**インラインの列レベルの既定値オブジェクトの列がテーブル自体への参照。 既定値がない場合は 0 です。|  
|**rule_object_id**|**int**|使用して、列にバインドするスタンドアロン ルールの ID **sys.sp_bindrule**します。<br /><br /> 0 = スタンドアロン ルールはありません。<br /><br /> 列レベルの CHECK 制約を参照してください。 [sys.check_constraints &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)します。|  
|is_sparse|**bit**|1 = 列はスパース列です。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|  
|is_column_set|**bit**|1 = 列は列セットです。 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|  
|generated_always_type|**tinyint**|列の種類を表す数値。<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|列の種類の説明テキスト。<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
