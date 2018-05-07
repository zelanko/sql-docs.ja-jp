---
title: sys.dm_exec_describe_first_result_set_for_object (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_describe_first_result_set_for_object_TSQL
- sys.dm_exec_describe_first_result_set_for_object
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_describe_first_result_set_for_object catalog view
ms.assetid: 63b0fde7-95d7-4ad7-a219-a9feacf1bd89
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7be8e26fbfc368de448d465dca7750998f1cccaa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecdescribefirstresultsetforobject-transact-sql"></a>sys.dm_exec_describe_first_result_set_for_object (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  この動的管理関数には、@object_idをパラメーターとしてその ID を持つモジュールの最初の結果のメタデータについて説明します @object_idの ID を指定することができます、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガーします。 その他のオブジェクト (ビュー、テーブル、関数、または CLR プロシージャ) などの ID の場合は、結果のエラー列にエラーが記載されます。  
  
 **sys.dm_exec_describe_first_result_set_for_object** has the same result set definition as [sys.dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md) and is similar to [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_exec_describe_first_result_set_for_object   
    ( @object_id , @include_browse_information )  
```  
  
## <a name="arguments"></a>引数  
 *@object_id*  
 @object_idの[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャまたは[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガーします。 @object_id 型は、 **int**です。  
  
 *@include_browse_information*  
 @include_browse_information 型は、**ビット**です。 1 に設定すると、各クエリは FOR BROWSE オプションが指定されているように分析されます。 追加のキー列とソース テーブル情報を返します。  
  
## <a name="table-returned"></a>返されるテーブル  
 この共通メタデータは、結果のメタデータの各列に対する 1 行の結果セットとして返されます。 各行には、列の種類と NULL 値の許容属性が次のセクションに示す形式で記述されます。 最初のステートメントは、各コントロールのパスが存在しない場合は、0 行を含む結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**is_hidden**|**bit**|この列が、参照および情報提供の目的で追加された余分な列で、実際に結果セットには表示されないかどうかを示します。|  
|**column_ordinal**|**int**|結果セット内の列の位置を示す序数を格納します。 最初の列の位置は、1 つとして指定されます。|  
|**name**|**sysname**|列の名前を確認できる場合は、その名前を格納します。 それ以外の場合は NULL です。|  
|**is_nullable**|**bit**|Null を許可する確認できない場合、列が列に Null を許容しない場合は 0 と 1、Null を許可する場合は、値 1 に含まれています。|  
|**system_type_id**|**int**|Sys.types で指定された列のデータ型の system_type_id を格納します。 CLR 型の場合は、system_type_name 列が NULL を返しても、この列は値 240 を返します。|  
|**system_type_name**|**nvarchar (256)**|データ型の名前を格納します。 列のデータ型に指定されている引数 (長さ、有効桁数、小数点以下桁数など) を含みます。 データ型がユーザー定義の別名型の場合は、基になるシステム型がここで指定されます。 CLR ユーザー定義型の場合は、この列には NULL が返されます。|  
|**max_length**|**smallint**|列の最大長 (バイト単位) です。<br /><br /> -1 = 列のデータ型は**varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**です。<br /><br /> **テキスト**、列、 **max_length**値は 16 かによって設定された値になります**sp_tableoption 'text in row'** です。|  
|**有効桁数 (precision)**|**tinyint**|数値ベースの場合は、列の有効桁数です。 それ以外の場合は 0 を返します。|  
|**scale**|**tinyint**|数値ベースの場合は、列の小数点以下桁数です。 それ以外の場合は 0 を返します。|  
|**collation_name**|**sysname**|文字ベースの場合は、列の照合順序の名前です。 それ以外の場合は NULL を返します。|  
|**user_type_id**|**int**|CLR 型と別名型の場合、sys.types で指定された列のデータ型の user_type_id を格納します。 それ以外の場合は NULL です。|  
|**user_type_database**|**sysname**|CLR 型と別名型の場合、その型が定義されたデータベースの名前を格納します。 それ以外の場合は NULL です。|  
|**user_type_schema**|**sysname**|CLR 型と別名型の場合、その型が定義されたスキーマの名前を格納します。 それ以外の場合は NULL です。|  
|**user_type_name**|**sysname**|CLR 型と別名型の場合、その型の名前を格納します。 それ以外の場合は NULL です。|  
|**assembly_qualified_type_name**|**nvarchar (4000)**|CLR 型の場合、その型を定義するアセンブリの名前とクラスを返します。 それ以外の場合は NULL です。|  
|**xml_collection_id**|**int**|sys.columns で指定された列のデータ型の xml_collection_id を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**xml_collection_database**|**sysname**|この型に関連付けられている XML スキーマ コレクションが定義されているデータベースを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**xml_collection_schema**|**sysname**|この型に関連付けられている XML スキーマ コレクションが定義されているスキーマを格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**xml_collection_name**|**sysname**|この型に関連付けられている XML スキーマ コレクションの名前を格納します。 この列は、返される型が XML スキーマ コレクションに関連付けられていない場合は NULL を返します。|  
|**is_xml_document**|**bit**|返されたデータ型が XML で、その型が XML フラグメントではなく完全な XML ドキュメント (ルート ノードを含む) であると保証される場合、1 を返します。 それ以外の場合は 0 を返します。|  
|**is_case_sensitive**|**bit**|列がない場合に区別して文字列型と 0 の場合は、1 を返します。|  
|**is_fixed_length_clr_type**|**bit**|この列が固定長の CLR 型の場合は 1、それ以外の場合は 0 を返します。|  
|**source_server**|**sysname**|この結果内の列によって返された元のサーバーの名前です (リモート サーバーから発生する場合)。 Sys.servers に表示される、名前が与えられます。  ローカルのサーバーで、この列が発生した場合、またはできない場合、NULL を返しますには、元のサーバーが決定されます。 参照情報が要求された場合にのみ設定されます。|  
|**source_database**|**sysname**|この結果内の列によって返された元のデータベースの名前です。 データベースを特定できない場合は NULL を返します。 参照情報が要求された場合にのみ設定されます。|  
|**source_schema**|**sysname**|この結果内の列によって返された元のスキーマの名前です。 スキーマを特定できない場合は NULL を返します。 参照情報が要求された場合にのみ設定されます。|  
|**source_table**|**sysname**|この結果内の列によって返された元のテーブルの名前です。 テーブルを特定できない場合は NULL を返します。 参照情報が要求された場合にのみ設定されます。|  
|**source_column**|**sysname**|この結果内の列によって返された元の列の名前です。 列を特定できない場合は NULL を返します。 参照情報が要求された場合にのみ設定されます。|  
|**is_identity_column**|**bit**|この列が ID 列の場合は 1、それ以外の場合は 0 を返します。 ID 列であることを確認できない場合は NULL を返します。|  
|**is_part_of_unique_key**|**bit**|この列が一意インデックス (一意制約と主キー制約を含む) の一部である場合は 1、それ以外の場合は 0 を返します。 一意インデックスの一部であることを確認できない場合は NULL を返します。 参照情報が要求された場合にのみ設定されます。|  
|**is_updateable**|**bit**|この列が更新可能である場合は 1、それ以外の場合は 0 を返します。 更新可能であることを確認できない場合は NULL を返します。|  
|**is_computed_column**|**bit**|この列が計算列の場合は 1、それ以外の場合は 0 を返します。 この列が計算列を確認できない場合は、NULL を返します。|  
|**is_sparse_column_set**|**bit**|この列がスパース列の場合は 1、それ以外の場合は 0 を返します。 スパース列セットの一部であることを確認できない場合は NULL を返します。|  
|**ordinal_in_order_by_list**|**smallint**|ORDER BY リストにおけるこの列の位置を返します。この列が ORDER BY リストにない場合、または ORDER BY リストを一意に特定できない場合は NULL を返します。|  
|**order_by_list_length**|**smallint**|ORDER BY リストの長さを返します。 ORDER BY リストがない場合、または ORDER BY リストを一意に特定できない場合は NULL を返します。 この値は、sp_describe_first_result_set によって返されるすべての行に対して同じであることに注意してください。|  
|**order_by_is_descending**|**smallint NULL**|Ordinal_in_order_by_list が NULL でない場合、 **order_by_is_descending**列は、この列の ORDER BY 句の方向を報告します。 それ以外の場合は、NULL が報告されます。|  
|**error_number**|**int**|関数によって返されるエラー番号が格納されます。 列でエラーが発生しなかった場合は、NULL が格納されます。|  
|**error_severity**|**int**|関数によって返される重大度が格納されます。 列でエラーが発生しなかった場合は、NULL が格納されます。|  
|**error_state**|**int**|関数によって返される状態メッセージが格納されます。 エラーが発生しなかった場合は、 NULL が格納されます。|  
|**error_message**|**nvarchar(4096)**|関数によって返されるメッセージが格納されます。 エラーが発生しなかった場合は、NULL が格納されます。|  
|**error_type**|**int**|返されるエラーを表す整数が格納されます。 error_type_desc にマップされます。 解説の下の一覧を参照してください。|  
|**error_type_desc**|**nvarchar(60)**|返されるエラーを表す短い大文字の文字列が格納されます。 error_type にマップされます。 解説の下の一覧を参照してください。|  
  
## <a name="remarks"></a>解説  
 この関数と同じアルゴリズムを使用して**sp_describe_first_result_set**です。 詳細については、次を参照してください。 [sp_describe_first_result_set & #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)。  
  
 次の表に、エラーの種類とその説明を示します。  
  
|error_type|error_type|Description|  
|-----------------|-----------------|-----------------|  
|1|MISC|他の項目に記載されていないすべてのエラー。|  
|2|SYNTAX|バッチ内で構文エラーが発生しました。|  
|3|CONFLICTING_RESULTS|2 つの有効な最初のステートメント間に競合があるため、結果を特定できませんでした。|  
|4|DYNAMIC_SQL|動的 SQL が最初の結果を返す可能性があるため、結果を特定できませんでした。|  
|5|CLR_PROCEDURE|結果でしたを特定できないため、CLR ストアド プロシージャは、最初の結果を返す可能性がある可能性があります。|  
|6|CLR_TRIGGER|CLR トリガーが最初の結果を返す可能性があるため、結果を特定できませんでした。|  
|7|EXTENDED_PROCEDURE|拡張ストアド プロシージャが最初の結果を返す可能性があるため、結果を特定できませんでした。|  
|8|UNDECLARED_PARAMETER|1 つまたは複数の結果セットの列のデータ型が、宣言されていないパラメーターに依存している可能性があるため、結果を特定できませんでした。|  
|9|RECURSION|バッチに再帰的なステートメントが含まれているため、結果を特定できませんでした。|  
|10|TEMPORARY_TABLE|バッチは、一時テーブルが含まれておりでサポートされていない、結果を判別できませんでした**sp_describe_first_result_set**です。|  
|11|UNSUPPORTED_STATEMENT|サポートされていないステートメントがバッチに含まれているために、結果を判別できませんでした**sp_describe_first_result_set** (FETCH、REVERT などです。)。|  
|12|OBJECT_ID_NOT_SUPPORTED|@object_id関数に渡されるは (つまり、ストアド プロシージャではありません) はサポートされていません|  
|13|OBJECT_ID_DOES_NOT_EXIST|@object_idに渡された関数がシステム カタログに見つかりませんでした。|  
  
## <a name="permissions"></a>権限  
 実行する権限が必要です、@tsql引数。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-metadata-with-and-without-browse-information"></a>A. 参照情報ありおよび参照情報なしでメタデータを返す  
 次の例では、次の 2 つの結果セットを返す TestProc2 をという名前のストアド プロシージャを作成します。 この例では、ことを示します、 **sys.dm_exec_describe_first_result_set**手順、および参照情報なしの最初の結果に関する情報を返します。  
  
```  
CREATE PROC TestProc2  
AS  
SELECT object_id, name FROM sys.objects ;  
SELECT name, schema_id, create_date FROM sys.objects ;  
GO  
  
SELECT * FROM sys.dm_exec_describe_first_result_set_for_object(OBJECT_ID('TestProc2'), 0) ;  
SELECT * FROM sys.dm_exec_describe_first_result_set_for_object(OBJECT_ID('TestProc2'), 1) ;  
GO  
```  
  
### <a name="b-combining-the-sysdmexecdescribefirstresultsetforobject-function-and-a-table-or-view"></a>B. sys.dm_exec_describe_first_result_set_for_object 関数をテーブルまたはビューと組み合わせる  
 次の例では、両方、sys.procedures システム カタログ ビューおよび**sys.dm_exec_describe_first_result_set_for_object**関数内のすべてのストアド プロシージャの結果セットのメタデータを表示、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースです。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT p.name, r.*   
FROM sys.procedures AS p  
CROSS APPLY sys.dm_exec_describe_first_result_set_for_object(p.object_id, 0) AS r;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [sp_describe_first_result_set &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md)   
 [sp_describe_undeclared_parameters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md)   
 [sys.dm_exec_describe_first_result_set &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql.md)  
  
  
