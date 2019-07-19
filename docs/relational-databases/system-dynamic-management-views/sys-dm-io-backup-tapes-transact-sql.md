---
title: sys.dm_io_backup_tapes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: c58f34404119592308515f95934e23cfc94e1fc6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900395"
---
# <a name="sysdmiobackuptapes-transact-sql"></a>sys.dm_io_backup_tapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テープ デバイスの一覧、およびバックアップのマウント要求の状態を返します。   
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**physical_device_name**|**nvarchar(520)**|バックアップを実行できる実際の物理デバイスの名前。 NULL 値は許可されません。|  
|**logical_device_name**|**nvarchar (256)**|ドライブのユーザーが指定した名前 (から**sys.backup_devices**)。 ユーザーが指定した名前が使用できない場合は NULL です。 NULL 値が許可されます。|  
|**status**|**int**|テープの状態。<br /><br /> 1 = open、使用可能<br /><br /> 2 = マウント保留<br /><br /> 3 = 使用中<br /><br /> 4 = 読み込み<br /><br /> **注:** テープの読み込み中に (**状態 = 4**)、メディア ラベルがまだ読み取られていません。 など、メディア ラベル値をコピーする列**media_sequence_number**予想値は、テープ上の実際の値が異なる場合があります。 ラベルが読み取られた後**状態**への変更**3** (使用) 中、メディア ラベル列が読み込まれている実際のテープを反映します。<br /><br /> NULL 値は許可されません。|  
|**status_desc**|**nvarchar(520)**|テープの状態の説明です。<br /><br /> AVAILABLE<br /><br /> MOUNT PENDING<br /><br /> IN USE<br /><br /> LOADING MEDIA<br /><br /> NULL 値は許可されません。|  
|**mount_request_time**|**datetime**|マウントが要求される時刻。 保留中マウントがない場合は NULL (**状態! = 2**)。 NULL 値が許可されます。|  
|**mount_expiration_time**|**datetime**|(タイムアウト) がどのマウント要求に有効期限は時間です。 保留中マウントがない場合は NULL (**状態! = 2**)。 NULL 値が許可されます。|  
|**database_name**|**nvarchar (256)**|このデバイスにバックアップするデータベース。 NULL 値が許可されます。|  
|**spid**|**int**|セッション ID。 これは、テープのユーザーを識別します。 NULL 値が許可されます。|  
|**command**|**int**|バックアップを実行するコマンド。 NULL 値が許可されます。|  
|**command_desc**|**nvarchar(120)**|コマンドの説明。 NULL 値が許可されます。|  
|**media_family_id**|**int**|メディア ファミリのインデックス (1...*n*)、 *n*メディア セット内のメディア ファミリの数です。 NULL 値が許可されます。|  
|**media_set_name**|**nvarchar (256)**|メディア セットが作成された場合、MEDIANAME オプションで指定されたメディア セット (あれば) の名前) NULL 値が許可されます。|  
|**media_set_guid**|**uniqueidentifier**|メディア セットを一意に識別する識別子です。 NULL 値が許可されます。|  
|**media_sequence_number**|**int**|メディア ファミリ内のボリュームのインデックス (1...*n*)。 NULL 値が許可されます。|  
|**tape_operation**|**int**|テープが実行される操作。<br /><br /> 1 = 読み取り<br /><br /> 2 = 形式<br /><br /> 3 = Init<br /><br /> 4 = 追加<br /><br /> NULL 値が許可されます。|  
|**tape_operation_desc**|**nvarchar(120)**|テープが実行される操作。<br /><br /> READ<br /><br /> FORMAT<br /><br /> INIT<br /><br /> 追加<br /><br /> NULL 値が許可されます。|  
|**mount_request_type**|**int**|マウント要求の種類です。<br /><br /> 1 = 特定のテープ。 識別される、テープ、 **media _\*** フィールドが必要です。<br /><br /> 2 = 次のメディア ファミリ。 復元されていない次のメディア ファミリが要求されます。 これは、メディア ファミリ数よりも少ない数のデバイスから復元する場合に使用されます。<br /><br /> 3 = 後続テープ。 メディア ファミリが拡張され、後続テープが要求されています。<br /><br /> NULL 値が許可されます。|  
|**mount_request_type_desc**|**nvarchar(120)**|マウント要求の種類です。<br /><br /> SPECIFIC TAPE<br /><br /> NEXT MEDIA FAMILY<br /><br /> CONTINUATION VOLUME<br /><br /> NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーによっては、サーバーの VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [O 関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

