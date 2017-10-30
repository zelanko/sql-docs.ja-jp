---
title: "catalog.worker_agents (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd0d827-e2f1-44fe-aa90-6bf922d68d16
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d56af0ab150255c53746898a638a32112938755c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="catalogworkeragents-ssisdb-database"></a>catalog.worker_agents (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

情報を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]スケール アウト ワーカーです。

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|WorkerAgentId|**uniqueidentifier**|ワーカーのエージェントの ID のスケール アウト ワーカー。|
|IsEnabled|**bit**|スケール アウト ワーカーが有効になっているかどうか。|
|DisplayName|**nvarchar (256)**|スケール アウト ワーカーの表示名。|
|Description|**nvarchar (256)**|スケール アウト ワーカーの説明です。|
|MachineName|**nvarchar (256)**|スケール アウト ワーカーのコンピューター名。|
|Tags|**nvarchar(max)**|スケール アウト ワーカーのタグ。|
|ユーザー アカウント|**nvarchar (256)**|スケール アウト Worker サービスを実行するユーザー アカウントです。|
|LastOnlineTime|**datetimeoffset (7)**|前回のスケール アウト ワーカーがオンラインになっています。|

## <a name="remarks"></a>解説
このビューには、スケール アウト作業者ごとに、SSISDB カタログの操作マスターを小数点以下桁数に接続する行が表示されます。

## <a name="permissions"></a>Permissions
このビューには、次の権限のいずれかが必要です。

- メンバーシップを**ssis_admin**データベース ロール

- メンバーシップを**ssis_cluster_executor**データベース ロール

- メンバーシップを**sysadmin**サーバーの役割

