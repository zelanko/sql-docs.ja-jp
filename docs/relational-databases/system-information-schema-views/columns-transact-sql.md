---
title: COLUMNS (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- COLUMNS
- COLUMNS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMNS view
- INFORMATION_SCHEMA.COLUMNS view
ms.assetid: bbf7ac4a-7444-4351-a590-a9f71e0bc495
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 021e9e66b281a8bbca6d5c9e21e78ffa4069c5c9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67950799"
---
# <a name="columns-transact-sql"></a>COLUMNS (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースの現在のユーザーがアクセスできる列ごとに1行のデータを返します。  
  
 これらのビューから情報を取得するには、 **INFORMATION_SCHEMA**の完全修飾名を指定し_ます。 view_name_。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|テーブル修飾子。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|テーブルを含むスキーマの名前。<br /><br /> **&#42;&#42; の重要な &#42;&#42;** オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|テーブル名。|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|列名。|  
|**ORDINAL_POSITION**|**int**|列の識別番号。|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|列の既定値です。|  
|**IS_NULLABLE**|**varchar (** 3 **)**|列の NULL 値の許容属性。 この列が NULL を許容する場合、この列は YES を返します。 許容されない場合は NO が返されます。|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|システム提供のデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|バイナリ データ、文字データ、またはテキストおよびイメージ データの最大文字列長。<br /><br /> **xml**と大きな値の型のデータの場合は-1。 その他の場合は NULL が返されます。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。|  
|**CHARACTER_OCTET_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (バイト単位)。<br /><br /> **xml**と大きな値の型のデータの場合は-1。 その他の場合は NULL が返されます。|  
|**NUMERIC_PRECISION**|**tinyint**|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数。 その他の場合は NULL が返されます。|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|数値データの概数、正確な数値データ、整数データ、または通貨データの有効桁数の基数。 その他の場合は NULL が返されます。|  
|**NUMERIC_SCALE**|**int**|数値データの概数、正確な数値データ、整数データ、または通貨データの桁数。 その他の場合は NULL が返されます。|  
|**DATETIME_PRECISION**|**smallint**|**Datetime**および ISO **interval**データ型のサブタイプコード。 他のデータ型の場合は NULL が返されます。|  
|**CHARACTER_SET_CATALOG**|**nvarchar (** 128 **)**|**Master**を返します。 列が文字データまたは**テキスト**データ型の場合、文字セットが存在するデータベースを示します。 その他の場合は NULL が返されます。|  
|**CHARACTER_SET_SCHEMA**|**nvarchar (** 128 **)**|常に NULL が返されます。|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|この列が文字データまたは**テキスト**データ型の場合、文字セットの一意の名前を返します。 その他の場合は NULL が返されます。|  
|**COLLATION_CATALOG**|**nvarchar (** 128 **)**|常に NULL が返されます。|  
|**COLLATION_SCHEMA**|**nvarchar (** 128 **)**|常に NULL が返されます。|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|列が文字データまたは**テキスト**データ型の場合、照合順序の一意な名前を返します。 その他の場合は NULL が返されます。|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|列が別名データ型の場合、この列はユーザー定義データ型が作成されたデータベース名になります。 その他の場合は NULL が返されます。|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|列がユーザー定義データ型の場合、この列はユーザー定義データ型のスキーマの名前を返します。 その他の場合は NULL が返されます。<br /><br /> **&#42;&#42; の重要な &#42;&#42;** データ型のスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 型のスキーマを検索する唯一の信頼性のある方法は、TYPEPROPERTY 関数を使用することです。|  
|**DOMAIN_NAME**|**nvarchar (** 128 **)**|列がユーザー定義データ型の場合、この列はユーザー定義データ型の名前になります。 その他の場合は NULL が返されます。|  
  
## <a name="remarks"></a>Remarks  
 INFORMATION_SCHEMA の**ORDINAL_POSITION**列 **。列**ビューは、COLUMNS_UPDATED 関数によって返される列のビットパターンと互換性がありません。 COLUMNS_UPDATED と互換性のあるビットパターンを取得するには、INFORMATION_SCHEMA に対してクエリを実行するときに、COLUMNPROPERTY システム関数の**ColumnID**プロパティを参照する必要があり**ます。列**ビュー。 次に例を示します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT TABLE_NAME, COLUMN_NAME, COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME), COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [syscharsets &#40;Transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [構成 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [COLUMNS_UPDATED &#40;Transact-SQL&#41;](../../t-sql/functions/columns-updated-transact-sql.md)  
  
  
