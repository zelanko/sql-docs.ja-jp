---
title: "LOGINPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BadPasswordCount_TSQL
- BadPasswordTime_TSQL
- IsLockedIsMustChange
- PasswordLastSetTime
- LOGINPROPERTY_TSQL
- LockoutTime
- BadPasswordCount
- PasswordHash
- HistoryLengthIsExpired
- LockoutTime_TSQL
- PasswordHash_TSQL
- HistoryLengthIsExpired_TSQL
- PasswordLastSetTime_TSQL
- BadPasswordTime
- IsLockedIsMustChange_TSQL
- LOGINPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- default database
- LOGINPROPERTY function
ms.assetid: b34df777-79b0-49a5-88db-b99998479a5d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c5aa0f30058bdd2e6fc13121e4a849d4496b667d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loginproperty-transact-sql"></a>LOGINPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログインのポリシー設定に関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
LOGINPROPERTY ( 'login_name' , 'property_name' )  
```  
  
## <a name="arguments"></a>引数  
 *login_name*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのログイン プロパティの状態が返されます。  
  
 *プロパティ名*  
 ログインに返されるプロパティ情報を含む式を指定します。 *propertyname*値は次のいずれかになります。  
  
|値|Description|  
|-----------|-----------------|  
|**BadPasswordCount**|正しくないパスワードで連続してログインが試行された回数を返します。|  
|**BadPasswordTime**|正しくないパスワードで最後にログインが試行された時刻を返します。|  
|**DaysUntilExpiration**|パスワードの有効期限が切れるまでの日数を返します。|  
|**DefaultDatabase**|返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータに格納されているログインの既定のデータベースまたは**マスター**データベースが指定されていない場合。 場合は NULL を返しますではない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー (たとえば、Windows 認証) をプロビジョニングします。|  
|**DefaultLanguage**|メタデータに格納されているログインの既定の言語を返します。 場合は NULL を返しますではない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]提供されるユーザー、たとえば、Windows が認証されたユーザー。|  
|**HistoryLength**|パスワード ポリシーの適用メカニズムを使用して、追跡されたログインのパスワードの数を返します。 パスワード ポリシーが適用されていない場合は 0 です。 パスワード ポリシーの適用は 1 から再開されます。|  
|**IsExpired**|ログインの期限が切れているかどうかを示します。|  
|**IsLocked**|ログインがロックされているかどうかを示します。|  
|**IsMustChange**|次回の接続時にログイン パスワードを変更する必要があるかどうかを示します。|  
|**LockoutTime**|日付を返しますと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]許可されている失敗したログイン試行回数を超えたためにログインがロックアウトされました。|  
|**PasswordHash**|パスワードのハッシュを返します。|  
|**PasswordLastSetTime**|現在のパスワードが設定された日付を返します。|  
|**PasswordHashAlgorithm**|パスワードのハッシュに使用されるアルゴリズムを返します。|  
  
## <a name="returns"></a>返します。  
 データ型は、要求する値によって異なります。  
  
 **IsLocked**、 **IsExpired**、および**IsMustChange**型**int**です。  
  
-   ログインが指定した状態の場合は 1 です。  
  
-   ログインが指定した状態でない場合は 0 です。  
  
 **BadPasswordCount**と**HistoryLength**型**int**です。  
  
 **BadPasswordTime**、 **LockoutTime**、 **PasswordLastSetTime**型**datetime**です。  
  
 **PasswordHash**の種類は**varbinary**です。  
  
 ログインが有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインでない場合は NULL です。  
  
 **DaysUntilExpiration**の種類は**int**です。  
  
-   ログインの有効期限が切れているか、照会した当日に有効期限が切れる場合は 0 です。  
  
-   Windows のローカル セキュリティ ポリシーでパスワードを無期限にしている場合は -1 です。  
  
-   ログインに対して CHECK_POLICY または CHECK_EXPIRATION が OFF であるか、オペレーティング システムがパスワード ポリシーをサポートしていない場合は NULL です。  
  
 **PasswordHashAlgorithm**は int 型です  
  
-   SQL7.0 ハッシュの場合は 0  
  
-   sha-1 ハッシュの場合は 1  
  
-   SHA-2 ハッシュの場合は 2  
  
-   ログインが有効な SQL Server ログインでない場合は NULL  
  
## <a name="remarks"></a>解説  
 この組み込み関数は、パスワードについての情報のポリシー設定を返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 プロパティの名前はプロパティの名前など、大文字と小文字が区別されない**BadPasswordCount**と**badpasswordcount**は同等です。 値、 **PasswordHash、PasswordHashAlgorithm**、および**PasswordLastSetTime**のプロパティはのすべてのサポートされている構成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が他のプロパティはのみ使用可能な場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で実行されて[!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]CHECK_POLICY と CHECK_EXPIRATION の両方が有効になっているとします。 詳細については、「 [Password Policy](../../relational-databases/security/password-policy.md)」をご参照ください。  
  
## <a name="permissions"></a>Permissions  
 ログインに対する VIEW 権限が必要です。 パスワードのハッシュを要求する場合、CONTROL SERVER 権限も必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-checking-whether-a-login-must-change-its-password"></a>A. ログインがパスワードを変更する必要があるかどうかを確認する  
 次の例をチェックするかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`John3`、次回のインスタンスに接続するパスワードを変更する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
SELECT LOGINPROPERTY('John3', 'IsMustChange');  
GO  
```  
  
### <a name="b-checking-whether-a-login-is-locked-out"></a>B. ログインがロックアウトされているかどうかを確認する  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン `John3` がロックされているかどうかを確認します。  
  
```  
SELECT LOGINPROPERTY('John3', 'IsLocked');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
  
