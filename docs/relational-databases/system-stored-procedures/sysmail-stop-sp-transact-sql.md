---
title: sysmail_stop_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8f304337470d0117b6f44d03bf7e459c6b9f51d5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257784"
---
# <a name="sysmailstopsp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  停止してデータベース メールを停止、[!INCLUDE[ssSB](../../includes/sssb-md.md)]外部プログラムによって使用されるオブジェクト。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャは、 **msdb**データベース。  
  
 このストアド プロシージャは、送信メッセージ要求を保持し、オフにするデータベース メール キューを停止[!INCLUDE[ssSB](../../includes/sssb-md.md)]外部プログラムのライセンス認証します。  
  
 キューが停止すると、データベース メール外部プログラムではメッセージが処理されなくなります。 このストアド プロシージャを使用すると、トラブルシューティングやメンテナンスの目的でデータベース メールを停止できます。  
  
 データベース メールを開始するには使用**sysmail_start_sp**です。 注意して**sp_send_dbmail**もメール、[!INCLUDE[ssSB](../../includes/sssb-md.md)]オブジェクトを停止します。  
  
> [!NOTE]  
>  このストアド プロシージャは、データベース メールのキューだけを停止します。 このストアド プロシージャは非アクティブ化できません[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ データベースに配信します。 このストアド プロシージャでは、外部からのアクセスを縮小するために、データベース メールの拡張ストアド プロシージャを無効にすることはできません。 拡張ストアド プロシージャを無効にするを参照してください、 [Database Mail XPs オプション](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)の**sp_configure**システム ストアド プロシージャです。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、データベース メールでの停止、 **msdb**データベース。 ここではデータベース メールが有効になっていることを前提としています。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
