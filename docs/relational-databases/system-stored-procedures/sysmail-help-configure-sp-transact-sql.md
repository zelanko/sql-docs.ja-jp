---
title: sysmail_help_configure_sp (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1ef80206f9ff82cf1ab2917e90f61432be15c190
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838430"
---
# <a name="sysmailhelpconfiguresp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールの構成設定を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [**@parameter_name** =] **'***parameter_name***'**  
 取得する構成設定の名前を指定します。 指定した場合、構成設定の値が返されます、 **@parameter_value**出力パラメーター。 ない場合**@parameter_name**を指定すると、このストアド プロシージャは、すべてのインスタンスでデータベース メール構成設定を含む結果セットを返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ない場合**@parameter_name**が指定された場合、次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**paramname**|**nvarchar (256)**|構成パラメーターの名前|  
|**paramvalue**|**nvarchar (256)**|構成パラメーターの値|  
|**description**|**nvarchar (256)**|構成パラメーターの説明|  
  
## <a name="remarks"></a>コメント  
 ストアド プロシージャ**sysmail_help_configure_sp**インスタンスの現在のデータベース メール構成設定を一覧表示されます。  
  
 ときに、 **@parameter_name**を指定の出力パラメーターが指定されていないが、 **@parameter_value**、このストアド プロシージャが出力を生成しません。  
  
 ストアド プロシージャ**sysmail_help_configure_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合は、3 つの部分の名前を持つプロシージャを起動する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例ではデータベース メールの構成設定を一覧表示、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
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
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
