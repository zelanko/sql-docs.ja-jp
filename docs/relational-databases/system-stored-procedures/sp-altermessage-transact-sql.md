---
title: sp_altermessage (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_altermessage_TSQL
- sp_altermessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_altermessage
ms.assetid: 1b28f280-8ef9-48e9-bd99-ec14d79abaca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 514b713b8970ecf38536da7e00b791dcef8a059a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761970"
---
# <a name="spaltermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのシステム メッセージまたはユーザー定義の状態の変更、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 使用してユーザー定義メッセージを表示することができます、 **sys.messages**カタログ ビューです。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>引数  
 [**@message_id =** ] *message_number*  
 変更するメッセージのエラー番号は、 **sys.messages**します。 *message_number*は**int**で既定値はありません。  
  
 [ **@parameter =** ] **'***write_to_log*'  
 併用**@parameter_value**に書き込まれるメッセージがあることを示す、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログ。 *write_to_log*は**sysname**で既定値はありません。 *write_to_log* WITH_LOG または NULL に設定する必要があります。 場合*write_to_log* WITH_LOG または null の場合、しの値に設定されている**@parameter_value**は**true**メッセージは、Windows アプリケーション ログに書き込まれます。 場合*write_to_log* WITH_LOG または NULL との値に設定されている**@parameter_value**は**false**メッセージは、Windows アプリケーション ログには常に書き込まれませんが、可能性がありますエラーの発生状況によっては書き込まれます。 場合*write_to_log*が指定されている値**@parameter_value**も指定する必要があります。  
  
> [!NOTE]  
>  Windows のアプリケーション ログにメッセージを書き込む場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のエラー ログ ファイルにも同じ内容が書き込まれます。  
  
 [ **@parameter_value =** ]**'***value*'  
 併用**@parameter**にへの書き込みエラーがあることを示す、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログ。 *値*は**varchar (5)** 既定値はありません。 場合**true**エラーが常に Windows アプリケーション ログに書き込まれます。 場合**false**エラーは、Windows アプリケーション ログには常に書き込まれませんが、エラーの発生状況によっては書き込まれる可能性があります。 場合*値*が指定されている*write_to_log*の**@parameter**も指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 効果**sp_altermessage**に WITH_LOG オプションは、点を除いて、RAISERROR WITH LOG パラメーターと同じ**sp_altermessage**既存のメッセージのログ記録の動作を変更します。 メッセージを WITH_LOG に変更すると、ユーザーがエラーをどのような方法で起こしたかとは無関係に、メッセージは常に Windows のアプリケーション ログに書き込まれます。 WITH_LOG オプションなしで RAISERROR を実行しても、Windows のアプリケーション ログにエラーが書き込まれます。  
  
 システム メッセージを使用して変更できる**sp_altermessage**します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **serveradmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、既存のメッセージをさせます`55001`を Windows アプリケーション ログに記録します。  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
