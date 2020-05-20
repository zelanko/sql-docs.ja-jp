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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8a29933568cec147dc27ff7c9b5f026d62856e5b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807766"
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
`[ @parameter_name = ] 'parameter_name'`取得する構成設定の名前。 指定した場合、構成設定の値が** \@ parameter_value**出力パラメーターに返されます。 ** \@ Parameter_name**が指定されていない場合、このストアドプロシージャは、インスタンス内のすべてのデータベースメール構成設定を含む結果セットを返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ** \@ Parameter_name**が指定されていない場合、は次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**paramname**|**nvarchar(256)**|構成パラメーターの名前。|  
|**paramvalue**|**nvarchar(256)**|構成パラメーターの値|  
|**記述**|**nvarchar(256)**|構成パラメーターの説明|  
  
## <a name="remarks"></a>Remarks  
 ストアドプロシージャ**sysmail_help_configure_sp**には、インスタンスの現在のデータベースメール構成設定が一覧表示されます。  
  
 ** \@ Parameter_name**が指定されていても、 ** \@ parameter_value**の出力パラメーターが指定されていない場合、このストアドプロシージャは出力を生成しません。  
  
 ストアドプロシージャ**sysmail_help_configure_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3部構成の名前を使用してプロシージャを呼び出す必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>使用例  
 次の例では、インスタンスのデータベースメール構成設定を一覧表示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
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
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
