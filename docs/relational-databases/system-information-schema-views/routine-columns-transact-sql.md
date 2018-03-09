---
title: "ROUTINE_COLUMNS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ROUTINE_COLUMNS_TSQL
- ROUTINE_COLUMNS
dev_langs:
- TSQL
helpviewer_keywords:
- ROUTINE_COLUMNS view
- INFORMATION_SCHEMA.ROUTINE_COLUMNS view
ms.assetid: 91dbc61b-e4c0-4826-976c-b2fce88b7793
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3815c6db044ec66bae8eddd7bceb6ad69f29db61
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="routinecolumns-transact-sql"></a>ROUTINE_COLUMNS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内の、現在のユーザーがアクセスできるテーブル値関数によって返される列ごとに、1 行のデータを返します。  
  
 このビューから情報を取得するには、完全修飾の名前を指定**INFORMATION_SCHEMA** 。*view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|テーブル値関数のカタログ名またはデータベース名です。|  
|**TABLE_SCHEMA、**|**nvarchar (**128**)**|テーブル値関数を含むスキーマ名です。<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**nvarchar (**128**)**|テーブル値関数の名前です。|  
|**COLUMN_NAME**|**nvarchar (**128**)**|列名|  
|**ORDINAL_POSITION**|**int**|列の識別番号。|  
|**COLUMN_DEFAULT**|**nvarchar (**4000**)**|列の既定値です。|  
|**によって IS_NULLABLE**|**varchar (**3**)**|この列が NULL 値を許可する場合は YES を返します。 それ以外の場合は NO を返します。|  
|**DATA_TYPE**|**nvarchar (**128**)**|システム提供のデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (文字単位)。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL を返します。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。|  
|**CHARACTER_OCTET_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (バイト単位)。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL を返します。|  
|**NUMERIC_PRECISION**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの有効桁数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|概数データ、真数データ、整数データ、または通貨データの有効桁数の基数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_SCALE**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの小数点以下桁数。 それ以外の場合は NULL を返します。|  
|**DATETIME_PRECISION**|**smallint**|サブタイプ コード**datetime**と ISO**整数**データ型。 他のデータ型の場合は NULL を返します。|  
|**CHARACTER_SET_CATALOG**|**varchar (**6**)**|返します**マスター**です。 これは、文字セットが配置されている列が文字データの場合、データベースを示しますまたは**テキスト**データ型。 それ以外の場合は NULL を返します。|  
|**CHARACTER_SET_SCHEMA**|**varchar (**3**)**|常に NULL が返されます。|  
|**CHARACTER_SET_NAME**|**nvarchar (**128**)**|この列が文字データの場合、文字セットの一意の名前を返しますまたは**テキスト**データ型。 それ以外の場合は NULL を返します。|  
|**COLLATION_CATALOG**|**varchar (**6**)**|常に NULL が返されます。|  
|**COLLATION_SCHEMA**|**varchar (**3**)**|常に NULL が返されます。|  
|**COLLATION_NAME**|**nvarchar (**128**)**|列が文字データの場合は、並べ替え順序の一意の名前を返しますまたは**テキスト**データ型。 それ以外の場合は NULL を返します。|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|列が別名データ型の場合、この列はユーザー定義のデータ型が作成されたデータベースの名前になります。 それ以外の場合は NULL を返します。|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|列がユーザー定義データ型の場合、この列はユーザー定義データ型を含むスキーマの名前です。 それ以外の場合は NULL を返します。<br /><br /> **\*\*重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**ドメイン名**|**nvarchar (**128**)**|列がクエリ アナライザーの場合、この列はクエリ アナライザーの名前になります。 それ以外の場合は NULL を返します。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
