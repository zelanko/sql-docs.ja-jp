---
title: sysmail_start_sp (TRANSACT-SQL) |Microsoft Docs
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
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2fa805836387ae94cca2cba189eb4a9a9b20d8a3
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024181"
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  開始してデータベース メールを開始、[!INCLUDE[ssSB](../../includes/sssb-md.md)]外部プログラムが使用するオブジェクト。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 データベース メールが有効になっているかにインストールされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールします。 データベース メール オブジェクトを有効化およびインストールするには、データベース メール構成ウィザードを使用します。  
  
 このストアド プロシージャは、 **msdb**データベース。 このストアド プロシージャは、送信メッセージ要求を保持しているデータベース メール キューを開始し、外部プログラムに対する [!INCLUDE[ssSB](../../includes/sssb-md.md)] のアクティブ化を有効にします。  
  
 キューが開始されると、データベース メール外部プログラムではメッセージを処理できます。 この手順で、キューを停止した後に、キューを再起動するように、 **sysmail_stop_sp**ストアド プロシージャ。  
  
> [!NOTE]  
>  このストアド プロシージャは、データベース メールのキューだけを開始します。 データベースでの [!INCLUDE[ssSB](../../includes/sssb-md.md)] のメッセージ配信はアクティブになりません。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、以降ではデータベース メール、 **msdb**データベース。 ここではデータベース メールが有効になっていることを前提としています。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail XPs サーバー構成オプション](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
