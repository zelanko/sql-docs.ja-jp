---
title: "syscollector_collection_items (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs: TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 62eb418671f74d34a27d1098b4be908ed1130d57
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syscollectorcollectionitems-transact-sql"></a>syscollector_collection_items (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セット内のアイテムに関する情報を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**collection_set_id**|**int**|コレクション セットを識別します。 NULL 値は許可されません。|  
|**collection_item_id**|**int**|コレクション セット内のアイテムを識別します。 NULL 値は許可されません。|  
|**collector_type_uid**|**uniqueidentifier**|コレクター型の識別に使用する GUID です。 NULL 値は許可されません。|  
|**name**|**nvarchar (4000)**|コレクション セットの名前です。 NULL 値が許可されます。|  
|**頻度**|**int**|コレクション アイテムでデータを収集する頻度です。 NULL 値は許可されません。|  
|**パラメーター**|**xml**|コレクション アイテムに関連付けられたコレクター型のパラメーター化を定義します。 このコレクション アイテムの XML スキーマが検証されると、XML スキーマ (XSD) に格納されている、 **parameter_schema**の特定のコレクター型にします。 NULL 値が許可されます。 詳細については、次を参照してください。 [syscollector_collector_types (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md).|  
  
## <a name="permissions"></a>Permissions  
 SELECT 権限が必要**dc_operator**、 **dc_proxy**です。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
