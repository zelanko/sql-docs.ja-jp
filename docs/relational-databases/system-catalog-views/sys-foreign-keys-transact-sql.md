---
title: "sys.foreign_keys (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2051dc726a4622f5340dc0972cf6fc38798d3f9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysforeignkeys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  FOREIGN KEY 制約があるオブジェクトごとに 1 行を含む**sys.object.type** F. を =  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**referenced_object_id**|**int**|参照されるオブジェクトの ID。|  
|**key_index_id**|**int**|参照されるオブジェクト内のキー インデックスの ID。|  
|**is_disabled**|**bit**|FOREIGN KEY 制約が無効です。|  
|**is_not_for_replication**|**bit**|FOREIGN KEY 制約は、NOT FOR REPLICATION オプションを使用して作成されました。|  
|**is_not_trusted**|**bit**|FOREIGN KEY 制約がシステムで検証されていません。|  
|**delete_referential_action**|**tinyint**|削除が発生したときに FOREIGN KEY に対して宣言された参照操作。<br /><br /> 0 = 操作なし<br /><br /> 1 = 連鎖<br /><br /> 2 = NULL に設定<br /><br /> 3 = 既定値に設定|  
|**delete_referential_action_desc**|**nvarchar (60)**|削除が発生したときに FOREIGN KEY に対して宣言された参照操作の説明。<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|更新が発生したときに FOREIGN KEY に対して宣言された参照操作。<br /><br /> 0 = 操作なし<br /><br /> 1 = 連鎖<br /><br /> 2 = NULL に設定<br /><br /> 3 = 既定値に設定|  
|**update_referential_action_desc**|**nvarchar (60)**|更新が発生したときに FOREIGN KEY に対して宣言された参照操作の説明。<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = システムによって生成された名前。<br /><br /> 0 = ユーザー指定の名前。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
