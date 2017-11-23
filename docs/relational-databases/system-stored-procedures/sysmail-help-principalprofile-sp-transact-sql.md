---
title: "sysmail_help_principalprofile_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 322984b88e879adb952a1168b17178b8ffe20ae2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpprincipalprofilesp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール プロファイルと msdb データベース プリンシパルとの関連付けに関する情報を表示します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@principal_id=** ] *principal_id*  
 データベース ユーザーまたはロールの id を指定します、 **msdb**データベースの関連付けを表示します。 *principal_id*は**int**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定することがあります。  
  
 [  **@principal_name=** ] **'***principal_name***'**  
 データベース ユーザーまたはロールの名前を指定します、 **msdb**データベースの関連付けを表示します。 *principal_name*は**sysname**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定することがあります。  
  
 [  **@profile_id=** ] *profile_id*  
 関連付けを表示するプロファイルの ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定することがあります。  
  
 [  **@profile_name=** ] **'***profile_name***'**  
 関連付けを表示するプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 返される結果セットには、次の表に示す列が含まれています。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|**principal_id**|**int**|データベース ユーザーの ID|  
|**principal_name**|**sysname**|データベース ユーザーの名前です。|  
|**profile_id**|**int**|データベース メール プロファイルの ID 番号|  
|**profile_name**|**sysname**|データベース メール プロファイルの名前|  
|**is_default**|**bit**|このプロファイルがユーザーの既定のプロファイルかどうかを示すフラグ|  
  
## <a name="remarks"></a>解説  
 場合**sysmail_help_principalprofile_sp**が呼び出されるパラメーターを指定せず、返される結果セットの一覧のすべてのインスタンス内の関連付けの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 パラメーターを指定した場合は、そのパラメーターに一致する関連付けについての情報が示されます。 たとえば、プロファイル名を指定した場合は、そのプロファイルのすべての関連付けが表示されます。  
  
 **sysmail_help_principalprofile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. 特定の関連付けについての情報を表示する  
 次の例では、`AdventureWorks Administrator` データベース内の `ApplicationLogin` プロファイルと `msdb` プリンシパルのすべての関連付けについて、その情報を表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 次に結果セットを示します。行の長さは調整されています。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>B. すべての関連付けについての情報を表示する  
 次の例では、インスタンス内のすべての関連付けについての情報を表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 次に結果セットを示します。行の長さは調整されています。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
