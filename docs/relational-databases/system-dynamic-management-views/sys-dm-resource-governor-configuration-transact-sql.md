---
title: sys.dm_resource_governor_configuration (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 552b1ecbfd01afddf8671c05dcdf528f3edccb6a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmresourcegovernorconfiguration-transact-sql"></a>sys.dm_resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リソース ガバナーの現在のメモリ内の構成状態を含む行を返します。  
  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|リソース ガバナーによって現在使用されている分類子関数の ID です。 関数が使用されていない場合は、値 0 を返します。 NULL 値は許可されません。<br /><br /> **注:** この関数は新しい要求の分類に使用し、適切なワークロード グループをこれらの要求をルーティングする規則を使用します。 詳細については、「[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。|  
|is_reconfiguration_pending|**bit**|グループまたはプールへの変更が、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを使用して行われたがメモリ内の構成に適用されていないかどうかを示します。 返される値は次のいずれかです。<br /><br /> 0: 再構成ステートメントは必要ありません。<br /><br /> 1: 保留中の構成変更を適用するため、再構成ステートメントまたはサーバーの再起動が必要です。<br /><br /> **注:** 返される値は常にリソース ガバナーが無効になっている場合は 0 です。<br /><br /> NULL 値は許可されません。|  
|max_outstanding_io_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ボリュームごとの未処理の I/O の最大数。|  
  
## <a name="remarks"></a>解説  
 この動的管理ビューには、メモリ内の構成が表示されます。 格納されている構成メタデータを表示するには、対応するカタログ ビューを使用します。  
  
 次の例では、リソース ガバナーの構成の格納されているメタデータの値とメモリ内の値を取得して比較する方法を示します。  
  
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
  
## <a name="permissions"></a>権限  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.resource_governor_configuration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  

