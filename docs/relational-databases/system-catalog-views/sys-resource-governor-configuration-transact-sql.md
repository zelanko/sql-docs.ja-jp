---
title: sys.resource_governor_configuration (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56ab892143c87ae53f2b9276247f06224ba83d10
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysresourcegovernorconfiguration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リソース ガバナーの格納されている状態を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|メタデータに格納されている分類子関数の ID。 NULL 値は許可されません。<br /><br /> **注**この関数は、新しいセッションを分類するために使用し、作業負荷を適切なワークロード グループにルーティングする規則を使用します。 詳細については、「[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。|  
|is_enabled|**bit**|リソース ガバナーの現在の状態を示します。<br /><br /> 0 = リソース ガバナーが有効になっていません。<br /><br /> 1 = リソース ガバナーを有効にします。<br /><br /> NULL 値は許可されません。|  
|max_outstanding_io_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ボリュームごとの未処理の I/O の最大数。|  
  
## <a name="remarks"></a>解説  
 カタログ ビューには、メタデータに格納されているリソース ガバナー構成が表示されます。 メモリ内の構成を表示するには、対応する動的管理ビューを使用します。  
  
## <a name="permissions"></a>権限  
 内容を表示するには VIEW ANY DEFINITION 権限が必要です。内容を変更するには CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、リソース ガバナーの構成の格納されているメタデータの値とメモリ内の値を取得して比較する方法を示します。  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_configuration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  
