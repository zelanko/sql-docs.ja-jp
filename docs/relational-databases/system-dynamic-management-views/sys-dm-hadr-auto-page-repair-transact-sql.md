---
title: sys.dm_hadr_auto_page_repair (TRANSACT-SQL) |Microsoft ドキュメント
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
- dm_hadr_auto_page_repair_TSQL
- sys.dm_hadr_auto_page_repair
- sys.dm_hadr_auto_page_repair_TSQL
- dm_hadr_auto_page_repair
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- automatic page repair
- sys.dm_hadr_auto_page_repair dynamic management view
ms.assetid: d7840adf-4a1b-41ac-bc94-102c07ad1c79
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85f42b166b08d25e357570be8ee84c94056ccfea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmhadrautopagerepair-transact-sql"></a>sys.dm_hadr_auto_page_repair (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンスで任意の可用性グループに対してホストされている可用性レプリカの可用性データベースに対するページの自動修復の試行ごとに 1 行のデータを返します。 このビューには、特定のプライマリまたはセカンダリ データベースに対して最近試行されたページの自動修復に対応する行が含まれます (データベースあたり最大 100 行)。 データベースあたりの最大行数に達すると、その後に試行されたページの自動修復の行によって、既存のエントリが置き換えられます。
  
  次の表では、さまざまな列の意味を定義します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|この行に対応するデータベースの ID です。|  
|**file_id**|**int**|ページが存在するファイルの ID です。|  
|**page_id**|**bigint**|ファイル内のページの ID です。|  
|**error_type**|**int**|エラーの種類です。 値を指定できます。<br /><br /> **-** 1 = すべてのハードウェア 823 エラー<br /><br /> 1 = 824 不適切なチェックサムまたは破損ページ (不適切なページ ID など) 以外のエラー<br /><br /> 2 = 不適切なチェックサム<br /><br /> 3 = 破損ページ|  
|**page_status**|**int**|ページ修復の試行ステータスです。<br /><br /> 2 = パートナーからの要求を待機中。<br /><br /> 3 = 要求はパートナーに送信済み。<br /><br /> 4 =  ページの自動修復を待機中 (応答はパートナーから受信済み)。<br /><br /> 5 = ページの自動修復に成功し、ページは使用可能。<br /><br /> 6 = 修復不可能。 パートナー側でもページが破損していた、パートナーと接続されていない、ネットワークの問題が発生したなど、ページ修復を試みているときにエラーが発生したことを示します。 これは最終的な状態ではありません。同じページで再度破損が見つかった場合、そのページが再びパートナーから要求されます。|  
|**modification_time**|**datetime**|ページ ステータスが最後に変更された日時です。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [ページの自動修復 &#40;可用性グループ: データベース ミラーリング&#41;](../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [suspect_pages & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/suspect-pages-transact-sql.md)   
 [suspect_pages テーブルの管理 &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  

