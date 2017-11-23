---
title: "sys.schemas (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs: TSQL
helpviewer_keywords: sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c25648add8882a49964a0838315f42b5c9b61e84
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="schemas-catalog-views---sysschemas"></a>スキーマ カタログ ビュー - sys.schemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  データベース スキーマごとに 1 行のデータを保持します。  
  
> [!NOTE]  
>  データベース スキーマは、XML ドキュメントのコンテンツ モデルの定義に使用される XML スキーマとは異なります。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|スキーマの名前です。 データベース内で一意です。|  
|**schema_id**|**int**|スキーマの ID です。 データベース内で一意です。|  
|**principal_id**|**int**|このスキーマを所有するプリンシパルの ID です。|  
  
## <a name="remarks"></a>解説  
 データベース スキーマの名前空間または含まれているテーブル、ビュー、プロシージャ、関数などのオブジェクトのコンテナーとして機能しません、 **sys.objects**カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [スキーマ カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   
 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
