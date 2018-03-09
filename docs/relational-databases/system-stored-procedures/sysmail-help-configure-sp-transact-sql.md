---
title: "sysmail_help_configure_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13f768cd5e1cbbbcfa3f5b74d7ae52d2e9f357e1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
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
 [ **@parameter_name**  =] **'***parameter_name***'**  
 取得する構成設定の名前を指定します。 指定した場合、構成設定の値は、  **@parameter_value** 出力パラメーターです。 ない場合 **@parameter_name** を指定すると、このストアド プロシージャは、すべてのインスタンスでデータベース メール構成設定を含む結果セットを返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 ない場合 **@parameter_name** を指定すると、次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|**paramname**|**nvarchar (256)**|構成パラメーターの名前|  
|**paramvalue**|**nvarchar (256)**|構成パラメーターの値|  
|**説明**|**nvarchar (256)**|構成パラメーターの説明|  
  
## <a name="remarks"></a>解説  
 ストアド プロシージャ**sysmail_help_configure_sp**インスタンスの現在のデータベース メールの構成設定を一覧表示します。  
  
 ときに、  **@parameter_name** が指定されているの出力パラメーターが指定されていませんが、  **@parameter_value** 、このストアド プロシージャの出力はありません。  
  
 ストアド プロシージャ**sysmail_help_configure_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合、3 部構成の名前を持つプロシージャを呼び出す必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース メールの構成設定を一覧表示、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
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
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
