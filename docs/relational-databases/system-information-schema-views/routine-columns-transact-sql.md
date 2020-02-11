---
title: ROUTINE_COLUMNS (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5b0ed500b1217ae70dca72ab6eab64ab661c22ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078534"
---
# <a name="routine_columns-transact-sql"></a>ROUTINE_COLUMNS (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内の、現在のユーザーがアクセスできるテーブル値関数によって返される列ごとに、1 行のデータを返します。  
  
 このビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|テーブル値関数のカタログ名またはデータベース名。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|テーブル値関数を含むスキーマの名前。<br /><br /> <strong> \*重要\* \* </strong>オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|テーブル値関数の名前。|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|列名。|  
|**ORDINAL_POSITION**|**int**|列の識別番号。|  
|**COLUMN_DEFAULT**|**nvarchar (** 4000 **)**|列の既定値です。|  
|**IS_NULLABLE**|**varchar (** 3 **)**|この列が NULL 値を許容する場合、は YES を返します。 それ以外の場合、は NO を返します。|  
|**DATA_TYPE**|**nvarchar (** 128 **)**|システム提供のデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|バイナリデータ、文字データ、またはテキストおよびイメージデータの最大長 (文字数)。<br /><br /> **xml**と大きな値の型のデータの場合は-1。 それ以外の場合は NULL を返します。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。|  
|**CHARACTER_OCTET_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (バイト単位)。<br /><br /> **xml**と大きな値の型のデータの場合は-1。 それ以外の場合は NULL を返します。|  
|**NUMERIC_PRECISION**|**tinyint**|概数データ、正確な数値データ、整数データ、または通貨データの有効桁数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|概数データ、真数データ、整数データ、または通貨データの有効桁数の基数。 それ以外の場合は NULL を返します。|  
|**NUMERIC_SCALE**|**tinyint**|概数型データ、真数データ、整数データ、または通貨データの小数点以下桁数。 それ以外の場合は NULL を返します。|  
|**DATETIME_PRECISION**|**smallint**|**Datetime**および ISO**整数**データ型のサブタイプコード。 その他のデータ型の場合は、NULL を返します。|  
|**CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|**Master**を返します。 これは、列が文字データまたは**テキスト**データ型の場合に、文字セットが配置されているデータベースを示します。 それ以外の場合は NULL を返します。|  
|**CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|常に NULL が返されます。|  
|**CHARACTER_SET_NAME**|**nvarchar (** 128 **)**|この列が文字データまたは**テキスト**データ型の場合、文字セットの一意の名前を返します。 それ以外の場合は NULL を返します。|  
|**COLLATION_CATALOG**|**varchar (** 6 **)**|常に NULL が返されます。|  
|**COLLATION_SCHEMA**|**varchar (** 3 **)**|常に NULL が返されます。|  
|**COLLATION_NAME**|**nvarchar (** 128 **)**|列が文字データまたは**テキスト**データ型の場合、並べ替え順序の一意な名前を返します。 それ以外の場合は NULL を返します。|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|列が別名データ型の場合、この列はユーザー定義データ型が作成されたデータベース名になります。 それ以外の場合は NULL を返します。|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|列がユーザー定義データ型の場合、この列はユーザー定義データ型を含むスキーマの名前です。 それ以外の場合は NULL を返します。<br /><br /> <strong> \*重要\* \* </strong>オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**DOMAIN_NAME**|**nvarchar (** 128 **)**|列がユーザー定義データ型の場合、この列はユーザー定義データ型の名前になります。 それ以外の場合は NULL を返します。|  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
