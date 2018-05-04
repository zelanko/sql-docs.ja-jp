---
title: sp_update_notification (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_update_notification_TSQL
- sp_update_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatenotification
ms.assetid: 3e1c3d40-8c24-46ce-a68e-ce6c6a237fda
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55234111fdda96225b1015d4090c29d9a09440a2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spupdatenotification-transact-sql"></a>sp_update_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告通知の通知方法を更新します。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_notification  
          [@alert_name =] 'alert' ,  
     [@operator_name =] 'operator' ,  
     [@notification_method =] notification  
```  
  
## <a name="arguments"></a>引数  
 [  **@alert_name =**] **'***アラート***'**  
 この通知に関連付けられている警告の名前を指定します。 *アラート*は**sysname**、既定値はありません。  
  
 [  **@operator_name =**] **'***演算子***'**  
 警告が発生したときに通知するオペレーターです。 *演算子*は**sysname**、既定値はありません。  
  
 [  **@notification_method =**]*通知*  
 オペレーターが通知を受ける方法を指定します。 *通知*は**tinyint**, で、既定値はありませんはこれらの値の 1 つ以上指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|[電子メール]|  
|**2**|[ポケットベル]|  
|**4**|**net send**|  
|**7**|すべての方法|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_update_notification**から実行する必要があります、 **msdb**データベース。  
  
 通知を更新するには、指定されたを使用して必要なアドレス情報を持っていないユーザーのオペレーターの*notification_method*です。 電子メールのメッセージやポケットベルによる通知に失敗した場合は、Microsoft SQL Server エージェント エラー ログに失敗がレポートされます。  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例に送信される通知の通知方法を変更する`François Ajenstat`アラート`Test Alert`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_notification  
   @alert_name = N'Test Alert',  
   @operator_name = N'François Ajenstat',  
   @notification_method = 7;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
