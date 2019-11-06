---
title: sysmail_help_configure_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: e4b0d4fb1f3c233ad8e7eedf91802da35fbbb1d2
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304748"
---
# <a name="sysmail_help_configure_sp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールの構成設定を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@parameter_name** =] **'***parameter_name***'**  
 取得する構成設定の名前。 このオプションを指定すると、構成設定の値が **@no__t 1parameter_value**出力パラメーターに返されます。 **@No__t**が指定されていない場合、このストアドプロシージャは、インスタンス内のすべてのデータベースメール構成設定を含む結果セットを返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 **@No__t**が指定されていない場合、は次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**paramname**|**nvarchar (256)**|構成パラメーターの名前。|  
|**paramvalue**|**nvarchar (256)**|構成パラメーターの値|  
|**description**|**nvarchar (256)**|構成パラメーターの説明|  
  
## <a name="remarks"></a>コメント  
 ストアドプロシージャ**sysmail_help_configure_sp**には、インスタンスの現在のデータベースメール構成設定が一覧表示されます。  
  
 **@No__t**が指定されているが **@no__t 3parameter_value**に出力パラメーターが指定されていない場合、このストアドプロシージャは出力を生成しません。  
  
 ストアドプロシージャ**sysmail_help_configure_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3部構成の名前を使用してプロシージャを呼び出す必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベースメール構成設定を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 次に結果セットを示します。行の長さは編集されています。  
  
```  
paramname                       paramvalue      description  
------------------------------- --------------- -----------------------------------------------------------------------------  
AccountRetryAttempts            1               Number of retry attempts for a mail server  
AccountRetryDelay               5000            Delay between each retry attempt to mail server  
DatabaseMailExeMinimumLifeTime  600             Minimum process lifetime in seconds  
DefaultAttachmentEncoding       MIME            Default attachment encoding  
LoggingLevel                    2               Database Mail logging level: normal - 1, extended - 2 (default), verbose - 3  
MaxFileSize                     1000000         Default maximum file size  
ProhibitedExtensions            exe,dll,vbs,js  Extensions not allowed in outgoing mails  
  
```  
  
## <a name="see-also"></a>関連項目  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [ストアドプロシージャ&#40;のデータベースメール transact-sql&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
