---
title: "sp_helplogins (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75e0521889f38db02bfdc9eabd3332d3fa76afb9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各データベース内の、ログインおよびログインに関連するユーザーに関する情報を提供します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@LoginNamePattern =** ] **'***ログイン***'**  
 ログイン名を指定します。 *ログイン*は**sysname**、既定値は NULL です。 *ログイン*指定されている場合に存在する必要があります。 場合*ログイン*が指定されていないすべてのログインに関する情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 最初のレポートには、次の表に示すとおり、指定した各ログインに関する情報が含まれます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|ログイン名。|  
|**SID**|**varbinary (85)**|ログイン セキュリティ識別子 (SID)。|  
|**DefDBName**|**sysname**|既定のデータベースを**LoginName**のインスタンスに接続するときは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**DefLangName**|**sysname**|既定の言語で使用される**LoginName**です。|  
|**Auser**|**char (5)**|Yes = **LoginName**データベースに関連付けられているユーザー名を持っています。<br /><br /> いいえ = **LoginName**関連付けられているユーザー名がありません。|  
|**ARemote**|**char (7)**|Yes = **LoginName**が関連付けられているリモート ログインします。<br /><br /> いいえ = **LoginName**関連付けられたログインはありません。|  
  
 2 番目のレポートには、次の表に示すとおり、各ログインにマップされているユーザーに関する情報、およびログインのロール メンバーシップが含まれています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|ログイン名。|  
|**DBName**|**sysname**|既定のデータベースを**LoginName**のインスタンスに接続するときは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**UserName**|**sysname**|ユーザー アカウントは、 **LoginName**でマップ**DBName**、およびロールを**LoginName**でのメンバーである**DBName**です。|  
|**UserOrAlias**|**char (8)**|MemberOf = **UserName**ロールします。<br /><br /> ユーザー = **UserName**ユーザー アカウントです。|  
  
## <a name="remarks"></a>解説  
 ログインを削除する前に使用して**sp_helplogins**ログインにマップされているユーザー アカウントを識別します。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **securityadmin**固定サーバー ロール。  
  
 特定のログインにマップされたすべてのユーザー アカウントを識別する**sp_helplogins**サーバー内のすべてのデータベースを確認する必要があります。 これを行うには、サーバーの各データベースに対して、少なくとも次のいずれか 1 つの条件を満たしている必要があります。  
  
-   実行しているユーザー **sp_helplogins**データベースにアクセスする権限を持っています。  
  
-   **ゲスト**ユーザー アカウントが、データベースで有効にします。  
  
 場合**sp_helplogins** 、データベースにアクセスできない**sp_helplogins**してエラー メッセージ 15622 が表示と同じ情報が返されます。  
  
## <a name="examples"></a>使用例  
 次の例は、ログイン情報をレポート`John`です。  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
