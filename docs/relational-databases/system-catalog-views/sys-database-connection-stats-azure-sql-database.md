---
title: sys.database_connection_stats (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_connection_stats
- database_connection_stats
- database_connection_stats_TSQL
- sys.database_connection_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_connection_stats
- database_connection_stats
ms.assetid: 5c8cece0-63b0-4dee-8db7-6b43d94027ec
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ff011bc3ab4b3b8cc49fc9199f4ca2359deeb021
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663100"
---
# <a name="sysdatabaseconnectionstats-azure-sql-database"></a>sys.database_connection_stats (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  統計情報を含む[!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベース**接続**イベント、データベース接続の成功と失敗の概要について説明します。 接続イベントの詳細については、イベントの種類を参照してください。 [sys.event_log &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md)します。  
  
|統計|型|説明|  
|---------------|----------|-----------------|  
|**database_name**|**sysname**|データベースの名前です。|  
|**start_time**|**datetime2**|集計の間隔の開始日時 (UTC)。 この時刻は常に 5 分の倍数です。 以下に例を示します。<br /><br /> '2011-09-28 16:00:00'<br />'2011-09-28 16:05:00'<br />'2011-09-28 16:10:00'|  
|**end_time**|**datetime2**|集計の間隔の終了日時 (UTC)。 **End_time**は常に 5 分後に、対応するよりも**start_time**同じ行にします。|  
|**success_count**|**int**|成功した接続の数。|  
|**total_failure_count**|**int**|失敗した接続の合計数。 これは、合計の**connection_failure_count**、 **terminated_connection_count**、および**throttled_connection_count**、デッドロック イベントは含まれません。|  
|**connection_failure_count**|**int**|失敗したログインの数。|  
|**terminated_connection_count**|**int**|***のみ適用[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]v11 します。***<br /><br /> 終了された接続の数。|  
|**throttled_connection_count**|**int**|***のみ適用[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]v11 します。***<br /><br /> スロットルされた接続の数。|  
  
## <a name="remarks"></a>コメント  
  
### <a name="event-aggregation"></a>イベント集計  
 このビューのイベント情報は、5 分未満の間隔で収集および集計されます。 数の列は、特定の間隔において特定のデータベースで特定の接続イベントが発生した回数を表します。  
  
 たとえば、2012 年 2 月 5 日の 11:00 から 11:05 まで (UTC) の間に Database1 データベースへの接続が 7 回失敗した場合、この情報はこのビューの 1 つの行に表示されます。  
  
|**database_name**|**start_time**|**end_time**|**success_count**|**total_failure_count**|**connection_failure_count**|**terminated_connection_count**|**throttled_connection_count**|  
|------------------------|---------------------|-------------------|------------------------|-------------------------------|------------------------------------|---------------------------------------|--------------------------------------|  
|`Database1`|`2012-02-05 11:00:00`|`2012-02-05 11:05:00`|`0`|`7`|`7`|`0`|`0`|  
  
### <a name="interval-starttime-and-endtime"></a>間隔の start_time と end_time  
 イベントの発生時に、集計間隔にイベントが含まれている*で*または*後 * * * start_time** と*する前に * * * end_time** その間隔。 たとえば、`2012-10-30 19:25:00.0000000` に発生したイベントは、下に示す例では 2 つ目の間隔にのみ含まれます。  
  
```  
  
start_time                    end_time  
2012-10-30 19:20:00.0000000   2012-10-30 19:25:00.0000000  
2012-10-30 19:25:00.0000000   2012-10-30 19:30:00.0000000  
```  
  
### <a name="data-updates"></a>データの更新  
 このビューのデータは、時間の経過と共に累積されます。 通常、データは集計の間隔が開始してから 1 時間以内に累積されますが、すべてのデータがビューに表示されるまでに最大で 24 時間かかることがあります。 その間に、1 つの行内の情報が定期的に更新されることがあります。  
  
### <a name="data-retention"></a>[データ保有期間]  
 このビューのデータは、最大で 30 日間保持され、論理サーバーのデータベースの数と各データベースが生成する一意のイベントの数によっては、保持される期間がそれより短くなる場合があります。 この情報をより長期間にわたって保持するには、データを別のデータベースにコピーします。 ビューの最初のコピーを行った後に、そのビューの行がデータの累積に伴って更新されることがあります。 データのコピーを最新の状態に保つには、定期的に行のテーブル スキャンを行うことにより、既存の行のイベント数の増加を検出し、新しい行を特定して (開始時刻と終了時刻を使用して一意の行を識別できます)、これらの更新内容をデータのコピーに反映させます。  
  
### <a name="errors-not-included"></a>含まれていないエラー  
 すべての接続情報とエラー情報がこのビューに含まれるわけではありません。  
  
-   このビューにすべて含まれていない[!INCLUDE[ssSDS](../../includes/sssds-md.md)]データベース イベントの種類で指定されているのみエラーが発生する可能性があります、 [sys.event_log &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-event-log-azure-sql-database.md)します。  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] データセンター内でコンピューター障害が発生すると、論理サーバーの少量のデータがイベント テーブルで見つからない可能性があります。  
  
-   IP アドレスが DoSGuard によってブロックされている場合、その IP アドレスからの接続の試みのイベントは収集できないため、このビューに表示されません。  
  
## <a name="permissions"></a>アクセス許可  
 アクセス許可を持つユーザー、**マスター**データベースは、このビューに読み取り専用のアクセス権を持ちます。  
  
## <a name="example"></a>例  
 次の例は、のクエリを示しています。 **sys.database_connection_stats**を 2011 年 9 月 25 日の正午と午後 9/28/2011 (UTC) の間に発生したデータベース接続の概要を返します。 既定では、クエリの結果は並べ**start_time** (昇順)。  
  
```  
SELECT *  
FROM sys.database_connection_stats   
WHERE start_time>='2011-09-25:12:00:00' and end_time<='2011-09-28 12:00:00';  
```  
  
## <a name="see-also"></a>参照  
 [Windows Azure SQL Database のトラブルシューティング](http://msdn.microsoft.com/library/windowsazure/ee730906.aspx)  
  
  
