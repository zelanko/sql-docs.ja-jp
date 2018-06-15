---
title: sp_dbmmonitorupdate (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorupdate
- sp_dbmmonitorupdate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorupdate
- database mirroring [SQL Server], monitoring
ms.assetid: 9ceb9611-4929-44ee-a406-c39ba2720fd5
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0882644bb3cef95694cee44e308b21fc627cd489
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242486"
---
# <a name="spdbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース ミラーリング監視の状態テーブルにミラー化されたデータベースごとの新しい行を挿入し、現在の保有期間より古い行を切り捨てます。 既定の保有期間は 7 日 (168 時間) です。 テーブルを更新するときに**sp_dbmmonitorupdate**パフォーマンス基準を評価します。  
  
> [!NOTE]  
>  初めて**sp_dbmmonitorupdate**実行されると、データベース ミラーリング状態テーブルを作成し、 **dbm_monitor**の固定データベース ロール、 **msdb**データベース。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 ミラーリングの状態を更新するデータベースの名前を指定します。 場合*database_name*が指定されていない、サーバー インスタンスでミラー化されたデータベースごとに状態テーブルが更新されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_dbmmonitorupdate**のコンテキストでのみ実行できる、 **msdb**データベース。  
  
 状態テーブルの列がパートナーのロールに該当しない場合、そのパートナーについて、値は NULL になります。 また、フェールオーバー時やサーバー再起動時などで、関連する情報を取得できない場合も、列の値は NULL になります。  
  
 後に**sp_dbmmonitorupdate**を作成、 **dbm_monitor**の固定データベース ロール、 **msdb**データベースでのメンバー、 **sysadmin**すべてのユーザーを追加できるは、固定サーバー ロール、 **dbm_monitor**固定データベース ロール。 **Dbm_monitor**ロールのメンバーはデータベース ミラーリングの状態を表示が、更新しますが、ないを表示または構成していないデータベース ミラーリング イベントを有効にします。  
  
 データベースのミラーリングの状態を更新するときに**sp_dbmmonitorupdate**をミラーリングのパフォーマンス測定基準の警告しきい値が指定されている最新の値を検査します。 値がしきい値を超えている場合は情報イベントをイベント ログに追加します。 すべての割合は、前回の更新時以降の平均になります。 詳細については、「 [ミラーリング パフォーマンス基準の警告しきい値および警告の使用 &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)」を参照してください。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに対してのみ、ミラーリングの状態を更新します。  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリングと &#40; の監視SQL Server と &#41; です。](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
