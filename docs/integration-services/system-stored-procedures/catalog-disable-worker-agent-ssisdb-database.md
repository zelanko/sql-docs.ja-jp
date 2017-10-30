---
title: "catalog.disable_worker_agent (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 8f4a8cd24278742ffb13d16791ce5f1f3a95f301
ms.contentlocale: ja-jp
ms.lasthandoff: 10/20/2017

---
# <a name="catalogdisableworkeragent-ssisdb-database"></a>catalog.disable_worker_agent (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

スケール アウト マスターでこの操作のスケール アウト ワーカーを無効にする[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。

## <a name="syntax"></a>構文

```sql
catalog.disable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>引数
[@WorkerAgentId =] *WorkerAgentId*ワーカー エージェント ID のスケール アウト ワーカーです。 *WorkerAgentId*は**uniqueidentifier**です。

## <a name="example"></a>例
この例では、スケール アウト Worker MachineA を無効にします。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
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

