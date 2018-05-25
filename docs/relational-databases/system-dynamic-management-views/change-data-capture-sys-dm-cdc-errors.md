---
title: sys.dm_cdc_errors (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 488e9eb3695dea1eada4b57d092451d40131f419
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="change-data-capture---sysdmcdcerrors"></a>変更データ キャプチャの sys.dm_cdc_errors
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更データ キャプチャのログ スキャン セッション中に発生したエラーごとに 1 行を返します。  
 
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|セッションの ID を指定します。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**phase_number**|**int**|エラー発生時のセッションのフェーズを示す数値です。 各フェーズの説明は、次を参照してください。 [sys.dm_cdc_log_scan_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)です。|  
|**entry_time**|**datetime**|エラーが記録された日時です。 この値は、SQL のエラー ログのタイムスタンプに対応します。|  
|**error_number**|**int**|エラー メッセージの ID です。|  
|**error_severity**|**int**|メッセージの重大度レベルです。有効値は 1 ～ 25 です。|  
|**error_state**|**int**|エラーの状態を表す数値です。|  
|**error_message**|**nvarchar(1024)**|エラー メッセージのテキストです。|  
|**start_lsn**|**nvarchar(23)**|エラー発生時に処理されていた行の開始 LSN 値です。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**begin_lsn**|**nvarchar(23)**|エラー発生時に処理されていたトランザクションの先頭 LSN 値です。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
|**sequence_value**|**nvarchar(23)**|エラー発生時に処理されていた行の LSN 値です。<br /><br /> 0 は、ログ スキャン セッション中にエラーが発生しなかったことを示します。|  
  
## <a name="remarks"></a>解説  
 **sys.dm_cdc_errors**以前の 32 セッションのエラー情報が含まれています。  
  
## <a name="permissions"></a>権限  
 クエリに VIEW DATABASE STATE 権限が必要です、 **sys.dm_cdc_errors**動的管理ビュー。 動的管理ビューに対するアクセス許可の詳細については、次を参照してください。[動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)です。  
  
## <a name="see-also"></a>参照  
 [sys.dm_cdc_log_scan_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [sys.dm_repl_traninfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

