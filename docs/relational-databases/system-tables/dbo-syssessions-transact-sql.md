---
description: dbo.sysセッション (Transact-sql)
title: dbo.sysセッション (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 72fa9a3d55b3ed783fcbfc7c230676e7fe653eea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473296"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.sysセッション (Transact-sql)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントが起動するたびに、新しいセッションが作成されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが予期せず再開または停止すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントではジョブの状態を保持するためセッションが使用されます。 **Syssessions**テーブルの各行には、1つのセッションに関する情報が含まれています。 各セッションの終了時にジョブの状態を表示するには、 **sysjobactivity** テーブルを使用します。  
  
 このテーブルは、 **msdb** データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント セッションの ID。 この session_id は、セッションの SPID ではなく、このシステムテーブル内の ID 値です。|  
|**agent_start_date**|**datetime**|セッションに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが開始された日時。|  
  
## <a name="remarks"></a>解説  
 このテーブルにアクセスできるのは、 **sysadmin** 固定サーバーロールのメンバーであるユーザーだけです。  
  
## <a name="see-also"></a>参照  
 [dbo.sysjobactivity &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
