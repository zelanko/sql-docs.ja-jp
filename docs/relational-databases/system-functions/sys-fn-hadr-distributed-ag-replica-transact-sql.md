---
title: fn_hadr_distributed_ag_replica (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_distributed_ag_replica
- sys.fn_hadr_distributed_ag_replica_TSQL
- fn_hadr_distributed_ag_replica
- fn_hadr_distributed_ag_replica_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_hadr_distributed_ag_replica
ms.assetid: a1e5f9cb-c350-4bb4-a04f-7394f6f25d62
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b4e6437a07aa571fc538f2630124dd52496d08e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906171"
---
# <a name="sysfn_hadr_distributed_ag_replica-transact-sql"></a>fn_hadr_distributed_ag_replica (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  分散型可用性グループ内のレプリカをローカル可用性グループにマップするために使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>引数  
 '*lag_Id*'  
 分散型可用性グループの識別子を示します。 *lag_Id*型は**uniqueidentifier**です。  
  
 '*replica_id*'  
 分散型可用性グループ内のレプリカの識別子を示します。 *replica_id*型は**uniqueidentifier**です。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|ローカル可用性グループの一意の識別子 (GUID)。|  
  
## <a name="examples"></a>使用例  
  
### <a name="using-sysfn_hadr_distributed_ag_replica"></a>Fn_hadr_distributed_ag_replica の使用  
 次の例では、指定された分散型可用性グループとレプリカに関連付けられているローカル可用性グループ識別子を含むテーブルを返します。  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ関数 &#40;Transact-sql&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [分散型可用性グループ &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [Transact-sql&#41;&#40;可用性グループの作成](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
