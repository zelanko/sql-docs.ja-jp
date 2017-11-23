---
title: "sys.triggers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab5788614af71fe9fa4cab1a4f22e81d5a19a6d8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  TR トリガーまたは TA トリガーであるオブジェクトごとに、1 行のデータを格納します。 DML トリガー名はスキーマ スコープあり、そのために表示される**sys.objects**です。 DDL トリガー名は親エンティティのスコープであり、このビューでのみ表示できます。  
  
 **Parent_class**と**名前**列は、データベース内のトリガーを一意に識別します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|トリガー名。 DML トリガー名はスキーマ スコープです。 DDL トリガー名は親エンティティに関してスコープされます。|  
|**object_id**|**int**|オブジェクト ID 番号。 データベース内で一意です。|  
|**parent_class**|**tinyint**|トリガーの親のクラス。<br /><br /> 0 = DDL トリガー用のデータベース<br /><br /> 1 = DML トリガー用のオブジェクトまたは列|  
|**parent_class_desc**|**nvarchar (60)**|トリガーの親のクラスの説明。<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|トリガーの親の ID。次のようになります。<br /><br /> 0 = データベースが親となっているトリガー<br /><br /> これは、DML トリガーの場合、 **object_id**テーブルまたはビュー、DML トリガーが定義されているのです。|  
|**型**|**char(2)**|オブジェクトの種類:<br /><br /> TA = アセンブリ (CLR) トリガー<br /><br /> TR = SQL トリガー|  
|**type_desc**|**nvarchar (60)**|オブジェクトの種類の説明。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|トリガーが作成された日付。|  
|**modify_date**|**datetime**|ALTER ステートメントを使用して最後にオブジェクトが変更された日付です。|  
|**is_ms_shipped**|**bit**|内部で、ユーザーの代理として作成されたトリガー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントです。|  
|**is_disabled**|**bit**|トリガーは無効。|  
|**is_not_for_replication**|**bit**|NOT FOR REPLICATION として作成されたトリガー。|  
|**is_instead_of_trigger**|**bit**|1 = INSTEAD OF トリガー<br /><br /> 0 = AFTER トリガー|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
