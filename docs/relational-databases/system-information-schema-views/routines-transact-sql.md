---
title: ルーチン (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- ROUTINES_TSQL
- ROUTINES
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINES view
- INFORMATION_SCHEMA.ROUTINES view
ms.assetid: c75561b2-c9a1-48a1-9afa-a5896b6454cf
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e3b1e6f0f767f202ab21048f70915b56d51eb14a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51673561"
---
# <a name="routines-transact-sql"></a>ROUTINES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースの現在のユーザーがアクセスできるストアド プロシージャと関数ごとに、1 行のデータを返します。 戻り値を記述する列は、関数のみに適用されます。 ストアド プロシージャの場合、この列は NULL になります。  
  
 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定します。*view_name*します。  
  
> [!NOTE]  
>  ROUTINE_DEFINITION 列には、関数またはストアド プロシージャを作成したソース ステートメントが格納されます。 ソース ステートメントには、埋め込み型のキャリッジ リターンが含まれる場合があります。 結果をテキスト形式で表示するアプリケーションにこの列を返す場合、ROUTINE_DEFINITION 結果に埋め込まれているキャリッジ リターンによって、結果セット全体の書式に影響が生じる可能性があります。 ROUTINE_DEFINITION 列を選択する場合は、結果セットをグリッドで返すか、ROUTINE_DEFINITION を専用のテキスト ボックスに返すなどして、埋め込み型のキャリッジ リターンを調整する必要があります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|SPECIFIC_CATALOG|**nvarchar(** 128 **)**|カタログの固有の名前。 この名前は ROUTINE_CATALOG と同じです。|  
|SPECIFIC_SCHEMA|**nvarchar(** 128 **)**|スキーマの固有の名前。<br /><br /> **\*\* 重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|SPECIFIC_NAME|**nvarchar(** 128 **)**|カタログの固有の名前。 この名前は ROUTINE_NAME と同じです。|  
|ROUTINE_CATALOG|**nvarchar(** 128 **)**|関数のカタログの名前。|  
|ROUTINE_SCHEMA|**nvarchar(** 128 **)**|関数を含むスキーマの名前。<br /><br /> **\*\* 重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|ROUTINE_NAME|**nvarchar(** 128 **)**|関数の名前。|  
|ROUTINE_TYPE|**nvarchar (** 20 **)**|ストアド プロシージャの場合は PROCEDURE、関数の場合は FUNCTION。|  
|MODULE_CATALOG|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|MODULE_SCHEMA|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|MODULE_NAME|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|UDT_CATALOG|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|UDT_SCHEMA|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|UDT_NAME|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|DATA_TYPE|**nvarchar(** 128 **)**|関数の戻り値のデータ型。 返します**テーブル**場合、テーブル値関数。|  
|CHARACTER_MAXIMUM_LENGTH|**int**|戻り値のデータ型が文字型の場合の最大文字数。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。|  
|CHARACTER_OCTET_LENGTH|**int**|戻り値のデータ型が文字型の場合の最大バイト数。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。|  
|COLLATION_CATALOG|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|COLLATION_SCHEMA|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|COLLATION_NAME|**nvarchar(** 128 **)**|戻り値の照合順序名。 文字型でない場合は NULL が返されます。|  
|CHARACTER_SET_CATALOG|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|CHARACTER_SET_SCHEMA|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|CHARACTER_SET_NAME|**nvarchar(** 128 **)**|戻り値の文字セットの名前。 文字型でない場合は NULL が返されます。|  
|NUMERIC_PRECISION|**smallint**|戻り値の数値の有効桁数。 数値型で NULL を返します。|  
|NUMERIC_PRECISION_RADIX|**smallint**|戻り値の数値の有効桁数の基数。 数値型でない場合は NULL が返されます。|  
|NUMERIC_SCALE|**smallint**|戻り値の小数点以下桁数。 数値型でない場合は NULL が返されます。|  
|DATETIME_PRECISION|**smallint**|型の場合は、戻り値の秒の小数部の有効桁数**datetime**します。 それ以外の場合は NULL を返します。|  
|INTERVAL_TYPE|**nvarchar (** 30 **)**|NULL。 将来使用するために予約されています。|  
|INTERVAL_PRECISION|**smallint**|NULL。 将来使用するために予約されています。|  
|TYPE_UDT_CATALOG|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|TYPE_UDT_SCHEMA|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|TYPE_UDT_NAME|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|SCOPE_CATALOG|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|SCOPE_SCHEMA|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|SCOPE_NAME|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|MAXIMUM_CARDINALITY|**bigint**|NULL。 将来使用するために予約されています。|  
|DTD_IDENTIFIER|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|ROUTINE_BODY|**nvarchar (** 30 **)**|[!INCLUDE[tsql](../../includes/tsql-md.md)] 関数の場合は SQL、外部で作成された関数の場合は EXTERNAL。<br /><br /> 関数は常に SQL です。|  
|ROUTINE_DEFINITION|**nvarchar (** 4000 **)**|関数またはストアド プロシージャが暗号化されていない場合、関数またはストアド プロシージャの定義テキストの最初の 4,000 文字を返します。 それ以外の場合は NULL を返します。<br /><br /> 完全な定義を取得するためには、クエリ、 [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)関数または内の definition 列、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビューです。|  
|EXTERNAL_NAME|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|EXTERNAL_LANGUAGE|**nvarchar (** 30 **)**|NULL。 将来使用するために予約されています。|  
|PARAMETER_STYLE|**nvarchar (** 30 **)**|NULL。 将来使用するために予約されています。|  
|IS_DETERMINISTIC|**nvarchar (** 10 **)**|ルーチンが決定的な場合は YES が返されます。<br /><br /> ルーチンが非決定的な場合は NO が返されます。<br /><br /> ストアド プロシージャの場合は常に NO が返されます。|  
|SQL_DATA_ACCESS|**nvarchar (** 30 **)**|次の値のいずれか。<br /><br /> NONE = 関数に SQL が含まれません。<br /><br /> CONTAINS = 関数に SQL が含まれる可能性があります。<br /><br /> READS = 関数で SQL データが読み取られる可能性があります。<br /><br /> MODIFIES = 関数で SQL データが変更される可能性があります。<br /><br /> すべての関数に READS、すべてのストアド プロシージャに MODIFIES が返されます。|  
|IS_NULL_CALL|**nvarchar (** 10 **)**|いずれかの引数が NULL の場合、ルーチンを呼び出すことができるかどうかを示します。|  
|SQL_PATH|**nvarchar(** 128 **)**|NULL。 将来使用するために予約されています。|  
|SCHEMA_LEVEL_ROUTINE|**nvarchar (** 10 **)**|スキーマレベルの関数の場合は YES、スキーマレベルの関数でない場合は NO。<br /><br /> 常に YES が返されます。|  
|MAX_DYNAMIC_RESULT_SETS|**smallint**|ルーチンによって返される動的結果セットの最大数。<br /><br /> 関数の場合は 0 が返されます。|  
|IS_USER_DEFINED_CAST|**nvarchar (** 10 **)**|ユーザー定義キャスト関数の場合は YES、ユーザー定義キャスト関数でない場合は NO。<br /><br /> 常に NO を返します。|  
|IS_IMPLICITLY_INVOCABLE|**nvarchar (** 10 **)**|ルーチンが暗黙的に呼び出し可能な場合は YES、関数が暗黙的に呼び出しできない場合は NO。<br /><br /> 常に NO を返します。|  
|CREATED|**datetime**|ルーチンが作成された時刻。|  
|LAST_ALTERED|**datetime**|関数が最後に変更された時刻。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)  
  
  
