---
title: システムエンドポイント (Transact-sql) (_a) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cluster_endpoints
- dm_cluster_endpoints_TSQL
- dm_cluster_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cluster_endpoints dynamic management view
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 05076a6b694ff5861c5a7862b1f8f913ddb67fd6
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536169"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>システムエンドポイント (Transact-sql) (_a)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|name|`sysname`|SQL ビッグデータクラスターで外部に公開されるサービスの名前。 エンドポイントの一意の識別子。 このビューのキー。 NULL 値は許可されません。 |  
|description|`nvarchar(4000)`|サービスの説明。 NULL 値は許可されません。 |
|エンドポイント (endpoint)|`sysname`|エンドポイント url または接続属性。 NULL 値は許可されません。 |
|protocol_desc|`sysname`|エンドポイントプロトコルの説明 |

## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]では、`VIEW SERVER STATE` のアクセス許可が必要です。

## <a name="see-also"></a>参照

[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)]とは (../..または、このようにして、このようにしてください。
