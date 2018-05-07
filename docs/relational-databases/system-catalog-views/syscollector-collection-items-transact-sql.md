---
title: syscollector_collection_items (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- syscollector_collection_items_TSQL
- syscollector_collection_items
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_collection_items view
- add data collector view
ms.assetid: a279ecd1-a59c-4315-9f08-bf221f00a465
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9e1113453ebe83221fb8dd8b9de92113bcb346c3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
|**frequency**|**int**|コレクション アイテムでデータを収集する頻度です。 NULL 値は許可されません。|  
|**parameters**|**xml**|コレクション アイテムに関連付けられたコレクター型のパラメーター化を定義します。 このコレクション アイテムの XML スキーマが検証されると、XML スキーマ (XSD) に格納されている、 **parameter_schema**の特定のコレクター型にします。 NULL 値が許可されます。 詳細については、次を参照してください。 [syscollector_collector_types &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)です。|  
  
## <a name="permissions"></a>権限  
 SELECT 権限が必要**dc_operator**、 **dc_proxy**です。  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクターのビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
