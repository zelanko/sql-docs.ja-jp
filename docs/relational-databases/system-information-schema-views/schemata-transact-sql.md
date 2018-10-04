---
title: スキーマ (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SCHEMATA_TSQL
- SCHEMATA
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
- SCHEMATA view
ms.assetid: 69617642-0f54-4b25-b62f-5f39c8909601
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a82eb8baa22c4a2f4cf66b0c4dbe9dbeb81685bc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663710"
---
# <a name="schemata-transact-sql"></a>SCHEMATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースのスキーマごとに 1 行を返します。 これらのビューから情報を取得するには、完全修飾名を指定 **INFORMATION_SCHEMA. * * * view_name*します。 インスタンスのすべてのデータベースに関する情報を取得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、クエリ、 [sys.databases &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|現在のデータベース名です。|  
|**SCHEMA_NAME**|**nvarchar(** 128 **)**|スキーマ名を返します。|  
|**SCHEMA_OWNER**|**nvarchar(** 128 **)**|スキーマ所有者名を返します。<br /><br /> **\*\* 重要な\* \*** オブジェクトのスキーマを決定 INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューを照会する方法です。|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|常に NULL が返されます。|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|常に NULL が返されます。|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|既定の文字セットの名前を返します。|  

**例**  
次の例では、master データベースにスキーマについての情報を返します。  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>参照  
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマ ビュー &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.schemas (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.syscharsets &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
