---
title: dm_filestream_file_io_handles (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a96bcedaa3922ebb0691ac949f9eb15ed28336b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68103301"
---
# <a name="sysdm_filestream_file_io_handles-transact-sql"></a>dm_filestream_file_io_handles (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  名前空間の所有者 (NSO) が認識しているファイルハンドルを表示します。 **Opensqlfilestream**を使用してクライアントが受け取った Filestream ハンドルは、このビューに表示されます。  
  
|列|Type|説明|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary (8)**|クライアントのハンドルに関連付けられた内部 NSO 構造体のアドレスを表示します。 NULL 値が許可されます。|  
|**creation_request_id**|**int**|このハンドルの作成に使用された REQ_PRE_CREATE i/o 要求のフィールドを表示します。 NULL 値は許可されません。|  
|**creation_irp_id**|**int**|このハンドルの作成に使用された REQ_PRE_CREATE i/o 要求のフィールドを表示します。 Null 値はありません|  
|**handle_id**|**int**|ドライバーによって割り当てられるこのハンドルの一意の ID を表示します。 NULL 値は許可されません。|  
|**creation_client_thread_id**|**varbinary (8)**|このハンドルの作成に使用された REQ_PRE_CREATE i/o 要求のフィールドを表示します。 NULL 値が許可されます。|  
|**creation_client_process_id**|**varbinary (8)**|このハンドルの作成に使用された REQ_PRE_CREATE i/o 要求のフィールドを表示します。 NULL 値が許可されます。|  
|**filestream_transaction_id**|**varbinary (128)**|特定のハンドルに関連付けられているトランザクションの ID を示します。 これは、 **get_filestream_transaction_context**関数によって返される値です。 このフィールドを使用して、 **dm_filestream_file_io_requests**ビューに結合します。 NULL 値が許可されます。|  
|**access_type**|**nvarchar(60)**|NULL 値は許可されません。|  
|**logical_path**|**nvarchar(256)**|このハンドルによって開かれたファイルの論理パス名を示します。 これは、によって返されるパス名と同じ**です。** **Varbinary**(**Max**) filestream の PathName メソッド。 NULL 値が許可されます。|  
|**physical_path**|**nvarchar(256)**|ファイルの実際の NTFS パス名を示します。 これは、によって返されるパス名と同じ**です。** **Varbinary**(**Max**) filestream の physicalpathname メソッド。 トレースフラグ5556によって有効にされます。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の Filestream および FileTable の動的管理ビュー](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
