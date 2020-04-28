---
title: system_columns (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: cdb28d10d04c21f0d377777b41c332eb20d1ee9c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "73981917"
---
# <a name="syssystem_columns-transact-sql"></a>system_columns (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  列を持つシステム オブジェクトの列ごとに 1 行のデータを保持します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列が所属するオブジェクトの ID。|  
|**name**|**sysname**|列の名前です。 は、オブジェクト内で一意です。|  
|**column_id**|**int**|列の ID。 は、オブジェクト内で一意です。<br /><br /> 列 Id が連続していない可能性があります。|  
|**system_type_id**|**tinyint**|列のシステム型の ID|  
|**user_type_id**|**int**|ユーザーが定義した列の型の ID。<br /><br /> 型の名前を返すには、この列の[型](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)のカタログビューに結合します。|  
|**max_length**|**smallint**|列の最大長 (バイト単位)。<br /><br /> -1 = 列のデータ型は**varchar (max)**,、 **nvarchar (max)**,、 **varbinary (max)**,、または**xml**です。<br /><br /> **テキスト**列の場合、 **max_length**値は16か**sp_tableoption** ' text in row ' によって設定された値になります。|  
|**有効桁数 (precision)**|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、0 です。|  
|**scale**|**tinyint**|数値ベースの場合は、列の小数点以下桁数です。それ以外の場合は、0 です。|  
|**collation_name**|**sysname**|文字ベースの場合は、列の照合順序の名前です。それ以外の場合は、NULL です。|  
|**is_nullable**|**bit**|1 = 列で NULL 値を使用できます。|  
|**is_ansi_padded**|**bit**|1 = 列文字、バイナリ、またはバリアントの場合は、動作に ANSI_PADDING が使用されます。<br /><br /> 0 = 列は文字、バイナリ、またはバリアントではありません。|  
|**is_rowguidcol**|**bit**|1 = 列は宣言された ROWGUIDCOL です。|  
|**is_identity**|**bit**|1 = 列には id 値があります。|  
|**is_computed**|**bit**|1 = 列は計算列です。|  
|**is_filestream**|**bit**|1 = 列は、filestream ストレージを使用するように宣言されています。|  
|**is_replicated**|**bit**|1 = 列はレプリケートされています。|  
|**is_non_sql_subscribed**|**bit**|1 = 列には、以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサブスクライバーがあります。|  
|**is_merge_published**|**bit**|1 = 列はマージパブリッシュされています。|  
|**is_dts_replicated**|**bit**|1 = 列は、を使用[!INCLUDE[ssIS](../../includes/ssis-md.md)]してレプリケートされます。|  
|**is_xml_document**|**bit**|1 = コンテンツは完全な XML ドキュメントです。<br /><br /> 0 = コンテンツがドキュメントフラグメントであるか、または列のデータ型が**xml**ではありません。|  
|**xml_collection_id**|**int**|列のデータ型が**xml**で xml が型指定されている場合は0以外の値。 この値は、列の検証 XML スキーマ名前空間を含むコレクションの ID になります。<br /><br /> 0 = XML スキーマコレクションがありません。|  
|**default_object_id**|**int**|スタンドアロンの[sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)であるか、インラインの列レベルの既定の制約であるかに関係なく、既定のオブジェクトの ID。 インライン列レベルの既定のオブジェクトの**parent_object_id**列は、テーブル自体への参照です。 既定値がない場合は 0 です。|  
|**rule_object_id**|**int**|**Sp_bindrule**を使用して、列にバインドされているスタンドアロンルールの ID。<br /><br /> 0 = スタンドアロンルールはありません。<br /><br /> 列レベルの CHECK 制約については、「 [sys. check_constraints &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)」を参照してください。|  
|is_sparse|**bit**|1 = 列はスパース列です。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|  
|is_column_set|**bit**|1 = 列は列セットです。 詳細については、「 [列セットの使用](../../relational-databases/tables/use-column-sets.md)」を参照してください。|  
|generated_always_type|**tinyint**|列の型を表す数値。<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END|  
|generated_always_type_desc|**nvarchar(60)**|列の型の説明テキスト。<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システムカタログに対するクエリについてよく寄せられる質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [all_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [computed_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)  
  
  
