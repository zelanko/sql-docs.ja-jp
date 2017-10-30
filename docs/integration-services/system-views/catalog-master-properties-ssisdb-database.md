---
title: "catalog.master_properties (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: 0fcbdca57c7764eaec758d2ad9ef3ab8675a3a9b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

プロパティを表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト マスター。

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|スケール アウト マスター プロパティの名前。|  
|property_value|**nvarchar(max)**|スケール アウト マスター プロパティの値。|

## <a name="remarks"></a>解説
このビューには、それぞれのスケール アウト マスター プロパティに行が表示されます。 このビューで表示されるプロパティは、次のとおりです。

|プロパティ名|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|ログ データベース、SQL Server で検索します。|
|**LAST_ONLINE_TIME**|スケール アウト マスターがオンラインと最後の時刻。|
|**MACHINE_IP**|コンピューターの IP。|
|**コンピューター名**|コンピューターの名前です。|
|**MASTER_ADDRESS**|スケール アウト master データベースのエンドポイントです。|
|**MASTER_SERVICE_PORT**|スケール アウト master データベースのエンドポイントのポートです。|
|**SSLCERT_THUMBPRINT**|スケール アウト マスター証明書の拇印です。|

## <a name="permissions"></a>Permissions
Public データベース ロールのすべてのメンバーの読み取り権限がこのビューです。 

