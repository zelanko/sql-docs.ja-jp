---
title: sys.dm_resource_governor_configuration (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_resource_governor_configuration_TSQL
- dm_resource_governor_configuration
- sys.dm_resource_governor_configuration
- sys.dm_resource_governor_configuration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_configuration dynamic management view
ms.assetid: c89aab6a-0434-4ce6-af8c-f8a1a3284e38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 00b425e5efd441868bfa763fe544827bd7279dc2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067789"
---
# <a name="sysdmresourcegovernorconfiguration-transact-sql"></a>sys.dm_resource_governor_configuration (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リソース ガバナーの現在のメモリ内の構成状態を含む行を返します。  
  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|リソース ガバナーが現在使用されている分類子関数の ID。 関数が使用されていない場合は、値 0 を返します。 NULL 値は許可されません。<br /><br /> **注:** この関数は、新しい要求を分類するために使用し、規則を使用して、適切なワークロード グループにこれらの要求をルートします。 詳細については、「[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。|  
|is_reconfiguration_pending|**bit**|グループまたはプールへの変更が、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントで行われたがメモリ内の構成に適用されていないかどうかを示します。 返される値は次のいずれかです。<br /><br /> 0: 再構成ステートメントは必要ありません。<br /><br /> 1: 保留中の構成変更を適用するため、再構成ステートメントまたはサーバーの再起動が必要です。<br /><br /> **注:** 返される値は常にリソース ガバナーが無効にした場合は 0。<br /><br /> NULL 値は許可されません。|  
|max_outstanding_io_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ボリュームごとの未処理の I/O の最大数。|  
  
## <a name="remarks"></a>コメント  
 この動的管理ビューは、メモリ内の構成を示しています。 格納されている構成メタデータを表示するには、対応するカタログ ビューを使用します。  
  
 次の例では、取得し、格納されているメタデータと、リソース ガバナーの構成のメモリ内の値を比較する方法を示します。  
  
```  
USE master;  
go  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
go  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
go  
```  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.resource_governor_configuration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  

