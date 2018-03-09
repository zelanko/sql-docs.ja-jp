---
title: "sys.dm_xe_session_targets (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_session_targets
- dm_xe_session_targets_TSQL
- dm_xe_session_targets
- sys.dm_xe_session_targets_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_session_targets dynamic management view
- extended events [SQL Server], views
ms.assetid: 76fbc3e1-ad88-4a47-8bf1-471c3bee5ad8
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cdc4dd3ffa39c7d245b25a895f189aaaaa6cd332
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxesessiontargets-transact-sql"></a>sys.dm_xe_session_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セッション ターゲットに関する情報を返します。  
  
  |列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|イベント セッションのメモリ アドレス。 sys.dm_xe_sessions.address との多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|target_name|**nvarchar(60)**|セッション内のターゲットの名前。 NULL 値は許可されません。|  
|target_package_guid|**uniqueidentifier**|ターゲットを含むパッケージの GUID。 NULL 値は許可されません。|  
|execution_count|**bigint**|セッションのターゲットが実行された回数。 NULL 値は許可されません。|  
|execution_duration_ms|**bigint**|ターゲットが実行された時間の合計 (ミリ秒単位)。 NULL 値は許可されません。|  
|target_data|**nvarchar(max)**|イベント集計情報など、ターゲットが保持するデータ。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_session_targets.event_session_address|sys.dm_xe_sessions.address|多対一|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|target_data 列のデータ型を修正しました。|  
|target_data 列の説明を、NULL 値が許可されることを示す記述に修正しました。|  
|「リレーションシップの基数」の表を修正しました。|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

