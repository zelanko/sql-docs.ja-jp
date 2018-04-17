---
title: sp_add_notification (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 65687af95ff4d8f608d528277e897e0cca2c70ab
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spaddnotification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告の通知を設定します。  
  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>引数  
 [ **@alert_name=** ] **'***alert***'**  
 この通知で示される警告を指定します。 *アラート*は**sysname**、既定値はありません。  
  
 [ **@operator_name=** ] **'***operator***'**  
 警告が発生したときに通知を受け取るオペレーターを指定します。 *演算子*は**sysname**、既定値はありません。  
  
 [  **@notification_method=** ] *notification_method*  
 オペレーターが通知を受ける方法を指定します。 *notification_method*は**tinyint**、既定値はありません。 *notification_method*と共にこれらの値の 1 つ以上にすることができます、 **OR**論理演算子です。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|[電子メール]|  
|**2**|[ポケットベル]|  
|**4**|**net send**|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_notification**から実行する必要があります、 **msdb**データベース。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、警告システム全体を簡単に管理できるグラフィカルなツールです。 警告システムを構成するときには、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用することをお勧めします。  
  
 警告に対応して通知を送るには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがメールを送れるようにあらかじめ構成しておく必要があります。  
  
 電子メールのメッセージやポケットベルによる通知に失敗した場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス エラー ログに失敗がレポートされます。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_notification**です。  
  
## <a name="examples"></a>使用例  
 次の例では、指定された警告 (`Test Alert`) に対応する電子メールでの通知を追加します。  
  
> **注:**この例では、`Test Alert`既に存在することと`François Ajenstat`有効な演算子の名前を指定します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
