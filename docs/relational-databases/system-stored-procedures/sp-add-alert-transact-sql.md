---
title: sp_add_alert (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 750d299b951b403ed6fe51baa43b047505860c3f
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493804"
---
# <a name="spaddalert-transact-sql"></a>sp_add_alert (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アラートを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_alert [ @name = ] 'name'   
     [ , [ @message_id = ] message_id ]   
     [ , [ @severity = ] severity ]   
     [ , [ @enabled = ] enabled ]  
     [ , [ @delay_between_responses = ] delay_between_responses ]   
     [ , [ @notification_message = ] 'notification_message' ]   
     [ , [ @include_event_description_in = ] include_event_description_in ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @event_description_keyword = ] 'event_description_keyword_pattern' ]   
     [ , { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ]   
     [ , [ @raise_snmp_trap = ] raise_snmp_trap ]   
     [ , [ @performance_condition = ] 'performance_condition' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'name'` アラートの名前。 この名前は、警告に対する応答として送信される電子メールまたはポケットベルのメッセージに表示されます。 一意であり、割合を含めることができます (**%**) 文字。 *名前*は**sysname**、既定値はありません。  
  
`[ @message_id = ] message_id` 警告を定義したメッセージ エラー番号。 (通常、エラー番号に対応して、 **sysmessages**テーブルです)。*message_id*は**int**、既定値は**0**します。 場合*重大度*、警告を定義するために使用*message_id*あります**0**または NULL。  
  
> [!NOTE]  
>  のみ**sysmessages** Microsoft Windows アプリケーション ログに書き込まれたエラーが原因で、アラートを送信します。  
  
`[ @severity = ] severity` 重大度レベル (から**1**を通じて**25**)、アラートを定義します。 すべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にメッセージが格納されている、 **sysmessages**テーブルに送信される、[!INCLUDE[msCoName](../../includes/msconame-md.md)]指定された重大度を持つ Windows アプリケーション ログと警告を送信します。 *重大度*は**int**、既定値は 0。 場合*message_id* 、警告を定義するために使用*重大度*あります**0**します。  
  
`[ @enabled = ] enabled` アラートの現在の状態を示します。 *有効になっている*は**tinyint**、既定値は 1 (有効)。 場合**0**アラートが有効でないとは発生しません。  
  
`[ @delay_between_responses = ] delay_between_responses` 待機時間を秒単位の警告に応答します。 *delay_between_responses*は**int**、既定値は**0**、つまりが発生するたび、アラートの応答) 間の待機中ではありません。 応答は、いずれかまたは両方の形式にできます。  
  
-   1 つまたは複数の通知が電子メールまたはポケットベル経由で送信します。  
  
-   実行するジョブ。  
  
 この値を設定するには、望ましくない電子メール メッセージ、アラートは、短時間で繰り返し発生時に送信されるを防ぐためになります。  
  
`[ @notification_message = ] 'notification_message'` 電子メールの一部としてオペレーターに送信される追加の省略可能なメッセージ**net send**、またはポケットベル通知します。 *このパラメーター*は**nvarchar (512)**、既定値は NULL です。 指定する*このパラメーター*は書き加えるなど特別な注意を追加するために便利です。  
  
`[ @include_event_description_in = ] include_event_description_in` あるかどうかの説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーが通知メッセージの一部として含めるする必要があります。 *include_event_description_in*は**tinyint**、既定値は**5** (電子メールと**net send**)、およびは 1 つまたはと共にこれらの値の詳細は、**または**論理演算子です。  
  
> [!IMPORTANT]
>  今後のバージョンの **では、** エージェントからポケットベル オプションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オプションが削除される予定です。 新しい開発作業では、これらの機能の使用を避け、現在これらの機能を使用しているアプリケーションは修正するようにしてください。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|なし|  
|**1**|[電子メール]|  
|**2**|[ポケットベル]|  
|**4**|**net send**|  
  
`[ @database_name = ] 'database'` データベースの警告が、エラーが発生する必要があります。 場合*データベース*が指定されていない、エラーの発生場所に関係なく警告が発生します。 *データベース*は**sysname**します。 角かっこ () で囲まれた名前を指定することはできません。 既定値は、NULL です。  
  
`[ @event_description_keyword = ] 'event_description_keyword_pattern'` 文字のシーケンスの説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のようなエラーがある必要があります。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 式のように、パターン検索文字を使用できます。 *event_description_keyword_pattern*は**nvarchar (100)**、既定値は NULL です。 このパラメーターはオブジェクト名をフィルター処理するために役立ちます (たとえば、 **%customer_table%**)。  
  
`[ @job_id = ] job_id` このアラートに応答して実行するジョブのジョブ識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'` この警告に応答して実行するジョブの名前。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
`[ @raise_snmp_trap = ] raise_snmp_trap` では未実装[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン 7.0。 *raise_snmp_trap*は**tinyint**、既定値は 0。  
  
`[ @performance_condition = ] 'performance_condition'` 形式で表される値は、'*itemcomparatorvalue*'。 *performance_condition*は**nvarchar (512)** 既定値は null の場合、これらの要素で構成されています。  
  
|Format 要素|説明|  
|--------------------|-----------------|  
|*アイテム*|パフォーマンス オブジェクト、パフォーマンス カウンター、またはカウンターの名前付きインスタンス。|  
|*比較演算子*|これらの演算子のいずれか: >、<、または =|  
|*[値]*|カウンターの数値|  
  
`[ @category_name = ] 'category'` アラートのカテゴリの名前。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
`[ @wmi_namespace = ] 'wmi_namespace'` イベントを照会する WMI 名前空間。 *wmi_namespace*は**sysname**、既定値は NULL です。 サポートされるのはローカル サーバーの名前空間だけです。  
  
`[ @wmi_query = ] 'wmi_query'` このクエリは、警告に対する WMI イベントを指定します。 *wmi_query*は**nvarchar (512)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_add_alert**から実行する必要があります、 **msdb**データベース。  
  
 これらは、エラーやメッセージによって生成される状況[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アプリケーションは、Windows アプリケーション ログに送信され、警告を生成するため。  
  
-   重大度が 19 以上**sys.messages**エラー  
  
-   WITH LOG 構文で任意の RAISERROR ステートメント  
  
-   すべて**sys.messages**エラーは、変更またはを使用して作成**sp_altermessage**  
  
-   すべてのイベントを使用してログに記録**xp_logevent**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、警告システム全体を簡単に管理できるグラフィカルなツールです。警告の基本構成を設定するには、SQL Server Management Studio を使用することをお勧めします。  
  
 警告が正常に動作しないときは、次のことを確認してください。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスが実行されています。  
  
-   Windows アプリケーション ログにイベントが表示されること。  
  
-   アラートが有効になっているとします。  
  
-   **xp_logevent** で生成されたイベントは master データベースで発生します。 このため、 **xp_logevent** では、警告の **@database_name** が **'master'** または NULL になっていないと、警告が起動されません。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sp_add_alert** を実行できるのは、 **sysadmin**固定サーバー ロールのメンバーだけです。  
  
## <a name="examples"></a>使用例  
 次の例では、警告発生時にジョブ `Back up the AdventureWorks2012 Database` を実行する Test Alert という警告を追加します。  
  
> [!NOTE]  
>  この例では、メッセージ 55001 と`Back up the AdventureWorks2012 Database`ジョブが既に存在します。 例では、例示を目的としてのみ表示されます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_alert  
    @name = N'Test Alert',  
    @message_id = 55001,   
   @severity = 0,   
   @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
   @job_name = N'Back up the AdventureWorks2012 Database' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_update_alert &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
