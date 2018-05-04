---
title: sp_help_notification (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
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
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cfc84d05393174ba804a5c3fc407da0e2fbe2159
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpnotification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたオペレーターに対する警告の一覧、または指定された警告の送信先であるオペレーターの一覧をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@object_type =**] **'***object_type***'**  
 返される情報の種類を指定します。 *object_type*は**char (9)**、既定値はありません。 *object_type*指定されたオペレーター名に割り当てられている警告の一覧を表示するアラートを指定できます*、*または演算子では、指定された警告名を担当する演算子の一覧を表示する*です。*  
  
 [  **@name =**] **'***名前***'**  
 演算子名 (場合*object_type* is 演算子) または警告の名前 (場合*object_type*アラートは、)。 *名前*は**sysname**、既定値はありません。  
  
 [ **@enum_type =**] **'***enum_type***'**  
 *Object_type*返される情報です。 *enum_type*は「ACTUAL」は、ほとんどの場合。 *enum_type*は**char (10)**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|ACTUAL|だけを表示、 *object_types*に関連付けられている*名前*です。|  
|ALL|すべてを一覧表示、*object_types*に関連付けられていないものも含め*名前*です。|  
|TARGET|だけを表示、 *object_types* 、指定された照合*target_name*との関連付けに関係なく、*名前*です。|  
  
 [  **@notification_method =**] *notification_method*  
 返される通知方法の列を表す数値を指定します。 *notification_method*は**tinyint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|電子メール: だけを返す、 **use_email**列です。|  
|**2**|ポケットベル: だけを返す、 **use_pager**列です。|  
|**4**|NetSend: だけを返す、 **use_netsend**列です。|  
|**7**|すべて: すべての列を返します。|  
  
 [ **@target_name =**] **'***target_name***'**  
 検索する警告の名前 (場合*object_type*アラートは、) を検索するには、するオペレーター名を指定 (場合*object_type* is 演算子)。 *target_name*場合にのみ必要*enum_type*ターゲットです。 *target_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-valves"></a>戻り値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 場合*object_type*は**アラート**、結果セットには、指定した演算子のすべてのアラートが一覧表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|警告識別番号。|  
|**alert_name**|**sysname**|警告名。|  
|**use_email**|**int**|電子メールを使用して、オペレーターに通知します。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**use_pager**|**int**|ポケットベルを使用して、オペレーターに通知します。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**use_netsend**|**int**|オペレーターへの通知にネットワーク ポップアップを使用するかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**has_email**|**int**|この警告で送信する電子メール通知の数。|  
|**has_pager**|**int**|この警告で送信するポケットベル通知の数。|  
|**has_netsend**|**int**|数**net send**この警告で送信する通知。|  
  
 場合**object_type**は**演算子**、結果セットには、指定された警告のすべての演算子が一覧表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|オペレーター識別番号。|  
|**operator_name**|**sysname**|オペレーター名。|  
|**use_email**|**int**|オペレーターへの通知に電子メールを使用するかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**use_pager**|**int**|オペレーターへの通知にポケットベルを使用するかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**use_netsend**|**int**|オペレーターに通知するために使用するネットワーク ポップアップ。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**has_email**|**int**|オペレーターが電子メール アドレスを持っているかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**has_pager**|**int**|オペレーターがポケットベル アドレスを持っているかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
|**has_netsend**|**int**|オペレーターに net send 通知が構成されているかどうか。<br /><br /> **1** = はい<br /><br /> **0** = いいえ|  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャを実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャを実行するには、 **sysadmin** 固定サーバー ロールのメンバーであることが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. 特定のオペレーターに対する警告を表示する  
 次の例では、オペレーター `François Ajenstat` が通知を受け取るすべての警告を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>B. 特定の警告の送信先となるオペレーターを表示する  
 次の例は、任意の種類の通知を受信するすべてのオペレーターを返して、`Test Alert`アラートです。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
