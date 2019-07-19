---
title: sp_update_alert (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_alert_TSQL
- sp_update_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_alert
ms.assetid: 4bbaeaab-8aca-4c9e-abc1-82ce73090bd3
author: stevestein
ms.author: sstein
ms.openlocfilehash: baecdca82d7edcb27196c7c43d9d071a82adf792
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084947"
---
# <a name="spupdatealert-transact-sql"></a>sp_update_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のアラートの設定を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_alert   
     [ @name =] 'name'   
     [ , [ @new_name =] 'new_name']   
     [ , [ @enabled =] enabled]   
     [ , [ @message_id =] message_id]   
     [ , [ @severity =] severity]   
     [ , [ @delay_between_responses =] delay_between_responses]   
     [ , [ @notification_message =] 'notification_message']   
     [ , [ @include_event_description_in =] include_event_description_in]   
     [ , [ @database_name =] 'database']   
     [ , [ @event_description_keyword =] 'event_description_keyword']   
     [ , [ @job_id =] job_id | [@job_name =] 'job_name']   
     [ , [ @occurrence_count = ] occurrence_count]   
     [ , [ @count_reset_date =] count_reset_date]   
     [ , [ @count_reset_time =] count_reset_time]   
     [ , [ @last_occurrence_date =] last_occurrence_date]   
     [ , [ @last_occurrence_time =] last_occurrence_time]   
     [ , [ @last_response_date =] last_response_date]   
     [ , [ @last_response_time =] last_response _time]  
     [ , [ @raise_snmp_trap =] raise_snmp_trap]  
     [ , [ @performance_condition =] 'performance_condition' ]   
     [ , [ @category_name =] 'category']  
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'name'` 更新する警告の名前。 *名前*は**sysname**、既定値はありません。  
  
`[ @new_name = ] 'new_name'` アラートの新しい名前。 名前は一意である必要があります。 *新しい名前*は**sysname**、既定値は NULL です。  
  
`[ @enabled = ] enabled` 警告を有効になっているかどうかを指定します (**1**) または有効になっていません (**0**)。 *有効になっている*は**tinyint**、既定値は NULL です。 起動には、アラートを有効にする必要があります。  
  
`[ @message_id = ] message_id` 警告の定義用の新しいメッセージまたはエラー番号。 通常、 *message_id*でエラー番号に対応する、 **sysmessages**テーブル。 *message_id*は**int**、既定値は NULL です。 アラートの重大度レベルの設定が場合にのみ、ID を使用できるメッセージ**0**します。  
  
`[ @severity = ] severity` 新しい重大度レベル (から**1**を通じて**25**) 警告の定義。 すべて[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定した重大度を持つ Windows アプリケーション ログに送信されるメッセージには、アラートがアクティブ化します。 *重大度*は**int**、既定値は NULL です。 警告のメッセージ ID の設定が場合にのみ、重大度レベルを使用できます**0**します。  
  
`[ @delay_between_responses = ] delay_between_responses` 新しい待機時間を秒単位の警告に応答します。 *delay_between_responses*は**int**、既定値は NULL です。  
  
`[ @notification_message = ] 'notification_message'` 変更されたテキスト、電子メールの一部としてオペレーターに送信される追加メッセージの**net send**、またはポケットベル通知します。 *このパラメーター*は**nvarchar (512)** 、既定値は NULL です。  
  
`[ @include_event_description_in = ] include_event_description_in` 指定するかどうかの説明、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows アプリケーション ログからのエラーは、通知メッセージに含める必要があります。 *include_event_description_in*は**tinyint**、既定値は null の場合、これらの値の 1 つ以上を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|なし|  
|**1**|[電子メール]|  
|**2**|[ポケットベル]|  
|**4**|**net send**|  
|**7**|All|  
  
`[ @database_name = ] 'database'` 警告のエラーが発生する必要がある、データベースの名前。 *データベース*は**sysname です。** 角かっこ () で囲まれた名前を指定することはできません。 既定値は NULL です。  
  
`[ @event_description_keyword = ] 'event_description_keyword'` エラー メッセージのログのエラーの説明 で確認する必要がありますの文字のシーケンス。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 式のように、パターン検索文字を使用できます。 *event_description_keyword*は**nvarchar (100)** 、既定値は NULL です。 このパラメーターはオブジェクト名をフィルター処理するために役立ちます (たとえば、 **%customer_table%** )。  
  
`[ @job_id = ] job_id` ジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。 場合*job_id*が指定されている*job_name*省略する必要があります。  
  
`[ @job_name = ] 'job_name'` この警告に応答を実行するジョブの名前。 *job_name*は**sysname**、既定値は NULL です。 場合*job_name*が指定されている*job_id*省略する必要があります。  
  
`[ @occurrence_count = ] occurrence_count` 警告が発生した回数をリセットします。 *occurrence_count*は**int**、既定値は NULL の場合にのみ設定できます**0**します。  
  
`[ @count_reset_date = ] count_reset_date` 発生回数を最後にリセットする日付をリセットします。 *count_reset_date*は**int**、既定値は NULL です。  
  
`[ @count_reset_time = ] count_reset_time` 発生回数を最後にリセット時刻をリセットします。 *count_reset_time*は**int**、既定値は NULL です。  
  
`[ @last_occurrence_date = ] last_occurrence_date` 最後に、アラートが発生した日付をリセットします。 *last_occurrence_date*は**int**、既定値は NULL の場合にのみ設定できます**0**します。  
  
`[ @last_occurrence_time = ] last_occurrence_time` 最後に、アラートが発生した時刻をリセットします。 *last_occurrence_time*は**int**、既定値は NULL の場合にのみ設定できます**0**します。  
  
`[ @last_response_date = ] last_response_date` アラートが最後に応答した sql server エージェント サービスの日付をリセットします。 *last_response_date*は**int**、既定値は NULL の場合にのみ設定できます**0**します。  
  
`[ @last_response_time = ] last_response_time` アラートが最後に応答した sql server エージェント サービスの時刻をリセットします。 *last_response_time*は**int**、既定値は NULL の場合にのみ設定できます**0**します。  
  
`[ @raise_snmp_trap = ] raise_snmp_trap` 予約されています。  
  
`[ @performance_condition = ] 'performance_condition'` 形式で表される値 **'***itemcomparatorvalue***'** します。 *performance_condition*は**nvarchar (512)** 、既定値は null の場合、これらの要素で構成されています。  
  
|Format 要素|説明|  
|--------------------|-----------------|  
|*アイテム*|パフォーマンス オブジェクト、パフォーマンス カウンター、またはカウンターの名前付きインスタンス。|  
|*比較演算子*|これらの演算子のいずれか: **>** 、 **<** 、 **=**|  
|*[値]*|カウンターの数値|  
  
`[ @category_name = ] 'category'` アラートのカテゴリの名前。 *カテゴリ*は**sysname**既定値は NULL です。  
  
`[ @wmi_namespace = ] 'wmi_namespace'` イベントを照会する WMI 名前空間。 *wmi_namespace*は**sysname**、既定値は NULL です。  
  
`[ @wmi_query = ] 'wmi_query'` このクエリは、警告に対する WMI イベントを指定します。 *wmi_query*は**nvarchar (512)** 、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 のみ**sysmessages**に書き込まれた、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログは、警告を発することができます。  
  
 **sp_update_alert**パラメーター値が提供される警告の設定のみを変更します。 パラメーターを省略すると、現在の設定は保持されます。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーをこのストアド プロシージャを実行するのメンバーである必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、警告が有効になっている `Test Alert` の設定を `0` (無効) に変更します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_alert  
    @name = N'Test Alert',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
