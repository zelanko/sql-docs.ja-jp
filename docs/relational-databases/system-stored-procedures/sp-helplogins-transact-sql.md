---
title: sp_helplogins (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b043b71ca3f0349ce8ed7ac7accf136f4b7eff60
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595230"
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
 [ **@LoginNamePattern =** ] **'***login***'**  
 ログイン名を指定します。 *login* のデータ型は **sysname** で、既定値は NULL です。 *ログイン*指定されている場合に存在する必要があります。 場合*ログイン*が指定されていないすべてのログインに関する情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 最初のレポートには、次の表に示すとおり、指定した各ログインに関する情報が含まれます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|ログイン名。|  
|**SID**|**varbinary(85)**|ログイン セキュリティ識別子 (SID)。|  
|**DefDBName**|**sysname**|既定のデータベースを**LoginName**のインスタンスに接続するときは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**DefLangName**|**sysname**|既定の言語で使用される**LoginName**します。|  
|**Auser**|**char (5)**|Yes = **LoginName**データベースに関連付けられているユーザー名を持っています。<br /><br /> いいえ = **LoginName**関連付けられているユーザー名がありません。|  
|**ARemote**|**char (7)**|Yes = **LoginName**が関連付けられたリモート ログインします。<br /><br /> いいえ = **LoginName**関連付けられたログインはありません。|  
  
 2 番目のレポートには、次の表に示すとおり、各ログインにマップされているユーザーに関する情報、およびログインのロール メンバーシップが含まれています。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|ログイン名。|  
|**データベース名**|**sysname**|既定のデータベースを**LoginName**のインスタンスに接続するときは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**UserName**|**sysname**|ユーザー アカウントは、 **LoginName**でマップが**DBName**、およびロールを**LoginName**でのメンバーである**DBName**します。|  
|**UserOrAlias**|**char (8)**|MemberOf = **UserName**は、ロールです。<br /><br /> ユーザー = **UserName**はユーザー アカウントです。|  
  
## <a name="remarks"></a>Remarks  
 ログインを削除する前に、使用して**sp_helplogins**ログインにマップされているユーザー アカウントを特定します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **securityadmin**固定サーバー ロール。  
  
 指定されたログインにマップされているすべてのユーザー アカウントを識別するために**sp_helplogins**サーバー内のすべてのデータベースを確認する必要があります。 これを行うには、サーバーの各データベースに対して、少なくとも次のいずれか 1 つの条件を満たしている必要があります。  
  
-   実行しているユーザー **sp_helplogins**データベースへのアクセス権があります。  
  
-   **ゲスト**ユーザー アカウントが、データベースで有効にします。  
  
 場合**sp_helplogins** 、データベースにアクセスできない**sp_helplogins**およびエラー メッセージ 15622 が表示できる限り多くの情報を返します。  
  
## <a name="examples"></a>使用例  
 次の例は、ログイン情報を報告`John`します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
