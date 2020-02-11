---
title: sysmail_stop_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 753375d139a03d5c0cec20dc994d83399e04f094
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037401"
---
# <a name="sysmail_stop_sp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  外部プログラムが使用し[!INCLUDE[ssSB](../../includes/sssb-md.md)]ているオブジェクトを停止することによって、データベースメールを停止します。  
  
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
 このストアドプロシージャは**msdb**データベースにあります。  
  
 このストアドプロシージャは、送信メッセージ要求を保持するデータベースメールキューを停止[!INCLUDE[ssSB](../../includes/sssb-md.md)]し、外部プログラムのアクティブ化をオフにします。  
  
 キューが停止されると、データベースメール外部プログラムはメッセージを処理しません。 このストアド プロシージャを使用すると、トラブルシューティングやメンテナンスの目的でデータベース メールを停止できます。  
  
 データベースメールを開始するには、 **sysmail_start_sp**を使用します。 オブジェクトが**** 停止しても、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] sp_send_dbmail はメールを受け取ることに注意してください。  
  
> [!NOTE]  
>  このストアドプロシージャは、データベースメールのキューのみを停止します。 このストアドプロシージャは、データベース[!INCLUDE[ssSB](../../includes/sssb-md.md)]でのメッセージ配信を非アクティブ化しません。 このストアドプロシージャでは、データベースメール拡張ストアドプロシージャを無効にして、セキュリティでセキュリティを低下させることはできません。 拡張ストアドプロシージャを無効にするには、 **sp_configure**システムストアドプロシージャの[データベースメール XPs オプション](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>例  
 次の例では、 **msdb**データベースのデータベースメールを停止します。 この例では、データベースメールが有効になっていることを前提としています。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
