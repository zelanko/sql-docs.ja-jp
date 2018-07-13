---
title: sys.pdw_loader_backup_runs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2b72034c-6a11-46b9-a76c-7a88b2bea360
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8da926d5e3e12619a249fe593fac4b1be5df2bf6
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36875010"
---
# <a name="syspdwloaderbackupruns-transact-sql"></a>sys.pdw_loader_backup_runs (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  進行中と完了したバックアップと復元操作に関する情報を格納[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]、および進行中と完了したバックアップ、復元、および読み込みの操作で[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。 情報は、システムの再起動の間で永続化します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|特定のバックアップ、復元、またはロードの実行の一意の識別子。<br /><br /> このビューのキーです。||  
|NAME|**nvarchar (255)**|Null の負荷になります。 バックアップまたは復元オプションの名前。||  
|submit_time|**datetime**|要求が送信された時刻です。||  
|start_time|**datetime**|操作の開始時刻。||  
|end_time|**datetime**|時刻の操作の完了、失敗、またはが取り消されました。||  
|total_elapsed_time|**int**|時間の合計では、start_time と現在の時刻の間または start_time と end_time の間が経過した完了、キャンセル、または失敗した実行します。|Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|operation_type|**nvarchar(16)**|負荷の種類。|'BACKUP'、'ロード'、'を' 復元|  
|mode|**nvarchar(16)**|実行の種類の中でのモードです。|Operation_type =**バックアップ**<br />**DIFFERENTIAL**<br />**FULL**<br /><br /> Operation_type =**負荷**<br />**追加**<br />**RELOAD**<br />**UPSERT**<br /><br /> Operation_type =**復元**<br />**DATABASE**<br />**HEADER_ONLY**|  
|database_name|**nvarchar (255)**|この操作のコンテキストであるデータベースの名前||  
|table_name|**nvarchar (255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|Principal_id|**int**|操作を要求するユーザーの ID です。||  
|session_id|**nvarchar(32)**|操作を実行するセッションの ID。|Session_id を参照してください。 [sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)します。|  
|request_id|**nvarchar(32)**|操作を実行して、要求の ID です。 読み込み、これには、この負荷に関連付けられている現在または最新の要求が、.|Request_id 内を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|status|**nvarchar(16)**|実行の状態です。|'取り消し済み'、' 完了 '、'FAILED'、'キューに置かれた'、'実行中|  
|進行状況|**int**|完了率。|0 ～ 100|  
|command|**nvarchar (4000)**|ユーザーによって送信されたコマンドの完全なテキスト。|(スペースをカウントする)、4,000 文字より長い場合は切り捨てられます。|  
|rows_processed|**bigint**|この操作の一部として処理された行の数です。||  
|rows_rejected|**bigint**|この操作の一部として拒否された行の数。||  
|rows_inserted|**bigint**|この操作の一部として、データベース テーブルに挿入される行の数。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
