---
title: sp_change_users_login (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 12/13/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_change_users_login
- sp_change_users_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_users_login
ms.assetid: 1554b39f-274b-4ef8-898e-9e246b474333
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0594066f044288757e5e31f8e078fabb4c2f3775
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68120227"
---
# <a name="sp_change_users_login-transact-sql"></a>sp_change_users_login (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースユーザーをログインにマップします。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[ALTER USER](../../t-sql/statements/alter-user-transact-sql.md)を使用してください。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_users_login [ @Action = ] 'action'   
    [ , [ @UserNamePattern = ] 'user' ]   
    [ , [ @LoginName = ] 'login' ]   
    [ , [ @Password = ] 'password' ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @Action= ]'*action*'  
 プロシージャにより実行されるアクションの説明です。 *action*は**varchar (10)** です。 *アクション*には、次のいずれかの値を指定できます。  
  
|値|[説明]|  
|-----------|-----------------|  
|**Auto_Fix**|現在のデータベース内の sys.database_principals システム カタログ ビューにあるユーザー エントリを、同じ名前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにリンクします。 同じ名前のログインが存在しない場合は、新しく作成されます。 **Auto_Fix**ステートメントの結果を調べて、正しいリンクが実際に作成されていることを確認します。 セキュリティを重視する状況では**Auto_Fix**を使用しないようにしてください。<br /><br /> **Auto_Fix**を使用する場合は、ログインがまだ存在しない場合は*ユーザー*と*パスワード*を指定する必要があります。そうでない場合は、*ユーザー*を指定する必要がありますが、*パスワード*は無視されます。 *ログイン*は NULL にする必要があります。 *ユーザー*は、現在のデータベースの有効なユーザーである必要があります。 ログインに別のユーザーをマップすることはできません。|  
|**Report**|現在のデータベース内で、どのログインにもリンクされていないユーザーと、対応するセキュリティ識別子 (SID) を一覧表示します。 *ユーザー*、*ログイン*、および*パスワード*は NULL であるか、指定されていません。<br /><br /> システムテーブルを使用するクエリでレポートオプションを置き換えるには、 **server_prinicpals**内のエントリを、 **database_principals**のエントリと比較します。|  
|**Update_One**|現在のデータベース内の指定された*ユーザー*を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既存の*ログイン*にリンクします。 *ユーザー*と*ログイン*を指定する必要があります。 *パスワード*は NULL であるか、指定されていません。|  
  
 [ @UserNamePattern= ]'*user*'  
 現在のデータベース内のユーザーの名前を指定します。 *user*の部分は**sysname**で、既定値は NULL です。  
  
 [ @LoginName= ]'*login*'  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインの名前を指定します。 *login*は**sysname**,、既定値は NULL です。  
  
 [ @Password= ]'*パスワード*'  
 Auto_Fix を指定して作成さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れた新しいログインに割り当て**** られたパスワードを指定します。 一致するログインが既に存在する場合、ユーザーとログインはマップされ、*パスワード*は無視されます。 一致するログインが存在しない場合、sp_change_users_login によっ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]て新しいログインが作成され、*パスワード*が新しいログインのパスワードとして割り当てられます。 *パスワード*は**sysname**であり、NULL にすることはできません。  
  
> **重要!!** 常に[強力なパスワード](../../relational-databases/security/strong-passwords.md)を使用してください。
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|UserName|**sysname**|データベースユーザー名。|  
|UserSID|**varbinary (85)**|ユーザーのセキュリティ識別子。|  
  
## <a name="remarks"></a>解説  
 sp_change_users_login は、現在のデータベースのデータベース ユーザーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインとリンクする場合に使用します。 ユーザーのログインが既に変更されている場合は、sp_change_users_login を使用してユーザーを新しいログインにリンクすれば、ユーザーの権限が失われることはありません。 新しい*ログイン*を sa にすることはできません。また、*ユーザー*を dbo、guest、または INFORMATION_SCHEMA ユーザーにすることはできません。  
  
 sp_change_users_login は、データベース ユーザーを Windows レベルのプリンシパル、証明書、または非対称キーにマップする場合は使用できません。  
  
 sp_change_users_login は、Windows プリンシパルから作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインや、CREATE USER WITHOUT LOGIN を使用して作成されたユーザーでは使用できません。  
  
 ユーザー定義のトランザクション内では、sp_change_users_login は実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 db_owner 固定データベース ロールのメンバーシップが必要です。 **Auto_Fix**オプションを指定できるのは、sysadmin 固定サーバーロールのメンバーだけです。  
  
## <a name="examples"></a>例  
  
### <a name="a-showing-a-report-of-the-current-user-to-login-mappings"></a>A. 現在のユーザーとログインの対応関係を示すレポートを表示する  
 次の例では、現在のデータベース内のユーザーと各ユーザーのセキュリティ識別子 (SID) を示すレポートを作成します。  
  
```  
EXEC sp_change_users_login 'Report';  
```  
  
### <a name="b-mapping-a-database-user-to-a-new-sql-server-login"></a>B. 新しい SQL Server ログインへのデータベースユーザーのマッピング  
 次の例では、データベースユーザーが新しい[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインに関連付けられています。 最初に`MB-Sales`別のログインにマップされるデータベースユーザーは、ログイン`MaryB`に再マップされます。  
  
```  
--Create the new login.  
CREATE LOGIN MaryB WITH PASSWORD = '982734snfdHHkjj3';  
GO  
--Map database user MB-Sales to login MaryB.  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Update_One', 'MB-Sales', 'MaryB';  
GO  
```  
  
### <a name="c-automatically-mapping-a-user-to-a-login-creating-a-new-login-if-it-is-required"></a>C. ユーザーをログインに自動的にマップし、必要に応じて新しいログインを作成する  
 次の例では、を`Auto_Fix`使用して、既存のユーザーを同じ名前のログインにマップする方法、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]また`Mary`はログイン`Mary`が存在`B3r12-3x$098f6`しない場合にパスワードを持つログインを作成する方法を示します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_change_users_login 'Auto_Fix', 'Mary', NULL, 'B3r12-3x$098f6';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Transact-sql&#41;&#40;ログインの作成](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_adduser &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_helplogins &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helplogins-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [database_principals &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
  
  
