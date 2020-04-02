---
title: sp_addmessage (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
author: stevestein
ms.author: sstein
ms.openlocfilehash: d040fa0ccfe9b962f8847db0a841b95a534326fa
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531032"
---
# <a name="sp_addmessage-transact-sql"></a>sp_addmessage (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  のインスタンスに新しいユーザー定義エラー メッセージを格納します[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。 **sp_addmessage**を使用して保存されたメッセージは **、sys.messages**カタログ ビューを使用して表示できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @msgnum = ] msg_id`メッセージの ID です。 *msg_id*は**デフォルト**の NULL です。 ユーザー定義のエラー メッセージの*msg_id*は、50,001 から 2,147,483,647 の整数にすることができます。 *msg_id*と*言語*の組み合わせは一意である必要があります。指定した言語の ID が既に存在する場合は、エラーが返されます。  
  
`[ @severity = ]severity`エラーの重大度レベルです。 *重大度*は**小さく**、デフォルトは NULL です。 有効なレベルは 1 ～ 25 です。 重大度レベルの詳細については、「 [データベース エンジン エラーの重大度](../../relational-databases/errors-events/database-engine-error-severities.md)」を参照してください。  
  
`[ @msgtext = ] 'msg'`エラー メッセージのテキストです。 *msg*は**nvarchar(255) で**、デフォルトは NULL です。  
  
`[ @lang = ] 'language'`このメッセージの言語です。 *言語*は、デフォルトは NULL の**sysname**です。 複数の言語を同じサーバーにインストールできるため、*言語*は各メッセージが書き込まれる言語を指定します。 *言語*を省略すると、その言語がセッションのデフォルト言語になります。  
  
`[ @with_log = ] { 'TRUE' | 'FALSE' }`メッセージが発生したときに Windows アプリケーション ログに書き込まれるかどうかを指定します。 with_logは、デフォルトの FALSE を持つ**varchar(5) です**。 ** \@** TRUE の場合、エラーは常に Windows アプリケーション ログに書き込まれます。 FALSE の場合、常に Windows のアプリケーション ログに書き込まれるわけではありませんが、エラーの発生状況によっては書き込まれることもあります。 このオプションを使用できるのは **、sysadmin**サーバー ロールのメンバだけです。  
  
> [!NOTE]  
>  Windows のアプリケーション ログにメッセージを書き込む場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のエラー ログ ファイルにも同じ内容が書き込まれます。  
  
`[ @replace = ] 'replace'`文字列*replace*として指定した場合、既存のエラー メッセージは新しいメッセージ テキストと重大度レベルで上書きされます。 *置換*は**varchar(7) で**、デフォルトは NULL です。 このオプションは *、msg_id*が既に存在する場合に指定する必要があります。 英語 (U.S. ) のメッセージを置き換える場合は、同じ*msg_id*を持つ他のすべての言語のすべてのメッセージに対して、重大度レベルが置き換えられます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 None  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の英語以外のバージョンで、別の言語を使用してメッセージを追加するには、あらかじめ英語版のメッセージが存在している必要があります。 2 つのバージョンのメッセージの重大度は同じであることが必要です。  
  
 パラメーターを含むメッセージをローカライズする場合は、元のメッセージのパラメーターに対応するパラメーター番号を使用します。 各パラメーター番号の後に感嘆符 (!) を挿入します。  
  
|元のメッセージ|ローカライズされたメッセージ|  
|----------------------|-----------------------|  
|'元のメッセージ パラメータ 1: %s、<br /><br /> param 2: %d'|'ローカライズされたメッセージ パラメータ 1: %1!,<br /><br /> パラム 2: %2!|  
  
 言語の構文に相違があるため、ローカライズされたメッセージのパラメーター番号は、元のメッセージと同じ順に出現しないことがあります。  
  
## <a name="permissions"></a>アクセス許可  
**sysadmin**または**サーバー管理者**の固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-defining-a-custom-message"></a>A. カスタム メッセージの定義  
 次の例では、カスタム メッセージを**sys.messages**に追加します。  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. 2 種類の言語のメッセージを追加する  
 次の例では、まず英語のメッセージを追加し、次に同じメッセージのフランス語版を追加します。`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. パラメーターの順序を変更する  
 次の例では、まず英語のメッセージを追加し、次にパラメーターの順序を変えてローカライズされたメッセージを追加します。  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>参照  
 [トランザクション SQL&#41;&#40;エラー](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [&#40;のトランザクション SQL&#41;をsp_altermessageします。](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
