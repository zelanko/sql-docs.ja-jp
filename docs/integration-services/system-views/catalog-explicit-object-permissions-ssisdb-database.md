---
title: "catalog.explicit_object_permissions (SSISDB データベース) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 49b09e0f-06e8-451f-b979-a0d91000bfe3
caps.latest.revision: "16"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0923ea0cb6262a3a45530d0c2aa513312e566597
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="catalogexplicitobjectpermissions-ssisdb-database"></a>catalog.explicit_object_permissions (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ユーザーに明示的に割り当てられた権限のみを表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|セキュリティ保護可能なオブジェクトの種類。 セキュリティ保護可能なオブジェクトの種類には、フォルダー (`1`)、プロジェクト (`2`)、環境 (`3`)、および操作 (`4`) があります。|  
|object_id|**bigint**|セキュリティ保護可能なオブジェクトの一意の識別子 (ID) または主キーを指定します。|  
|principal_id|**int**|データベース プリンシパルの ID。|  
|permission_type|**smallint**|権限の種類。|  
|is_deny|**bit**|権限が拒否または許可されているかどうかを示します。 値が `1` の場合、権限は拒否されています。 値が `0` の場合、権限は拒否されていません。|  
|grantor_id|**int**|権限を付与したプリンシパルの ID。|  
  
## <a name="remarks"></a>解説  
 このビューは、次の表に示す権限の種類を表示します。  
  
|permission_type 値|権限名|権限の説明|該当するオブジェクトの種類|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが読み取ることができるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトのコンテンツを列挙したり、読み取ったりすることはできません。|フォルダー、プロジェクト、環境、操作|  
|`2`|MODIFY|プロパティなど、オブジェクトの一部と見なされる情報をプリンシパルが変更できるようにします。 プリンシパルがオブジェクト内に含まれるその他のオブジェクトを修正することはできません。|フォルダー、プロジェクト、環境、操作|  
|`3`|CREATE ステートメントを実行する前に、|プリンシパルがプロジェクトのすべてのパッケージを実行できるようにします。|プロジェクト|  
|`4`|MANAGE_PERMISSIONS|プリンシパルがオブジェクトに権限を割り当てることができるようにします。|フォルダー、プロジェクト、環境、操作|  
|`100`|CREATE_OBJECTS|プリンシパルがフォルダーでオブジェクトを作成できるようにします。|フォルダー|  
|`101`|READ_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを読み取ることができるようにします。|フォルダー|  
|`102`|MODIFY_OBJECTS|プリンシパルがフォルダーのすべてのオブジェクトを変更できるようにします。|フォルダー|  
|`103`|EXECUTE_OBJECTS|プリンシパルがフォルダーのすべてのプロジェクトからすべてのパッケージを実行できるようにします。|フォルダー|  
|`104`|MANAGE_OBJECT_PERMISSIONS|プリンシパルがフォルダー内のすべてのオブジェクトに対する権限を管理できるようにします。|フォルダー|  
  
## <a name="permissions"></a>Permissions  
 このビューには、現在のプリンシパルの権限が完全に表示されません。 ユーザーは、プリンシパルが、権限が割り当てられたロールまたはグループのメンバーであるかどうかを確認する必要もあります。  
  
  
