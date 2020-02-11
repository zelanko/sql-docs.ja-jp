---
title: sys. triggers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 33eb5a1c4176041d64ba60a3a684b75bc4816350
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091929"
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  TR トリガーまたは TA トリガーであるオブジェクトごとに、1 行のデータを格納します。 DML トリガー名はスキーマスコープであるため、 **sys. オブジェクト**に表示されます。 DDL トリガー名は親エンティティによってスコープが設定され、このビューでのみ表示されます。  
  
 **Parent_class**列と**name**列は、データベース内のトリガーを一意に識別します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|トリガー名。 DML トリガー名はスキーマ スコープです。 DDL トリガーの名前は、親エンティティに対してスコープが設定されます。|  
|**object_id**|**int**|オブジェクト ID 番号。 データベース内で一意です。|  
|**parent_class**|**tinyint**|トリガーの親のクラス。<br /><br /> 0 = DDL トリガー用のデータベース<br /><br /> 1 = DML トリガー用のオブジェクトまたは列|  
|**parent_class_desc**|**nvarchar (60)**|トリガーの親クラスの説明です。<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|トリガーの親の ID。次に例を示します。<br /><br /> 0 = データベースが親となっているトリガー<br /><br /> DML トリガーの場合、これは DML トリガーが定義されているテーブルまたはビューの**object_id**です。|  
|**type**|**char (2)**|オブジェクトの種類:<br /><br /> TA = アセンブリ (CLR) トリガー<br /><br /> TR = SQL トリガー|  
|**type_desc**|**nvarchar (60)**|オブジェクトの種類の説明。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**DATETIME**|トリガーが作成された日付。|  
|**modify_date**|**DATETIME**|ALTER ステートメントを使用してオブジェクトが最後に変更された日付。|  
|**is_ms_shipped**|**bit**|内部[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントによってユーザーの代理として作成されたトリガー。|  
|**is_disabled**|**bit**|トリガーは無効です。|  
|**is_not_for_replication**|**bit**|トリガーは NOT FOR REPLICATION として作成されました。|  
|**is_instead_of_trigger**|**bit**|1 = INSTEAD OF トリガー<br /><br /> 0 = AFTER トリガー|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]詳細については、「[メタデータ表示の構成](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
