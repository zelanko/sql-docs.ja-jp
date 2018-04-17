---
title: sp_delete_log_shipping_primary_database (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
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
- sp_delete_log_shipping_primary_database
- sp_delete_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_database
ms.assetid: cb1d5d00-2805-4d47-bd04-545232067345
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0583ca04a83e4abb4a815a7ac94eb3b0c99948b3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletelogshippingprimarydatabase-transact-sql"></a>sp_delete_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  バックアップ ジョブ、ローカル履歴、およびリモート履歴を含むプライマリ データベースのログ配布を削除します。 のみを使用して、セカンダリ データベースを削除した後にこのストアド プロシージャを使用して**sp_delete_log_shipping_primary_secondary**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_log_shipping_primary_database  
[ @database = ] 'database'  
```  
  
## <a name="arguments"></a>引数  
 [  **@database =** ] '*データベース*'  
 ログ配布プライマリ データベースの名前を指定します。 *データベース*は**sysname**、既定値はありません、NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [なし] :  
  
## <a name="remarks"></a>解説  
 **sp_delete_log_shipping_primary_database**から実行する必要があります、**マスター**プライマリ サーバー上のデータベースです。 このストアド プロシージャでは次の処理が行われます。  
  
1.  指定したプライマリ データベースのバックアップ ジョブを削除する。  
  
2.  ローカル監視レコードを削除**log_shipping_monitor_primary**プライマリ サーバーでします。  
  
3.  対応するエントリを削除**log_shipping_monitor_history_detail**と**log_shipping_monitor_error_detail**です。  
  
4.  監視サーバーがプライマリ サーバーと異なる場合は、ある監視レコードを削除します。 **log_shipping_monitor_primary** 、監視サーバー。  
  
5.  対応するエントリを削除**log_shipping_monitor_history_detail**と**log_shipping_monitor_error_detail**監視サーバー。  
  
6.  内のエントリを削除**log_shipping_primary_databases**このプライマリ データベースに対して。  
  
7.  呼び出し**sp_delete_log_shipping_alert_job**監視サーバー。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して**sp_delete_log_shipping_primary_database** 、プライマリ データベースを削除する**AdventureWorks2012**です。  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_database @database = N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
