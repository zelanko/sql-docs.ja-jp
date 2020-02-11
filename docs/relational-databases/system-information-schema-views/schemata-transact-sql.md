---
title: スキーマ (Transact-sql) |Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 16b2a23c696b4da405e4983689217abb15074f03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078431"
---
# <a name="schemata-transact-sql"></a>スキーマ (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースのスキーマごとに1行のデータを返します。 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。 のインスタンス内のすべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースに関する情報を取得するには、 [transact-sql&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログビューを &#40;て、データベースに対してクエリを実行します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**CATALOG_NAME**|**sysname**|現在のデータベースの名前|  
|**SCHEMA_NAME**|**nvarchar (** 128 **)**|スキーマの名前を返します。|  
|**SCHEMA_OWNER**|**nvarchar (** 128 **)**|スキーマの所有者の名前。<br /><br /> **&#42;&#42; の重要な &#42;&#42;** オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを検索する唯一の信頼性のある方法は、のカタログビューに対してクエリを実行することです。|  
|**DEFAULT_CHARACTER_SET_CATALOG**|**varchar (** 6 **)**|常に NULL が返されます。|  
|**DEFAULT_CHARACTER_SET_SCHEMA**|**varchar (** 3 **)**|常に NULL が返されます。|  
|**DEFAULT_CHARACTER_SET_NAME**|**sysname**|既定の文字セットの名前を返します。|  

**例**  
次の例では、master データベースのスキーマに関する情報を返します。  
```sql  
SELECT * FROM master.INFORMATION_SCHEMA.SCHEMATA;
```  

## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [データベース &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [スキーマ &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [syscharsets &#40;Transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-syscharsets-transact-sql.md)  
  
  
