---
title: "ドメイン (TRANSACT-SQL) |Microsoft ドキュメント"
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
- DOMAINS_TSQL
- DOMAINS
dev_langs:
- TSQL
helpviewer_keywords:
- DOMAINS view
- INFORMATION_SCHEMA.DOMAINS view
ms.assetid: f0b734d5-816f-4b10-a60c-615931b515c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ab3416e33aa79bcb499451b5b4ffa7b50fe4efd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="domains-transact-sql"></a>DOMAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースの現在のユーザーがアクセスできる別名データ型ごとに 1 行のデータを返します。  
  
 これらのビューから情報を取得するには、完全修飾の名前を指定**INFORMATION_SCHEMA** 。*view_name*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**nvarchar (**128**)**|別名データ型が存在するデータベース。|  
|**DOMAIN_SCHEMA**|**nvarchar (**128**)**|別名データ型を含むスキーマの名前。<br /><br /> **\*\*重要な\* \*** データ型のスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 型のスキーマを調べる唯一の信頼性のある方法は、TYPEPROPERTY 関数を使用する方法です。|  
|**ドメイン名**|**sysname**|別名データ型。|  
|**DATA_TYPE**|**sysname**|システム提供のデータ型。|  
|**CHARACTER_MAXIMUM_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (文字単位)。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL が返されます。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。|  
|**CHARACTER_OCTET_LENGTH**|**int**|バイナリ データ、文字データ、またはテキスト/イメージ データの最大長 (バイト単位)。<br /><br /> 場合は-1 **xml**と大きな値型のデータ。 それ以外の場合は NULL が返されます。|  
|**COLLATION_CATALOG**|**varchar (**6**)**|常に NULL が返されます。|  
|**COLLATION_SCHEMA**|**varchar (**3**)**|常に NULL が返されます。|  
|**COLLATION_NAME**|**nvarchar (**128**)**|列が文字データの場合は、並べ替え順序の一意の名前を返しますまたは**テキスト**データ型。 それ以外の場合は NULL が返されます。|  
|**CHARACTER_SET_CATALOG**|**varchar (**6**)**|返します**マスター**です。 列が文字データの場合、文字セットが、配置されているデータベースを示すこのまたは**テキスト**データ型。 それ以外の場合は NULL が返されます。|  
|**CHARACTER_SET_SCHEMA**|**varchar (**3**)**|常に NULL が返されます。|  
|**CHARACTER_SET_NAME**|**nvarchar (**128**)**|この列が文字データの場合、文字セットの一意の名前を返しますまたは**テキスト**データ型。 それ以外の場合は NULL が返されます。|  
|**NUMERIC_PRECISION**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの有効桁数。 それ以外の場合は NULL が返されます。|  
|**NUMERIC_PRECISION_RADIX**|**smallint**|概数データ、真数データ、整数データ、または通貨データの有効桁数の基数。 それ以外の場合は NULL が返されます。|  
|**NUMERIC_SCALE**|**tinyint**|概数データ、真数データ、整数データ、または通貨データの小数点以下桁数。 それ以外の場合は NULL が返されます。|  
|**DATETIME_PRECISION**|**smallint**|サブタイプ コード**datetime**と ISO**間隔**データ型。 その他のデータ型の場合は、NULL が返されます。|  
|**DOMAIN_DEFAULT**|**nvarchar (**4000**)**|定義の実際のテキスト[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.syscharsets &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.types &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
