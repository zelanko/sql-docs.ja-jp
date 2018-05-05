---
title: パラメーター (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PARAMETERS_TSQL
- PARAMETERS
dev_langs:
- TSQL
helpviewer_keywords:
- PARAMETERS view
- INFORMATION_SCHEMA.PARAMETERS view
ms.assetid: 06ded0ca-7d21-4400-864a-b801e855b257
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 71aaf16dd45c0bc5efb6a2741f554b346abf4905
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-transact-sql"></a>PARAMETERS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベース内の、現在のユーザーがアクセスできるユーザー定義の関数またはストアド プロシージャのパラメーターごとに 1 行のデータを返します。 関数の場合は、戻り値情報の行も返します。  
  
 これらのビューから情報を取得するには、完全修飾の名前を指定 **INFORMATION_SCHEMA. * * * view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**SPECIFIC_CATALOG**|**nvarchar(** 128 **)**|パラメーターの基になるルーチンのカタログ名。|  
|**SPECIFIC_SCHEMA**|**nvarchar(** 128 **)**|パラメーターの基になるルーチンのスキーマ名。<br /><br /> **\*\* 重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**SPECIFIC_NAME**|**nvarchar(** 128 **)**|パラメーターの基になるルーチンの名前。|  
|**ORDINAL_POSITION**|**int**|1 から始まるパラメーターの順序を表す位置。 関数の戻り値の場合、この値は 0 です。|  
|**PARAMETER_MODE**|**nvarchar (** 10 **)**|入力パラメーターの場合は IN、出力パラメーターの場合は OUT、入出力パラメーターの場合は INOUT を返します。|  
|**IS_RESULT**|**nvarchar (** 10 **)**|関数であるルーチンの結果を表す場合は YES を返します。 それ以外の場合は NO を返します。|  
|**AS_LOCATOR**|**nvarchar (** 10 **)**|ロケーターとして宣言されている場合は YES を返します。 それ以外の場合は NO を返します。|  
|**PARAMETER_NAME**|**nvarchar(** 128 **)**|パラメーターの名前です。 関数の戻り値に対応する場合は NULL です。|  
|**DATA_TYPE**|**nvarchar(** 128 **)**|システム提供のデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|バイナリ型または文字型の最大文字数。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL を返します。|  
|**CHARACTER_OCTET_LENGTH**|**int**|バイナリ型または文字型の最大バイト数。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL を返します。|  
|**COLLATION_CATALOG**|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|**COLLATION_SCHEMA**|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|**COLLATION_NAME**|**nvarchar(** 128 **)**|パラメーターの照合順序の名前。 文字型のいずれかに該当しない場合は NULL を返します。|  
|**CHARACTER_SET_CATALOG**|**nvarchar(** 128 **)**|パラメーターの文字セットのカタログ名。 文字型のいずれかに該当しない場合は NULL を返します。|  
|**CHARACTER_SET_SCHEMA**|**nvarchar(** 128 **)**|常に NULL が返されます。|  
|**CHARACTER_SET_NAME**|**nvarchar(** 128 **)**|パラメーターの文字セットの名前。 文字型のいずれかに該当しない場合は NULL を返します。|  
|**NUMERIC_PRECISION**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの有効桁数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|概数データ、真数データ、整数データ、または通貨データの有効桁数の基数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_SCALE**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの小数点以下桁数。 それ以外の場合は NULL を返します。|  
|**DATETIME_PRECISION**|**smallint**|パラメーターの型がある場合の秒の小数部の有効桁数**datetime**または**smalldatetime**です。 それ以外の場合は NULL を返します。|  
|**INTERVAL_TYPE**|**nvarchar (** 30 **)**|NULL。 将来の使用のために予約されています。|  
|**INTERVAL_PRECISION**|**smallint**|NULL。 将来の使用のために予約されています。|  
|**USER_DEFINED_TYPE_CATALOG**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
|**USER_DEFINED_TYPE_SCHEMA**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
|**USER_DEFINED_TYPE_NAME**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
|**SCOPE_CATALOG**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
|**SCOPE_SCHEMA**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
|**SCOPE_NAME**|**nvarchar(** 128 **)**|NULL。 将来の使用のために予約されています。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.parameters & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)  
  
  
