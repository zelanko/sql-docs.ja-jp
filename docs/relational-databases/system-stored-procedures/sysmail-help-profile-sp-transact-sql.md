---
title: sysmail_help_profile_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sysmail_help_profile_sp_TSQL
- sysmail_help_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profile_sp
ms.assetid: d7169a8e-92b1-49eb-9124-3b2f69755ddb
caps.latest.revision: 41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ba57437de19addff8e5e8040add167d546f1fa0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmailhelpprofilesp-transact-sql"></a>sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上のメール プロファイルに関する情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_id** = ] *profile_id*  
 情報を返すプロファイル ID を指定します。 *profile_id*は**int**、既定値は NULL です。  
  
 [ **@profile_name** =] **'***profile_name***'**  
 情報を返すプロファイル名を指定します。 *profile_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の列を含む結果セットが返されます。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|**profile_id**|**int**|プロファイルのプロファイル ID|  
|**name**|**sysname**|プロファイルのプロファイル名|  
|**説明**|**nvarchar (256)**|プロファイルの説明|  
  
## <a name="remarks"></a>解説  
 プロファイル名またはプロファイル id を指定すると、 **sysmail_help_profile_sp**そのプロファイルに関する情報を返します。 それ以外の場合、 **sysmail_help_profile_sp**のすべてのプロファイルに関する情報を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 ストアド プロシージャ**sysmail_help_profile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.すべてのプロファイルを一覧表示します。**  
  
 次の例では、インスタンス内のすべてのプロファイルを一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 次に、サンプルの結果セットの行の長さを再フォーマットを示します。  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B.特定のプロファイルを一覧表示します。**  
  
 次の例では、プロファイル `AdventureWorks Administrator` に関する情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 次に、サンプルの結果セットの行の長さを再フォーマットを示します。  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
