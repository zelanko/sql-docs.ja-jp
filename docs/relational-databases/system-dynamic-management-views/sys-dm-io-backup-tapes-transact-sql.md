---
title: sys.dm_io_backup_tapes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_io_backup_tapes
- dm_io_backup_tapes_TSQL
- sys.dm_io_backup_tapes_TSQL
- dm_io_backup_tapes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_backup_tapes dynamic management view
ms.assetid: 2e27489e-cf69-4a89-9036-77723ac3de66
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3bed26729a4a743d59e61e88e1f6b7a6427cf14e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmiobackuptapes-transact-sql"></a>sys.dm_io_backup_tapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テープ デバイスの一覧、およびバックアップのマウント要求の状態を返します。   
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**nvarchar(520)**|バックアップを実行できる実際の物理デバイスの名前。 NULL 値は許可されません。|  
|**logical_device_name**|**nvarchar (256)**|ドライブのユーザーが指定した名前 (から**sys.backup_devices**)。 ユーザーが指定した名前がない場合は NULL になります。 NULL 値が許可されます。|  
|**ステータス**|**int**|テープの状態。<br /><br /> 1 = 空き、使用可<br /><br /> 2 = マウント保留<br /><br /> 3 = 使用中<br /><br /> 4 = 読み込み中<br /><br /> **注:** テープの読み込み中に (**状態 = 4**)、メディア ラベルがまだ閲覧していません。 など、メディア ラベル値をコピーする列**media_sequence_number**、予想値を表示する、テープ上の実際の値と異なる場合があります。 ラベルが読み取られた後**ステータス**に変更**3** (使用中)、メディア ラベル列が読み込まれている実際のテープを反映し、します。<br /><br /> NULL 値は許可されません。|  
|**status_desc**|**nvarchar(520)**|テープの状態の説明。<br /><br /> AVAILABLE <br /><br /> MOUNT PENDING <br /><br /> IN USE <br /><br /> LOADING MEDIA <br /><br /> NULL 値は許可されません。|  
|**mount_request_time**|**datetime**|マウントが要求された時間。 保留中マウントがない場合は NULL (**ステータス! = 2**)。 NULL 値が許可されます。|  
|**mount_expiration_time**|**datetime**|マウント要求が期限切れ (タイムアウト) となる時間。 保留中マウントがない場合は NULL (**ステータス! = 2**)。 NULL 値が許可されます。|  
|**database_name**|**nvarchar (256)**|このデバイスにバックアップされるデータベース。 NULL 値が許可されます。|  
|**spid**|**int**|セッション ID。 テープのユーザーを識別できます。 NULL 値が許可されます。|  
|**command**|**int**|バックアップを実行するコマンド。 NULL 値が許可されます。|  
|**command_desc**|**nvarchar(120)**|コマンドの説明。 NULL 値が許可されます。|  
|**media_family_id**|**int**|メディア ファミリのインデックス (1...*n*)、 *n*メディア セット内のメディア ファミリの数です。 NULL 値が許可されます。|  
|**media_set_name**|**nvarchar (256)**|メディア セットが作成されている場合、MEDIANAME オプションで指定されたメディア セットの名前 (存在する場合)。 NULL 値が許可されます。|  
|**media_set_guid**|**uniqueidentifier**|メディア セットを一意に識別する識別子。 NULL 値が許可されます。|  
|**media_sequence_number**|**int**|メディア ファミリ内のボリュームのインデックス (1...*n*)。 NULL 値が許可されます。|  
|**tape_operation**|**int**|実行中のテープ操作。<br /><br /> 1 = 読み取り<br /><br /> 2 = フォーマット<br /><br /> 3 = 初期化<br /><br /> 4 = 追加<br /><br /> NULL 値が許可されます。|  
|**tape_operation_desc**|**nvarchar(120)**|テープの実行中の操作。<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> APPEND <br /><br /> NULL 値が許可されます。|  
|**mount_request_type**|**int**|マウント要求の種類。<br /><br /> 1 = 特定のテープ。 によって識別される、テープ、 **media _\*** フィールドが必要です。<br /><br /> 2 = 次のメディア ファミリ。 まだ復元されていない次のメディア ファミリが要求されています。 これは、メディア ファミリより少ないデバイスから復元するときに使用されます。<br /><br /> 3 = 後続テープ。 メディア ファミリが拡張され、後続テープが要求されています。<br /><br /> NULL 値が許可されます。|  
|**mount_request_type_desc**|**nvarchar(120)**|マウント要求の種類。<br /><br /> SPECIFIC TAPE <br /><br /> NEXT MEDIA FAMILY <br /><br /> CONTINUATION VOLUME <br /><br /> NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーでの VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I、O 関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

