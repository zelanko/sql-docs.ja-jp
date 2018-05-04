---
title: sys.fn_hadr_distributed_ag_replica (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 52fc3c97e629acc3455cdeae5707429f44d3e2cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysfnhadrdistributedagreplica-transact-sql"></a>sys.fn_hadr_distributed_ag_replica (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  ローカルの可用性グループに分散型可用性グループには、レプリカをマップするために使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_hadr_distributed_ag_replica( lag_Id, replica_id )  
```  
  
## <a name="arguments"></a>引数  
 '*lag_Id*'  
 分散型可用性グループの識別子です。 *lag_Id*は型です。 **uniqueidentifier**です。  
  
 '*replica_id*'  
 分散型可用性グループには、レプリカの識別子です。 *replica_id*は型です。 **uniqueidentifier**です。  
  
## <a name="tables-returned"></a>返されたテーブル  
 次の情報を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|ローカルの可用性グループの一意の識別子 (GUID)。|  
  
## <a name="examples"></a>使用例  
  
### <a name="using-sysfnhadrdistributedagreplica"></a>Sys.fn_hadr_distributed_ag_replica を使用します。  
 次の例では、指定された分散型可用性グループとレプリカに関連付けられているローカルの可用性グループ識別子を持つテーブルを返します。  
  
```  
DECLARE @lagId uniqueidentifier = '4A03D1A8-4AE6-B153-E7E9-ED22A546008D'  
DECLARE @replicaId uniqueidentifier = 'D5517513-04A8-FD82-14C6-E684EC913935'  
  
SELECT * FROM sys.fn_hadr_distributed_ag_replica(@lagId, @replicaId)  
GO  
```  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [AlwaysOn 可用性グループと &#40; です。SQL Server と &#41; です。](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [可用性グループの分散&#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)  
 [可用性グループ &#40;Transact SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
