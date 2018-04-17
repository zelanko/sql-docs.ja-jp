---
title: sys.dm_db_mirroring_auto_page_repair (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
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
- dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair_TSQL
- sys.dm_db_mirroring_auto_page_repair
- dm_db_mirroring_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- automatic page repair
- database mirroring [SQL Server], automatic page repair
- sys.dm_db_mirroring_auto_page_repair dynamic management view
ms.assetid: 49f0fc2a-e25e-47e1-a135-563adb509af1
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d71ed7405b896a4e8542a66f445a7b6ed9376092
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="database-mirroring---sysdmdbmirroringautopagerepair"></a>データベース ミラーリングでは sys.dm_db_mirroring_auto_page_repair
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンス上のミラー化されたデータベースに対して試行されたページの自動修復ごとに 1 行を返します。 このビューには、ミラー化された特定のデータベースに対して最近試行されたページの自動修復に対応する行が含まれます (データベースあたり最大 100 行)。 データベースあたりの最大行数に達すると、その後に試行されたページの自動修復の行によって、既存のエントリが置き換えられます。 次の表に各列の意味を示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|この行に対応するデータベースの ID です。|  
|**file_id**|**int**|ページが存在するファイルの ID です。|  
|**page_id**|**bigint**|ファイル内のページの ID です。|  
|**error_type**|**int**|エラーの種類です。 値を指定できます。<br /><br /> **-**1 = すべてのハードウェア 823 エラー<br /><br /> 1 = 824 不適切なチェックサムまたは破損ページ (不適切なページ ID など) 以外のエラー<br /><br /> 2 = 不適切なチェックサム<br /><br /> 3 = 破損ページ|  
|**page_status**|**int**|ページ修復の試行ステータスです。<br /><br /> 2 = パートナーからの要求を待機中。<br /><br /> 3 = 要求はパートナーに送信済み。<br /><br /> 4 =  ページの自動修復を待機中 (応答はパートナーから受信済み)。<br /><br /> 5 = ページの自動修復に成功し、ページは使用可能。<br /><br /> 6 = 修復不可能。 パートナー側でもページが破損していた、パートナーと接続されていない、ネットワークの問題が発生したなど、ページ修復を試みているときにエラーが発生したことを示します。 これは最終的な状態ではありません。同じページで再度破損が見つかった場合、そのページが再びパートナーから要求されます。|  
|**modification_time**|**datetime**|ページ ステータスが最後に変更された日時です。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [ページの自動修復 &#40;可用性グループ: データベース ミラーリング&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [suspect_pages & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  


