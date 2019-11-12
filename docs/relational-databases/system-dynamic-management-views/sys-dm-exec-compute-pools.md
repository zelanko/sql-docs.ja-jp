---
title: システムプール (Transact-sql) (_c) |。)Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_dm_compute_pools
- dm_dm_compute_pools_TSQL
- dm_dm_compute_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_dm_compute_pools dynamic management view
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 0b21f517b540c69822dd8b1da4aa6a4cf8b8616f
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532959"
---
# <a name="sysdm_dm_compute_pools-transact-sql"></a>システムプール (Transact-sql) (_r) (_c)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|name|`sysname`|コンピューティングプールの名前。 NULL 値は許可されません。 既定のコンピューティングプールの `default` を返します。 |
|compute_pool_id|`int`|プールの一意の識別子。 このビューのキー。|  
|設置|`sysname`|SQL ビッグデータクラスター内のコントローラーへのエンドポイント。 NULL 値は許可されません。 |

## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]では、`VIEW SERVER STATE` のアクセス許可が必要です。

## <a name="see-also"></a>参照

[[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)]とは何](../../big-data-cluster/big-data-cluster-overview.md)ですか。
