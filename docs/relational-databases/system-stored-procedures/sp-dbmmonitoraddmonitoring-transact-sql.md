---
title: sp_dbmmonitoraddmonitoring (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aa3215b176fe96b0e449f95b01afa79f20d6371
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンスのミラー化されたデータベースごとにミラーリングの状態を定期的に更新する、データベース ミラーリング監視ジョブを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>引数  
 *update_period*  
 更新間隔を分単位で指定します。 指定できる値は 1 ～ 120 分です。 既定値は 1 分です。  
  
> [!NOTE]  
>  更新間隔が短すぎると、クライアントへの応答時間が長くなることがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このプロシージャを実行するには、サーバー インスタンス上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを実行できることが必要です。また、データベース ミラーリング監視ジョブを実行するにはエージェントが実行中であることが必要です。  
  
 データベース ミラーリングが開始された場合[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 **sp_dbmmonitoraddmonitoring**プロシージャが自動的に実行します。 ALTER DATABASE ステートメントを使用して手動でのミラーリングを開始する場合、サーバー インスタンスでミラー データベースを監視する必要がありますを実行する**sp_dbmmonitoraddmonitoring**手動でします。  
  
> [!NOTE]  
>  実行する場合**sp_dbmmonitoraddmonitoring**データベース ミラーリングを設定する前に監視ジョブは実行されますが、データベース ミラーリング監視の履歴が格納されている状態テーブルは更新されません。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、の更新間隔で監視を開始`3`分です。  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリングと &#40; の監視SQL Server と &#41; です。](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
