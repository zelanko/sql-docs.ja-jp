---
title: sp_help_alert (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bca9c53780bb3258f73a274240c0bb5e63e126c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796583"
---
# <a name="sphelpalert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のサーバーに対して定義された警告に関する情報をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>引数  
`[ @alert_name = ] 'alert_name'` アラートの名前。 *alert_name*は**nvarchar (128)** します。 場合*alert_name*が指定されていないすべてのアラートに関する情報が返されます。  
  
`[ @order_by = ] 'order_by'` 結果を生成するために使用する並べ替え順。 *order_by*は**sysname**、既定値は N '*名前*'。  
  
`[ @alert_id = ] alert_id` 情報をレポートする警告の識別番号。 *alert_id*は**int**、既定値は NULL です。  
  
`[ @category_name = ] 'category'` アラートのカテゴリ。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
`[ @legacy_format = ] legacy_format` レガシ バージョンの結果セットを生成するかどうかです。 *legacy_format*は**ビット**、既定値は**0**します。 ときに*legacy_format*は**1**、 **sp_help_alert**によって返される結果セットを返す**sp_help_alert** Microsoft SQL Server 2000 でします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ときに**@legacy_format**は**0**、 **sp_help_alert**次の結果セットが生成されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|システムによって割り当てられた一意な整数識別子。|  
|**name**|**sysname**|アラート名 (たとえば、デモします。完全な**msdb**ログ)。|  
|**event_source**|**nvarchar(100)**|イベントのソース。 常に**MSSQLServer**の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|警告を定義したメッセージ エラー番号。 (通常、エラー番号に対応して、 **sysmessages**テーブル)。 重大度を使用して、警告を定義する場合**message_id**は**0**または NULL。|  
|**severity**|**int**|重大度レベル (から**9**を通じて**25**、 **110**、 **120**、 **130**、または**140**)アラートを定義するとします。|  
|**enabled**|**tinyint**|警告が現在有効かどうかの状態 (**1**) かどうか (**0**)。 有効でない警告は送信されません。|  
|**delay_between_responses**|**int**|警告に応答までの秒の期間、待機します。|  
|**last_occurrence_date**|**int**|警告が最後に発生した日付。|  
|**last_occurrence_time**|**int**|最後に、アラートが発生した時刻。|  
|**last_response_date**|**int**|によって日付が最後に警告が応答する、 **SQLServerAgent**サービス。|  
|**last_response_time**|**int**|によって、時間が最後に警告が応答する、 **SQLServerAgent**サービス。|  
|**notification_message**|**nvarchar(512)**|省略可能な追加メッセージが電子メールまたはポケットベルの通知の一部としてオペレーターに送信します。|  
|**include_event_description**|**tinyint**|Microsoft Windows アプリケーション ログからの SQL Server エラーの説明を通知メッセージに含めるかどうか。|  
|**database_name**|**sysname**|データベースの警告が、エラーが発生する必要があります。 データベース名が NULL の場合は、エラーの発生場所に関係なく警告が発生します。|  
|**event_description_keyword**|**nvarchar(100)**|Windows アプリケーション ログ内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの説明。これには、提供されたものと同様の文字シーケンスが含まれている必要があります。|  
|**occurrence_count**|**int**|警告が発生した回数。|  
|**count_reset_date**|**int**|日付、 **occurrence_count**が最後にリセットします。|  
|**count_reset_time**|**int**|時間、 **occurrence_count**が最後にリセットします。|  
|**job_id**|**uniqueidentifier**|警告に応答して実行するジョブの識別番号。|  
|**job_name**|**sysname**|警告に応答して実行されるジョブの名前。|  
|**has_notification**|**int**|1 つまたは複数の演算子はこのアラートの通知を受け取る場合は 0 以外の値。 値は、次の値 (和) の 1 つ以上です。<br /><br /> **1**= 電子メールによる通知<br /><br /> **2**= ポケットベルによる通知<br /><br /> **4**= が**net send**通知します。|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|場合**型**は**2**、この列は、パフォーマンス条件の定義を示しています。 それ以外の場合、列が NULL です。|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 の場合は常に '[Uncategorized]' となります。|  
|**wmi_namespace**|**sysname**|場合**型**は**3**、この列は、WMI イベントの名前空間を示します。|  
|**wmi_query**|**nvarchar(512)**|場合**型**は**3**、この列は、WMI イベントのクエリを示しています。|  
|**type**|**int**|イベントの種類:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]イベント警告<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンス警告<br /><br /> **3** = WMI イベント警告|  
  
 ときに**@legacy_format**は**1**、 **sp_help_alert**次の結果セットが生成されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|システムによって割り当てられた一意な整数識別子。|  
|**name**|**sysname**|アラート名 (たとえば、デモします。完全な**msdb**ログ)。|  
|**event_source**|**nvarchar(100)**|イベントのソース。 常に**MSSQLServer**の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]version 7.0|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|警告を定義したメッセージ エラー番号。 (通常、エラー番号に対応して、 **sysmessages**テーブル)。 重大度を使用して、警告を定義する場合**message_id**は**0**または NULL。|  
|**severity**|**int**|重大度レベル (から**9**を通じて**25**、 **110**、 **120**、 **130**、または 1**40**)アラートを定義するとします。|  
|**enabled**|**tinyint**|警告が現在有効かどうかの状態 (**1**) かどうか (**0**)。 有効でない警告は送信されません。|  
|**delay_between_responses**|**int**|警告に応答までの秒の期間、待機します。|  
|**last_occurrence_date**|**int**|警告が最後に発生した日付。|  
|**last_occurrence_time**|**int**|最後に、アラートが発生した時刻。|  
|**last_response_date**|**int**|によって日付が最後に警告が応答する、 **SQLServerAgent**サービス。|  
|**last_response_time**|**int**|によって、時間が最後に警告が応答する、 **SQLServerAgent**サービス。|  
|**notification_message**|**nvarchar(512)**|省略可能な追加メッセージが電子メールまたはポケットベルの通知の一部としてオペレーターに送信します。|  
|**include_event_description**|**tinyint**|あるかどうかの説明、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows アプリケーション ログからのエラーを通知メッセージの一部として含めることがあります。|  
|**database_name**|**sysname**|データベースの警告が、エラーが発生する必要があります。 データベース名が NULL の場合は、エラーの発生場所に関係なく警告が発生します。|  
|**event_description_keyword**|**nvarchar(100)**|Windows アプリケーション ログ内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの説明。これには、提供されたものと同様の文字シーケンスが含まれている必要があります。|  
|**occurrence_count**|**int**|警告が発生した回数。|  
|**count_reset_date**|**int**|日付、 **occurrence_count**が最後にリセットします。|  
|**count_reset_time**|**int**|時間、 **occurrence_count**が最後にリセットします。|  
|**job_id**|**uniqueidentifier**|ジョブ識別番号。|  
|**job_name**|**sysname**|警告に応答して実行するオンデマンド ジョブ。|  
|**has_notification**|**int**|1 つまたは複数の演算子はこのアラートの通知を受け取る場合は 0 以外の値。 値は次のとおりです。複数の場合は OR で表されます。<br /><br /> **1**= 電子メールによる通知<br /><br /> **2**= ポケットベルによる通知<br /><br /> **4**= が**net send**通知します。|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] 。|  
|**performance_condition**|**nvarchar(512)**|場合**型**は**2**、この列は、パフォーマンス条件の定義を示しています。 場合**型**は**3**、この列は、WMI イベントのクエリを示しています。 それ以外の場合、列が NULL です。|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] 常に '**[未分類]**' の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]7.0。|  
|**type**|**int**|アラートの種類:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]イベント警告<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンス警告<br /><br /> **3** = WMI イベント警告|  
  
## <a name="remarks"></a>コメント  
 **sp_help_alert**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
 詳細については**SQLAgentOperatorRole**を参照してください[SQL Server エージェント固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)します。  
  
## <a name="examples"></a>使用例  
 次の例では、`Demo: Sev. 25 Errors` 警告に関する情報をレポートします。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
