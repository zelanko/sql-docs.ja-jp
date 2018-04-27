---
title: catalog.master_properties (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57941951cbf442b275b349a753ae8aa73c69668f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master のプロパティを表示します。

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|Scale Out Master のプロパティの名前。|  
|property_value|**nvarchar(max)**|Scale Out Master のプロパティの値。|

## <a name="remarks"></a>Remarks
このビューは、各 Scale Out Master のプロパティの行を表示します。 このビューで表示されるプロパティは、次のとおりです。

|プロパティ名|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|ログ データベースのある SQL Server。|
|**LAST_ONLINE_TIME**|Scale Out Master がオンラインになった最後の時刻。|
|**MACHINE_IP**|コンピューターの IP。|
|**MACHINE_NAME**|コンピューターの名前です。|
|**MASTER_ADDRESS**|Scale Out Master のエンドポイント。|
|**MASTER_SERVICE_PORT**|Scale Out Master のエンドポイントのポート。|
|**SSLCERT_THUMBPRINT**|Scale Out Master 証明書の拇印。|

## <a name="permissions"></a>アクセス許可
public データベース ロールのすべてのメンバーにこのビューの読み取りアクセス許可が与えられます。 
