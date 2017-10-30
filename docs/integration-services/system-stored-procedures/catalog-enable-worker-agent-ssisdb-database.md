---
title: "catalog.enable_worker_agent (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6e5266b-c32d-49ff-aa69-f09664009fb4
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3eb3f21b6a686c3013cdaaa3000038896edfbf94
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogenableworkeragent-ssisdb-database"></a>catalog.enable_worker_agent (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

スケール アウト マスターでこの操作のスケール アウト ワーカーを有効にする[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。

## <a name="syntax"></a>構文

```sql
catalog.enable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>引数
[@WorkerAgentId =] *WorkerAgentId*ワーカー エージェント ID のスケール アウト ワーカーです。 *WorkerAgentId*は**uniqueidentifier**です。

## <a name="example"></a>例
この例では、MachineA で Scale Out Worker を有効にします。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  

## <a name="permissions"></a>Permissions  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割 

## <a name="errors-and-warnings"></a>エラーおよび警告
ワーカー エージェント ID が有効でない場合、ストアド プロシージャはエラーを返します。

