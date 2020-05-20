---
title: dm_resource_governor_configuration (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df38bbb333e3cadb328b9701c19f21ae657a544b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830484"
---
# <a name="sysdm_resource_governor_configuration-transact-sql"></a>dm_resource_governor_configuration (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Resource Governor の現在のメモリ内の構成状態を含む行を返します。  
  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|Resource Governor によって現在使用されている分類子関数の ID。 関数が使用されていない場合は、値 0 を返します。 NULL 値は許可されません。<br /><br /> **注:** この関数は、新しい要求を分類するために使用され、ルールを使用してこれらの要求を適切なワークロードグループにルーティングします。 詳細については、「[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)」を参照してください。|  
|is_reconfiguration_pending|**bit**|グループまたはプールに対する変更が ALTER RESOURCE GOVERNOR 再構成ステートメントで行われたが、メモリ内の構成に適用されていないかどうかを示します。 返される値は次のいずれかです。<br /><br /> 0-再構成ステートメントは必要ありません。<br /><br /> 1: 保留中の構成変更を適用するため、再構成ステートメントまたはサーバーの再起動が必要です。<br /><br /> **注:** Resource Governor が無効になっている場合、返される値は常に0です。<br /><br /> NULL 値は許可されません。|  
|max_outstanding_io_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 以降。<br /><br /> ボリュームごとの未処理の I/O の最大数。|  
  
## <a name="remarks"></a>解説  
 この動的管理ビューには、メモリ内の構成が表示されます。 格納されている構成メタデータを表示するには、対応するカタログビューを使用します。  
  
 次の例では、格納されているメタデータ値と Resource Governor 構成のメモリ内の値を取得して比較する方法を示します。  
  
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
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [resource_governor_configuration &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-configuration-transact-sql.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  

