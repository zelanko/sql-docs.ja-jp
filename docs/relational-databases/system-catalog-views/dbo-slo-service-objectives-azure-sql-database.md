---
title: "dbo.slo_service_objectives (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: Azure SQL Database
f1_keywords:
- dbo.slo_service_objectives
- dbo.slo_service_objectives_TSQL
- slo_service_objectives
- slo_service_objectives_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_service_objectives
- slo_service_objectives
ms.assetid: d5dd7ed9-440a-4432-ad45-644e4e72318f
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0f91dccf478821047e4c3a25ea19d35d1a2774fd
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dbosloserviceobjectives-azure-sql-database"></a>dbo.slo_service_objectives (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  この機能はプレビュー状態では、ありは既に廃止されて[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V12 します。 この機能は将来のリリースで変更または削除される可能性があるので、この機能の特定の実装に依存する設定は行わないでください。  
  
 現在のサーバー上にあるサービス レベル目標 (SLO) に関する情報を返します。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11 します。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|objective_id|**uniqueidentifier**|サービス レベル目標の ID。|  
|NAME|**sysname**|サービス レベル目標 の名前。|  
|description|**nvarchar**|サービス レベル目標に関する説明。|  
|create_date|**datetimeoffset(7)**|サーバー上にあるサービス レベル オブジェクトの作成日。|  
|is_system|**bit**|1 = システムのサービス レベル目標|  
|is_default|**bit**|1 = サービス レベル目標は既定の SLO。|  
|state|**tinyint**|1 = サービス レベル目標は有効。<br /><br /> 2 = サービス レベル目標は無効。|  
|state_desc|**nvarchar**|サービス レベル目標に関する説明。|  
|metadata_version|**decimal**|サービス レベル目標のバージョン。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [Premium データベースの管理](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
