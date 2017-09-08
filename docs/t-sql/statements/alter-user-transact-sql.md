---
title: "ALTER USER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_USER_TSQL
- ALTER USER
dev_langs:
- TSQL
helpviewer_keywords:
- modifying database users
- ALTER USER statement
- renaming databases
- schemas [SQL Server], default
- database user names [SQL Server]
- names [SQL Server], database users
- default schemas
- modifying default schemas
ms.assetid: 344fc6ce-a008-47c8-a02e-47fae66cc590
caps.latest.revision: 75
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62651475119ba147e6823ba9e25b2cde67678dcc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-user-transact-sql"></a>ALTER USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース ユーザーの名前、またはデータベースの既定のスキーマを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | DEFAULT_LANGUAGE = { NONE | <lcid> | <language name> | <language alias> }  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = schemaName  
    | LOGIN = loginName  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
[;]  
  
-- Azure SQL Database Update Syntax  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
[;]  
  
<set_item> ::=   
      NAME = newUserName   
    | DEFAULT_SCHEMA = { schemaName | NULL }  
    | LOGIN = loginName  
    | PASSWORD = 'password' [ OLD_PASSWORD = 'oldpassword' ]  
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ]   
  
-- SQL Database syntax when connected to a federation member  
ALTER USER userName  
     WITH <set_item> [ ,… n ]   
[;]  
  
<set_item> ::=   
     NAME = newUserName  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER USER userName    
     WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
     NAME =newUserName   
     | LOGIN =loginName  
     | DEFAULT_SCHEMA = schema_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *ユーザー名*  
 データベース内でユーザーを識別する名前を指定します。  
  
 ログイン **=**  *loginName*  
 ユーザーのセキュリティ識別子 (SID) を別のログインの SID に一致するように変更することで、ユーザーを別のログインに再マップします。  
  
 ALTER USER ステートメントが SQL のバッチ内の唯一のステートメントである場合、Windows Azure SQL データベースでは WITH LOGIN 句がサポートされます。 ALTER USER ステートメントが SQL のバッチ内の唯一のステートメントではない場合、または動的 SQL で実行されていない場合、WITH LOGIN 句はサポートされません。  
  
 名前 **=**  *newUserName*  
 このユーザーの新しい名前を指定します。 *newUserName*現在のデータベースには存在しない必要があります。  
  
 DEFAULT_SCHEMA  **=**  { *schemaName* |NULL}  
 このユーザー用のオブジェクトの名前を解決するときに、サーバーで最初に検索されるスキーマを指定します。 既定のスキーマを NULL に設定すると、既定のスキーマが Windows グループから削除されます。   Windows ユーザーでは NULL オプションは使用できません。  
  
 パスワード **=**  '*パスワード*'  
 **適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 変更するユーザーのパスワードを指定します。 パスワードでは大文字と小文字が区別されます。  
  
> [!NOTE]  
>  このオプションは、包含ユーザーに対してのみ使用できます。 参照してください[Contained Databases](../../relational-databases/databases/contained-databases.md)と[sp_migrate_user_to_contained (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)詳細についてはします。  
  
 OLD_PASSWORD  **=**  *'oldpassword'*  
 **適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 現在のユーザー パスワードによって置き換えられる '*パスワード*' です。 パスワードでは大文字と小文字が区別されます。 *OLD_PASSWORD*がない限り、パスワードの変更に必要な**ALTER ANY USER**権限です。 必要とする*OLD_PASSWORD*とユーザーを防止**偽装**からパスワードを変更する権限です。  
  
> [!NOTE]  
>  このオプションは、包含ユーザーに対してのみ使用できます。  
  
 DEFAULT_LANGUAGE  **=**  *{NONE |\<lcid > |\<言語名 > |\<言語の別名 >}*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ユーザーに割り当てる既定の言語を指定します。 このオプションを NONE に設定した場合、既定の言語はデータベースの現在の既定の言語に設定されます。 データベースの既定の言語が将来変更されても、ユーザーの既定の言語は変更されません。 *DEFAULT_LANGUAGE*ローカル ID (lcid)、言語、または言語の別名の名前を指定できます。  
  
> [!NOTE]  
>  このオプションは包含データベースでのみ指定でき、また、包含ユーザーに対してのみ指定できます。  
  
 ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ON |**OFF** ]  
 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 一括コピー操作で、サーバーに対する暗号化メタデータ チェックを抑制します。 これにより、データの暗号化を解除せずにテーブルまたはデータベース間でデータを一括コピーを暗号化するユーザー。 既定値は OFF です。  
  
> [!WARNING]  
>  このオプションを不適切に使用すると、データが破損する場合があります。 詳細については、次を参照してください。[機密性の高いデータで保護された移行 Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)です。  
  
## <a name="remarks"></a>解説  
 既定のスキーマは、このデータベース ユーザー用のオブジェクトの名前を解決するときに、サーバーで最初に検索されるスキーマになります。 特に指定しない限り、このデータベース ユーザーによって作成されたオブジェクトの所有者になるのは、既定のスキーマです。  
  
 ユーザーに既定のスキーマが設定されている場合は、その既定のスキーマが使用されます。 ユーザーに既定のスキーマが指定されておらず、そのユーザーが所属しているグループに既定のスキーマが指定されている場合は、グループの既定のスキーマが使用されます。 ユーザーに既定のスキーマが指定されておらず、そのユーザーが複数のグループに所属している場合、ユーザーの既定のスキーマは、最も小さい principle_id と明示的に設定された既定のスキーマを持つ Windows グループのスキーマになります。 で、ユーザーの既定のスキーマを特定できない場合、 **dbo**スキーマが使用されます。  
  
 DEFAULT_SCHEMA には、データベースに現在存在しないスキーマも設定できます。 したがって、スキーマが作成される前に DEFAULT_SCHEMA をユーザーに割り当てることができます。  
  
 証明書または非対称キーにマップされているユーザーに対して DEFAULT_SCHEMA を指定することはできません。  
  
> [!IMPORTANT]  
>  ユーザーのメンバーである場合、DEFAULT_SCHEMA の値は無視されます、 **sysadmin**固定サーバー ロール。 すべてのメンバー、 **sysadmin**固定サーバー ロールの既定のスキーマのある`dbo`です。  
  
 Windows のログインまたはグループにマップされているユーザーの名前を変更できるのは、新しいユーザー名の SID とデータベースに記録されている SID が一致する場合だけです。 この条件により、データベースにおける Windows ログインのなりすましを防止できます。  
  
 WITH LOGIN 句を使用すると、ユーザーを別のログインに再マップできます。 ログインのないユーザー、証明書にマップされているユーザー、非対称キーにマップされているユーザーをこの句で再マップすることはできません。 SQL ユーザーおよび Windows ユーザー (またはグループ) のみ再マップできます。 WITH LOGIN 句は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインへの Windows アカウントの変更など、ユーザーの種類の変更には使用できません。  
  
 次の条件を満たす場合、ユーザーの名前はログイン名に自動的に変更されます。  
  
-   ユーザーが Windows ユーザーである。  
  
-   名前が Windows 名である (円記号を含む)。  
  
-   新しい名前が指定されていない。  
  
-   現在の名前がログイン名とは異なる。  
  
 これらの条件を満たさない場合は、呼び出し元が NAME 句を追加で呼び出さない限り、ユーザーの名前は変更されません。  
  
マップされたユーザーの名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、証明書または非対称キーは、バック スラッシュ文字を含めることはできません (\\)。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="security"></a>セキュリティ  
  
> [!NOTE]  
>  持つユーザーは**ALTER ANY USER**権限は、すべてのユーザーの既定のスキーマを変更できます。 変更されたスキーマを所有するユーザーは、知らずに間違ったテーブルからデータを選択したり、間違ったスキーマからコードを実行する可能性があります。  
  
### <a name="permissions"></a>Permissions  
 ユーザーの名前を変更する必要があります、 **ALTER ANY USER**権限です。  
  
 ユーザーの対象ログインを変更する必要があります、**コントロール**データベースに対する権限。  
  
 持つユーザーのユーザー名を変更する**コントロール**データベースに対する権限が必要です、**コントロール**データベースに対する権限。  
  
 既定のスキーマまたは言語を変更する必要があります。 **ALTER**ユーザーに対する権限。 ユーザーは自分が所有する既定のスキーマまたは言語を変更できます。  
  
## <a name="examples"></a>使用例  

すべての例は、ユーザー データベースで実行されます。  

### <a name="a-changing-the-name-of-a-database-user"></a>A. データベース ユーザーの名前を変更する  
 次の例は、データベース ユーザーの名前を変更`Mary5`に`Mary51`です。  
  
```  
ALTER USER Mary5 WITH NAME = Mary51;  
GO  
```  
  
### <a name="b-changing-the-default-schema-of-a-user"></a>B. ユーザーの既定のスキーマを変更する  
 次の例は、ユーザーの既定のスキーマを変更`Mary51`に`Purchasing`です。  
  
```  
ALTER USER Mary51 WITH DEFAULT_SCHEMA = Purchasing;  
GO  
```  
  
### <a name="c-changing-several-options-at-once"></a>C. 複数のオプションを一度に変更する  
 次の例では、包含データベース ユーザーに対する複数のオプションを 1 つのステートメントで変更します。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
ALTER USER Philip   
WITH  NAME = Philipe   
    , DEFAULT_SCHEMA = Development   
    , PASSWORD = 'W1r77TT98%ab@#’ OLD_PASSWORD = 'New Devel0per'   
    , DEFAULT_LANGUAGE  = French ;  
GO  
```  
  
  
## <a name="see-also"></a>参照  
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-user-transact-sql.md)   
 [包含データベース](../../relational-databases/databases/contained-databases.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_migrate_user_to_contained & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md)  
  
  



