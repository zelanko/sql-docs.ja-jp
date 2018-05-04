---
title: sys.dm_filestream_file_io_handles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34d72c21f66544cae05bd9fa6dba8cb70282862c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  名前空間所有者 (NSO) が認識するファイル ハンドルを表示します。 クライアントを使用して取得した Filestream ハンドル**OpenSqlFilestream**がこのビューで表示されます。  
  
|列|型|Description|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|クライアントのハンドルに関連付けられた内部 NSO 構造のアドレスを示します。 NULL 値が許可されます。|  
|**creation_request_id**|**int**|このハンドルの作成に使用した REQ_PRE_CREATE I/O 要求のフィールドを示します。 NULL 値は許可されません。|  
|**creation_irp_id**|**int**|このハンドルの作成に使用した REQ_PRE_CREATE I/O 要求のフィールドを示します。 Null 値はありません。|  
|**handle_id**|**int**|ドライバーによって割り当てられるこのハンドルの一意の ID を示します。 NULL 値は許可されません。|  
|**creation_client_thread_id**|**varbinary(8)**|このハンドルの作成に使用した REQ_PRE_CREATE I/O 要求のフィールドを示します。 NULL 値が許可されます。|  
|**creation_client_process_id**|**varbinary(8)**|このハンドルの作成に使用した REQ_PRE_CREATE I/O 要求のフィールドを示します。 NULL 値が許可されます。|  
|**filestream_transaction_id**|**varbinary (128)**|特定のハンドルに関連付けられているトランザクションの ID を示します。 これは、によって返される値、 **get_filestream_transaction_context**関数。 このフィールドへの参加を使用して、 **sys.dm_filestream_file_io_requests**ビュー。 NULL 値が許可されます。|  
|**access_type**|**nvarchar(60)**|NULL 値は許可されません。|  
|**logical_path**|**nvarchar (256)**|このハンドルによって開かれたファイルの論理パス名を示します。 これは、によって返されるパス名と同じ、**です。PathName**メソッドの**varbinary**(**max**) filestream です。 NULL 値が許可されます。|  
|**physical_path**|**nvarchar (256)**|ファイルの実際の NTFS パス名を示します。 これは、同じパス名がによって返される、**です。PhysicalPathName**のメソッド、 **varbinary**(**max**) filestream です。 トレース フラグ 5556 で有効になります。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [Filestream および FileTable 動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
