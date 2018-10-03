---
title: sp_refresh_log_shipping_monitor (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4382dc4de4010944e60cb37640759e91a0fc2727
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851560"
---
# <a name="sprefreshlogshippingmonitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  リモートの監視テーブルを、指定したログ配布エージェントの特定のプライマリまたはセカンダリ サーバーにある最新の情報に更新します。 このプロシージャはプライマリまたはセカンダリ サーバーで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>引数  
 [ **@agent_id=** ] **'***agent_id***'**  
 バックアップの場合はプライマリ ID、コピーまたは復元の場合はセカンダリ ID。 *agent_id*は**uniqueidentifier** NULL にすることはできません。  
  
 [ **@agent_type=** ] **'***agent_type***'**  
 ログ配布ジョブの種類を指定します。  
  
 0 = バックアップ。  
  
 1 = コピー。  
  
 2 = 復元。  
  
 *agent_type*は**tinyint** NULL にすることはできません。  
  
 [ **@database=** ] **'***database***'**  
 バックアップや復元エージェントのログ記録で使用されるプライマリまたはセカンダリ データベースを指定します。  
  
 [ **@mode** ] *n*  
 監視データを更新するか削除するかを指定します。 データ型*m* tinyint は、サポートされている値します。  
  
 1 = 更新 (既定値)。  
  
 2 = delete  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>コメント  
 **sp_refresh_log_shipping_monitor**更新、 **log_shipping_monitor_primary**、 **log_shipping_monitor_secondary**、 **log_shipping_monitor_history_detail**、および**log_shipping_monitor_error_detail**まだ転送されていないすべてのセッション情報とテーブル。 これにより、しばらくの間監視サーバーを同期していなかった場合に、監視サーバーとプライマリまたはセカンダリ サーバーを同期できます。 また、必要に応じて監視サーバーにある監視情報をクリーンアップできます。  
  
 **sp_refresh_log_shipping_monitor**から実行する必要があります、**マスター**プライマリまたはセカンダリ サーバー上のデータベース。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
