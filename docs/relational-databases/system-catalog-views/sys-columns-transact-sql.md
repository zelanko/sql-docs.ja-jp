---
title: "sys.columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.columns_TSQL
- sys.columns
- columns_TSQL
- columns
dev_langs: TSQL
helpviewer_keywords: sys.columns catalog view
ms.assetid: 323ac9ea-fc52-4b8c-8a7e-e0e44f8ed86c
caps.latest.revision: "57"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4ddf0a9cf5aabd35bd02b11a3b270e8e1c8100cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syscolumns-transact-sql"></a>sys.columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ビューやテーブルなど、列を持つオブジェクトの列ごとに 1 行のデータを返します。 以下に、列を持つオブジェクトの種類の一覧を示します。  
  
-   テーブル値アセンブリ関数 (FT)  
  
-   インライン テーブル値 SQL 関数 (IF)  
  
-   内部テーブル (IT)  
  
-   システム テーブル (S)  
  
-   テーブル値 SQL 関数 (TF)  
  
-   ユーザー テーブル (U)  
  
-   ビュー (V)  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|この列が属するオブジェクトの ID です。|  
|name|**sysname**|列の名前です。 オブジェクト内で一意です。|  
|column_id|**int**|列の ID です。 オブジェクト内で一意です。<br /><br /> 列 ID は連続した値にならないことがあります。|  
|system_type_id|**tinyint**|列のシステム型の ID。|  
|user_type_id|**int**|ユーザーが定義した列の型の ID です。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
|max_length|**smallint**|列の最大長 (バイト単位) です。<br /><br /> -1 = 列のデータ型は**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**です。<br /><br /> **テキスト**列の場合、max_length の値は 16 かなります sp_tableoption 'text in row' によって設定された値。|  
|有効桁数 (precision)|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、0 です。|  
|scale|**tinyint**|数値ベース以外の場合は列の小数点以下桁数それ以外の場合、0 を返します。|  
|collation_name|**sysname**|文字ベースの場合は、列の照合順序の名前です。それ以外の場合は、NULL です。|  
|is_nullable|**bit**|1 = 列で NULL 値を使用できます。|  
|is_ansi_padded|**bit**|1 = 文字、バイナリ、またはバリアントの場合、列で ANSI_PADDING ON 動作を使用します。<br /><br /> 0 = 列は文字、バイナリ、またはバリアントではありません。|  
|is_rowguidcol|**bit**|1 = 列は宣言された ROWGUIDCOL です。|  
|is_identity|**bit**|1 = 列の id 値には|  
|is_computed|**bit**|1 = 列は計算列です。|  
|is_filestream|**bit**|1 = 列は FILESTREAM 列です。|  
|is_replicated|**bit**|1 = 列はレプリケートされています。|  
|is_non_sql_subscribed|**bit**|1 = 列は SQL Server 以外のサブスクライバーを持ちます。|  
|is_merge_published|**bit**|1 = 列はマージ パブリッシュされています。|  
|is_dts_replicated|**bit**|1 = を使用して列をレプリケート[!INCLUDE[ssIS](../../includes/ssis-md.md)]です。|  
|is_xml_document|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = コンテンツは、ドキュメント フラグメントまたは列のデータ型が無効**xml**です。|  
|xml_collection_id|**int**|列のデータ型の場合は 0 以外。 **xml** XML が型指定されたとします。 この値は、列の検証 XML スキーマ名前空間を含むコレクションの ID です。<br /><br /> 0 = いいえの XML スキーマ コレクションです。|  
|default_object_id|**int**|スタンドアロン オブジェクトであるかどうかに関係なく、既定のオブジェクトの ID [sys.sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)、または、インラインの列レベルの既定の制約。 インラインの列レベルの既定のオブジェクトの parent_object_id 列は、テーブル自体への参照です。<br /><br /> 0 = 既定値はありません。|  
|rule_object_id|**int**|sys.sp_bindrule を使用して列にバインドするスタンドアロン ルールの ID です。<br /><br /> 0 = スタンドアロン ルールはありません。 列レベルの CHECK 制約を参照してください。 [sys.check_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = 列はスパース列です。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|  
|is_column_set|**bit**|1 = 列は列セットです。 詳細については、「 [スパース列の使用](../../relational-databases/tables/use-sparse-columns.md)」を参照してください。|  
|generated_always_type|**tinyint**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 列の型を表す数値 (値は常に 0 でシステム テーブルの列)。<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END<br /><br /> Always Encrypted の詳細については、次を参照してください。 [Always Encrypted &#40;データベース エンジン&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)です。|  
|generated_always_type_desc|**nvarchar (60)**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 列の型の説明テキスト (値は常に NOT_APPLICABLE システム テーブルの列)。<br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END|  
|encryption_type|**int**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 暗号化の種類:<br /><br /> 1 = 明確な暗号化<br /><br /> 2 = ランダム化された暗号化|  
|encryption_type_desc|**nvarchar(64)**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 暗号化の種類の説明。<br /><br /> ランダム化<br /><br /> DETERMINISTIC|  
|encryption_algorithm_name|**sysname**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 暗号化アルゴリズムの名前です。<br /><br /> AEAD_AES_256_CBC_HMAC_SHA_512 のみがサポートされているとします。|  
|column_encryption_key_id|**int**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> CEK の ID です。|  
|column_encryption_key_database_name|**sysname**|**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDW_md](../../includes/sssds-md.md)]です。<br /><br /> 列のデータベースと異なる場合、列の暗号化キーが存在するデータベースの名前。 列と同じデータベースに、キーが存在する場合は NULL です。|  
|is_hidden|**bit**|**適用されます**:[!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> かどうか、列が非表示を示します。<br /><br /> 0 = 正規、not 非、表示される列<br /><br /> 1 = 非表示の列|  
|is_masked|**bit**|**適用されます**:[!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。<br /><br /> 動的データ マスクによって、列がマスクされるかどうかを示します。<br /><br /> 0 = 標準、not マスクされた列<br /><br /> 1 = 列はマスクされて|  


 
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)  
  
  
