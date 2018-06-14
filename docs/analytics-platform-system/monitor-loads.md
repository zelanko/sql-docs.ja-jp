---
title: 並列データ ウェアハウスの読み込みを監視 |Microsoft ドキュメント
description: Analytics Platform System (AP) 管理コンソールまたは並列データ ウェアハウス (PDW) のシステム ビューを使用してアクティブになっており、最新の負荷を監視します。"
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8980259b69dfa74c2bb27c9406553a5b5810348a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585674"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Parallel Data Warehouse にモニターを読み込みます
Active と最近モニター [dwloader](dwloader.md) Analytics Platform System (APS) 管理コンソールまたは並列データ ウェアハウス (PDW) を使用してロード[システム ビュー](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/)です。 
  
> [!TIP]  
> INSERT ステートメントまたは SQL ステートメントを使用して、負荷を実行するビジネス インテリジェンス ツールを使用して、いくつかの読み込みが開始されます。 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>前提条件  
負荷を監視するために使用するメソッドにかかわらず、ログインは、基になるデータ ソースにアクセスする権限が必要です。 

<!-- MISSING LINKS
For the permissions to grant, see “Use All of the Admin Console” in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>負荷を監視  
次のセクションでは、負荷を監視する方法について説明します。  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>管理コンソールを使用して負荷を監視するには  
  
1.  管理コンソールにログオンします。 <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  上部のメニューをクリックして**負荷**です。 最近使ったすべてを表示、並べ替え可能なテーブルとアクティブな読み込み、読み込みが完了するかがアクティブかどうかなどの追加情報が表示されます。 行を並べ替える列のヘッダーをクリックします。  
  
3.  特定のロードの追加の詳細を表示するには、負荷をクリックして**ID**左の列にします。 詳細ビューでは、負荷の各手順の進行状況を確認できます。  
  
管理コンソールに表示されるロードについてのメタデータについてこれらのシステム ビューを参照してください。  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>システム ビューを使用して負荷を監視するには  
SQL Server PDW のビューを使用してアクティブになっており、最新の負荷を監視するに次の手順に従います。 使用されるシステム ビューごとに、ビューによって返される可能性のある値と列については、そのビューのドキュメントを参照してください。  
  
1.  検索、`request_id`で読み込み、 [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)ローダーのコマンドラインを検索して表示、`command`このビューの列。  
  
    コマンド テキストと現在の状態、たとえば、次のコマンドが返されますと`request_id`です。  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  使用して、`request_id`を使用して、負荷の追加情報を取得する、 [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) 、および[sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)ビュー。 たとえば、次のクエリを返します、`run_id`開始、終了、および、負荷のエラーを持続時間に関する情報および処理された行の数に関する情報。  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id=’12738’;  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
