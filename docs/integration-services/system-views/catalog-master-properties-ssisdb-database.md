---
title: catalog.master_properties (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5614a15df481602ee0bdaa755afd53b522e79e47
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35404534"
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Master のプロパティを表示します。

|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar (256)**|Scale Out Master のプロパティの名前。|  
|property_value|**nvarchar(max)**|Scale Out Master のプロパティの値。|

## <a name="remarks"></a>Remarks
このビューは、各 Scale Out Master のプロパティの行を表示します。 このビューで表示されるプロパティは、次のとおりです。

|プロパティ名|[説明]|  
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
