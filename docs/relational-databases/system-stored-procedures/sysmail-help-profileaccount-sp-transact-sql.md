---
title: "sysmail_help_profileaccount_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- sysmail_help_profileaccount_sp_TSQL
- sysmail_help_profileaccount_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profileaccount_sp
ms.assetid: 3ea68271-0a6b-4d77-991c-4757f48f747a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dfe0115ca0e641ca0b6397cd624d093f7d94acff
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailhelpprofileaccountsp-transact-sql"></a>sysmail_help_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上のデータベース メール プロファイルに関連付けられているアカウントを一覧表示します。  
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_profileaccount_sp  
   {   [ @profile_id = ] profile_id   
      | [ @profile_name = ] 'profile_name' }  
   [ , {   [ @account_id = ] account_id  
         | [ @account_name = ] 'account_name' } ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_id** = ] *profile_id*  
 表示するプロファイルのプロファイル ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@profile_name** = ] **'***profile_name***'**  
 表示するプロファイルのプロファイル名を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@account_id** = ] *account_id*  
 表示するアカウント ID を指定します。 *account_id*は**int**、既定値は NULL です。 ときに*account_id*と*account_name*が両方の NULL の場合、プロファイル内のすべてのアカウントを一覧表示します。  
  
 [  **@account_name**  =] **'***account_name***'**  
 表示するアカウント名を指定します。 *account_name*は**sysname**、既定値は NULL です。 ときに*account_id*と*account_name*が両方の NULL の場合、プロファイル内のすべてのアカウントを一覧表示します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の列を含む結果セットが返されます。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|**profile_id**|**int**|プロファイルのプロファイル ID。|  
|**profile_name**|**sysname**|プロファイルの名前。|  
|**account_id**|**int**|アカウントのアカウント ID。|  
|**account_name**|**sysname**|アカウントの名前。|  
|**sequence_number**|**int**|プロファイ内のアカウントのシーケンス番号。|  
  
## <a name="remarks"></a>解説  
 ない場合*profile_id*または*profile_name*を指定すると、このストアド プロシージャは、インスタンス内のプロファイルすべてについての情報を返します。  
  
 ストアド プロシージャ**sysmail_help_profileaccount_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.名前で、特定のプロファイルのアカウントを一覧表示します。**  
  
 次の例ではの情報を一覧表示、`AdventureWorks Administrator`プロファイル名を指定してプロファイルできます。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
   @profile_name = 'AdventureWorks Administrator';  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **B.アカウントを特定してプロファイルのプロファイル ID を一覧表示**  
  
 次の例では、`AdventureWorks Administrator` プロファイルの情報を、プロファイル ID を指定して一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
    @profile_id = 131 ;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **C.すべてのプロファイルのアカウントを一覧表示します。**  
  
 次の例では、インスタンスのすべてのプロファイルのアカウントを一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
106         AdventureWorks Operator      210         Operator-MainServer  1  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
