---
title: サーバーのポーリング | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- target servers [SQL Server], polling interval
- polling master servers [SQL Server]
- server polling [SQL Server]
- master servers [SQL Server], polling
- polling interval [SQL Server]
ms.assetid: 96f5fd43-3edd-4418-9dd0-4d34e618890e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9f2245f6f524c9087d3c8d6a9d2c9c22d18120a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="poll-servers"></a>サーバーのポーリング
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

マルチサーバー管理を実装している場合、対象サーバーからマスター サーバーに定期的にアクセスし、既に実行したジョブの情報をアップロードして新しいジョブをダウンロードします。 マスター サーバーにアクセスする処理は *サーバー ポーリング* と呼ばれ、定期的な *ポーリング間隔*で行われます。  
  
## <a name="polling-intervals"></a>ポーリング間隔  
対象サーバーからマスター サーバーに接続し、命令をダウンロードしてジョブの実行結果をアップロードする頻度をポーリング間隔 (既定値は 1 分) で制御します。  
  
対象サーバーからマスター サーバーにポーリングするとき、対象サーバーに割り当てられる操作を **msdb** データベースの **sysdownloadlist** テーブルから読み取ります。 読み取った操作により、マルチサーバー ジョブや対象サーバーのさまざまな動作を制御します。 操作の例には、ジョブの削除、ジョブの挿入、ジョブの開始、対象サーバーのポーリング間隔の更新などがあります。  
  
操作は次のいずれかの方法で **sysdownloadlist** テーブルに書き込まれます。  
  
-   **sp_post_msx_operation** ストアド プロシージャを使用して明示的に行います。  
  
-   他のジョブ ストアド プロシージャを使用して暗黙的に行います。  
  
ジョブ ストアド プロシージャを使用してマルチサーバー ジョブ スケジュールやジョブ ステップを変更する場合、または SQL-DMO (SQL 分散管理オブジェクト) を使用してマルチサーバー ジョブを制御する場合、マルチサーバー ジョブのステップやスケジュールを変更してから次のコマンドを実行します。  
  
```  
EXECUTE msdb.dbo.sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
このコマンドを実行すると、現在のジョブ定義が対象サーバーと同期されます。  
  
次のアイテムを使用する場合、操作を明示的に書き込む必要はありません。  
  
-   Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用してマルチサーバー ジョブを制御する場合。  
  
-   ジョブ スケジュールまたはジョブ ステップを変更しないジョブ ストアド プロシージャの場合。  
  
**対象サーバーからマスター サーバーにポーリングさせるには**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>参照  
[イベントの管理](../../ssms/agent/manage-events.md)  
  
