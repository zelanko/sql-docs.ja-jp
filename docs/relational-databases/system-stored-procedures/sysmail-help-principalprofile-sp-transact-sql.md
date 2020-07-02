---
title: sysmail_help_principalprofile_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_principalprofile_sp_TSQL
- sysmail_help_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_principalprofile_sp
ms.assetid: 0cfd6464-09c7-4f03-9d25-58001c096a9e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 534e695a9648ef1e183660f15f6f76d882c52bd9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752727"
---
# <a name="sysmail_help_principalprofile_sp-transact-sql"></a>sysmail_help_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  データベース メール プロファイルと msdb データベース プリンシパルとの関連付けに関する情報を表示します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_principalprofile_sp [ {   [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ]  
    [ [ , ] {   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ]  
```  
  
## <a name="arguments"></a>引数  
`[ @principal_id = ] principal_id`関連付けを表示する**msdb**データベースのデータベースユーザーまたはロールの ID を示します。 *principal_id*は**int**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定できます。  
  
`[ @principal_name = ] 'principal_name'`関連付けを表示する**msdb**データベースのデータベースユーザーまたはロールの名前を指定します。 *principal_name*は**sysname**,、既定値は NULL です。 *Principal_id*または*principal_name*のいずれかを指定できます。  
  
`[ @profile_id = ] profile_id`関連付けを一覧表示するプロファイルの ID を示します。 *profile_id*は**int**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定できます。  
  
`[ @profile_name = ] 'profile_name'`関連付けを一覧表示するプロファイルの名前を指定します。 *profile_name*は**sysname**,、既定値は NULL です。 *Profile_id*または*profile_name*のいずれかを指定できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 返される結果セットには、次の表に示す列が含まれています。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**principal_id**|**int**|データベース ユーザーの ID|  
|**principal_name**|**sysname**|データベースユーザーの名前。|  
|**profile_id**|**int**|データベースメールプロファイルの ID 番号。|  
|**profile_name**|**sysname**|データベースメールプロファイルの名前。|  
|**is_default**|**bit**|このプロファイルがユーザーの既定のプロファイルかどうかを示すフラグ|  
  
## <a name="remarks"></a>Remarks  
 パラメーターを指定せずに**sysmail_help_principalprofile_sp**が呼び出された場合、返される結果セットには、のインスタンス内のすべての関連付けが一覧表示され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 それ以外の場合、結果セットには、指定されたパラメーターに一致するアソシエーションの情報が含まれます。 たとえば、プロファイル名が指定されている場合、このプロシージャはプロファイルのすべての関連付けを一覧表示します。  
  
 **sysmail_help_principalprofile_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-information-for-a-specific-association"></a>A. 特定の関連付けに関する情報を一覧表示する  
 次の例では、`AdventureWorks Administrator` データベース内の `ApplicationLogin` プロファイルと `msdb` プリンシパルのすべての関連付けについて、その情報を表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp  
    @principal_name = 'danw',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 次に示すのは、行の長さに対して再フォーマットされる、結果セットのサンプルです。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
5            danw               9           AdventureWorks Administrator   1  
```  
  
### <a name="b-listing-information-for-all-associations"></a>B: すべての関連付けに関する情報を一覧表示する  
 次の例では、インスタンス内のすべての関連付けについての情報を表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_principalprofile_sp ;  
```  
  
 次に示すのは、行の長さに対して再フォーマットされる、結果セットのサンプルです。  
  
```  
principal_id principal_name     profile_id  profile_name                   is_default  
------------ ------------------ ----------- ------------------------------ ----------  
6            terrid             3           Product Update Profile         1  
5            danw               9           AdventureWorks Administrator   1  
```  
  
## <a name="see-also"></a>関連項目  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースメール](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
