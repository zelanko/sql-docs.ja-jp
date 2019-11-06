---
title: アクティブなクエリの並列データ ウェアハウスの監視 |Microsoft Docs
description: 管理コンソールと Parallel Data Warehouse システム ビューを使用すると、Analytics Platform System でのアクティブなクエリを監視できます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 65d656b02ef0d726292a7d37aef565bf508d7662
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960492"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>アクティブなクエリの並列データ ウェアハウスの監視
この記事では、管理コンソールと、SQL Server PDW システム ビューを使用して、アクティブなクエリを監視する方法を示します。 参照してください[アプライアンスの監視、管理コンソールを使用して](monitor-the-appliance-by-using-the-admin-console.md)と[システム ビュー](tsql-system-views.md)についてこれらのツール。  
  
## <a name="prerequisites"></a>必須コンポーネント  
アクティブなクエリを監視するために使用する方法に関係なく、ログインに「すべての管理者コンソールを使用して」で説明されているアクセス許可がある[管理者コンソールを使用してアクセス許可の付与](grant-permissions.md#grant-permissions-to-use-the-admin-console)します。  
  
## <a name="PermsAdminConsole"></a>アクティブなクエリの監視  
アクティブなクエリを監視する管理コンソールと、SQL Server PDW システム ビューの両方を使用できます。 以下の手順に従います。  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>管理コンソールを使用してアクティブなクエリを監視するには  
  
1.  管理者コンソールにログオンします。 参照してください[アプライアンスの監視、管理コンソールを使用して](monitor-the-appliance-by-using-the-admin-console.md)手順についてはします。  
  
2.  上部のメニューでクリックして**クエリ**します。 クエリ、クエリとクエリの現在の状態の開始および終了時刻を送信したログインを含むアプライアンスで、最新のクエリに関する基本情報を持つテーブルが表示されます。  
  
3.  クエリ コマンドを表示するには、その行の左の列にクエリ ID 経由でマウス ポインターを置きます。  
  
    特定のクエリの詳細を表示するには、クエリ ID をクリックします。 完全なクエリやクエリの実行の各ステップのステータス情報、クエリ プランなどの情報が表示されます。 すべてのエラーが返された場合は、エラーも詳細を参照できます。 <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>システム ビューを使用してアクティブなクエリを監視するには  
プライマリ システム ビューのクエリを監視するには、 [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。 このシステム ビューを使用して、検索、`request_id`クエリ テキストに基づくアクティブまたは最近のクエリ。  
  
たとえば、次のクエリの検索、`request_id`と現在`status`からすべての列を選択するクエリに対して、`memberAddresses`テーブル。  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
後に、`request_id`されました内の他の情報を使用して、クエリで特定された、 `dm_pdw_exec_requests` 、クエリの処理について説明するテーブルまたはを使用して、 [sys.dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)個別のクエリの状態を表示するにはクエリの実行の手順を実行します。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
