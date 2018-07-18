---
title: sys.dm_io_pending_io_requests (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_io_pending_io_requests
- dm_io_pending_io_requests
- dm_io_pending_io_requests_TSQL
- sys.dm_io_pending_io_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_pending_io_requests dynamic management view
ms.assetid: d1fb46dd-5c74-4c04-9ecf-8934b1bedb5b
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: eeb43f5d32b5ecfa62787c6c9c2189ea2476c7cd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38065470"
---
# <a name="sysdmiopendingiorequests-transact-sql"></a>sys.dm_io_pending_io_requests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で保留中の I/O 要求ごとに 1 行のデータを返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_io_pending_io_requests**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**io_completion_request_address**|**varbinary(8)**|I/O 要求のメモリ アドレス。 NULL 値は許可されません。|  
|**io_type**|**varchar(7)**|保留中の I/O 要求の種類。 NULL 値は許可されません。|  
|**io_pending**|**int**|I/O 要求が Windows で保留されているか、完了しているかを示します。 でも Windows が完了すると、要求を保留中の I/O 要求ができますが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を I/O 要求を処理し、この一覧から削除して、コンテキストが切り替えがまだ実行されていません。 NULL 値は許可されません。|  
|**io_completion_routine_address**|**varbinary(8)**|I/O 要求が完了したときに呼び出される内部関数。 NULL 値が許可されます。|  
|**io_user_data_address**|**varbinary(8)**|内部使用のみです。 NULL 値が許可されます。|  
|**scheduler_address**|**varbinary(8)**|I/O 要求が発行されたスケジューラ。 I/O 要求はスケジューラの保留中 I/O 一覧に表示されます。 詳細については、次を参照してください。 [sys.dm_os_schedulers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)します。 NULL 値は許可されません。|  
|**io_handle**|**varbinary(8)**|I/O 要求で使用されているファイルのファイル ハンドル。 NULL 値が許可されます。|  
|**io_offset**|**bigint**|I/O 要求のオフセット。 NULL 値は許可されません。|  
|**io_pending_ms_ticks**|**int**|内部使用のみです。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [O 関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


