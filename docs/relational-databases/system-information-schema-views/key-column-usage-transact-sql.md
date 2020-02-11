---
title: KEY_COLUMN_USAGE (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- KEY_COLUMN_USAGE_TSQL
- KEY_COLUMN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.KEY_COLUMN_USAGE view
- KEY_COLUMN_USAGE view
ms.assetid: ec1e18c2-63a1-4d2b-ba9a-c13857403782
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d38e6ae0eaf7ed6015834052067db28993cbcccd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948610"
---
# <a name="key_column_usage-transact-sql"></a>KEY_COLUMN_USAGE (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベース内のキーとして制約されている列ごとに1行のデータを返します。 この情報スキーマビューでは、現在のユーザーがアクセス許可を持っているオブジェクトに関する情報が返されます。  
  
 これらのビューから情報を取得するには、INFORMATION_SCHEMA の完全修飾名を指定し**ます。**_view_name_。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|制約修飾子。|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|制約を含むスキーマの名前。<br /><br /> <strong> \*重要\* \* </strong>オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**CONSTRAINT_NAME**|**nvarchar (** 128 **)**|制約名。|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|テーブル修飾子。|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|テーブルを含むスキーマの名前。<br /><br /> <strong> \*重要\* \* </strong>オブジェクトのスキーマを決定するために INFORMATION_SCHEMA ビューを使用しないでください。 オブジェクトのスキーマを調べる唯一の信頼性のある方法は、sys.objects カタログ ビューに対するクエリを実行する方法です。|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|テーブル名。|  
|**COLUMN_NAME**|**nvarchar (** 128 **)**|列名。|  
|**ORDINAL_POSITION**|**int**|列の序数の位置。|  
  
## <a name="see-also"></a>参照  
 [システムビュー &#40;Transact-sql&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [情報スキーマビュー &#40;Transact-sql&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [&#40;Transact-sql&#41;の列](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [SQL&#41;&#40;Transact-sql のインデックス](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [foreign_keys &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-foreign-keys-transact-sql.md)   
 [key_constraints &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
  
