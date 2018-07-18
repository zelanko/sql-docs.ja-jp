---
title: sys.numbered_procedures (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.numbered_procedures_TSQL
- numbered_procedures
- sys.numbered_procedures
- numbered_procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedures catalog view
ms.assetid: 5b6d6498-bac6-4266-94b9-d16ef5089cf0
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d16757a007b423ab6c4ed8ff8a002a73c9c583dd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37987444"
---
# <a name="sysnumberedprocedures-transact-sql"></a>sys.numbered_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  番号付きプロシージャとして作成された SQL Server ストアド プロシージャごとに 1 行のデータを保持します。 ベース ストアド プロシージャ (番号が 1 のもの) に対する行は表示されません。 ベース ストアド プロシージャのエントリで見つかるビューなど**sys.objects**と**sys.procedures**します。  
  
> [!IMPORTANT]  
>  番号付きプロシージャは非推奨とされました。 番号付きプロシージャの使用はお勧めしません。 このカタログ ビューを使用するクエリをコンパイルすると、DEPRECATION_ANNOUNCEMENT イベントが発生します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ストアド プロシージャのオブジェクト ID です。|  
|**procedure_number**|**smallint**|オブジェクト内のプロシージャの番号 (2 以降)。|  
|**definition**|**nvarchar(max)**|このプロシージャを定義する SQL Server のテキストです。<br /><br /> NULL は、暗号化されていることを示します。|  
  
> [!NOTE]  
>  XML および CLR パラメーターは、番号付きプロシージャではサポートされていません。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
