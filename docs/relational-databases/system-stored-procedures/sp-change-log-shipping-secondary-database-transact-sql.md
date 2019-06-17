---
title: sp_change_log_shipping_secondary_database (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_secondary_database
- sp_change_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_secondary_database
ms.assetid: 3ebcf2f1-980f-4543-a84b-fbaeea54eeac
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 136771c5bf691155b4547963fa2b6bd035f3f039
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62994231"
---
# <a name="spchangelogshippingsecondarydatabase-transact-sql"></a>sp_change_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セカンダリ データベースの設定を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database',  
[, [ @restore_delay = ] 'restore_delay']  
[, [ @restore_all = ] 'restore_all']  
[, [ @restore_mode = ] 'restore_mode']  
[, [ @disconnect_users = ] 'disconnect_users']  
[, [ @block_size = ] 'block_size']  
[, [ @buffer_count = ] 'buffer_count']  
[, [ @max_transfer_size = ] 'max_transfer_size']  
[, [ @restore_threshold = ] 'restore_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
```  
  
## <a name="arguments"></a>引数  
`[ @restore_delay = ] 'restore_delay'` セカンダリ サーバーが指定されたバックアップ ファイルを復元する前に待機する分単位の時間数。 *restore_delay*は**int** NULL にすることはできません。 既定値は 0 です。  
  
`[ @restore_all = ] 'restore_all'` 場合 1、セカンダリ サーバーに設定するは、復元ジョブを実行すると、すべてのトランザクション ログ バックアップを復元します。 それ以外の場合、1 つのファイルを復元した後を停止します。 *restore_all*は**ビット**NULL にすることはできません。  
  
`[ @restore_mode = ] 'restore_mode'` セカンダリ データベースの復元モード。  
  
 0 = NORECOVERY でログを復元。  
  
 1 = STANDBY でログを復元します。  
  
 *復元*は**ビット**NULL にすることはできません。  
  
`[ @disconnect_users = ] 'disconnect_users'` 場合 1 をユーザーに設定するは、復元操作が実行されると、セカンダリ データベースから切断されます。 既定 = 0。 *disconnect_users*は**ビット**NULL にすることはできません。  
  
`[ @block_size = ] 'block_size'` サイズ (バイト単位) をバックアップ デバイスのブロック サイズとして使用されます。 *block_size*は**int**を既定値は-1。  
  
`[ @buffer_count = ] 'buffer_count'` バックアップまたは復元操作で使用されるバッファーの合計数。 *buffer_count*は**int**を既定値は-1。  
  
`[ @max_transfer_size = ] 'max_transfer_size'` サイズをバイト単位の最大入力または出力要求によって発行された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ デバイスにします。 *max_transfersize*は**int** NULL にすることができます。  
  
`[ @restore_threshold = ] 'restore_threshold'` 許容経過時間を分単位の数は、アラートを生成する前に、操作を復元します。 *restore_threshold*は**int** NULL にすることはできません。  
  
`[ @threshold_alert = ] 'threshold_alert'` 復元のしきい値を超えたときに発生するアラートです。 *threshold_alert*は**int**、既定値 14420 はします。  
  
`[ @threshold_alert_enabled = ] 'threshold_alert_enabled'` アラートがあるかどうかを指定する場合に発生します*restore_threshold*を超過します。 1 = 有効になっています。0 = 無効になっています。 *threshold_alert_enabled*は**ビット**NULL にすることはできません。  
  
`[ @history_retention_period = ] 'history_retention_period'` 分の履歴を保持する時間の長さです。 *history_retention_period*は**int**します。1440 の値が指定されていない場合適用されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_change_log_shipping_secondary_database**から実行する必要があります、**マスター**セカンダリ サーバー上のデータベース。 このストアド プロシージャでは次の処理が行われます。  
  
1.  設定を変更、 **log_shipping_secondary_database**に応じてを記録します。  
  
2.  ローカル監視レコードを変更**log_shipping_monitor_secondary**セカンダリ サーバーを使用して、指定された引数に必要な場合。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して**sp_change_log_shipping_secondary_database**データベースのセカンダリ データベースのパラメーターを更新する**LogShipAdventureWorks**します。  
  
```  
EXEC master.dbo.sp_change_log_shipping_secondary_database   
 @secondary_database =  'LogShipAdventureWorks'  
,  @restore_delay = 0  
,  @restore_all = 1  
,  @restore_mode = 0  
,  @disconnect_users = 0  
,  @threshold_alert = 14420  
,  @threshold_alert_enabled = 1  
,  @history_retention_period = 14420;  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
