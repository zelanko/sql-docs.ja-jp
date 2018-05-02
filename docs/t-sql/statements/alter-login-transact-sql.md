---
title: ALTER LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
caps.latest.revision: 68
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d1a1bbef130ca5b5fef4255121a8d602c9dc47d2
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    | <cryptographic_credential_option>  
    }   
[;]  
  
<status_option> ::=  
        ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD = 'password' | hashed_password HASHED  
    [   
      OLD_PASSWORD = 'oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }  
    | CREDENTIAL = credential_name  
    | NO CREDENTIAL  
  
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
  
<cryptographic_credentials_option> ::=   
    ADD CREDENTIAL credential_name  
  | DROP CREDENTIAL credential_name  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse 
  
ALTER LOGIN login_name   
  {   
      <status_option>   
    | WITH <set_option> [ ,.. .n ]   
  }   
[;]  
  
<status_option> ::=  
    ENABLE | DISABLE  
  
<set_option> ::=   
    PASSWORD ='password'   
    [  
      OLD_PASSWORD ='oldpassword'  
    ]   
    | NAME = login_name  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    }   
  
<status_option> ::=ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD ='password'   
    [   
      OLD_PASSWORD ='oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }   
      
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
```  
  
## <a name="arguments"></a>引数  
 *login_name*  
 変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの名前を指定します。 ドメイン ログインは角かっこで囲み、[domain\user] の形式で表す必要があります。  
  
 ENABLE | DISABLE  
 このログインを有効にするか無効にするかを指定します。 ログインを無効にしても、既に接続されているログインの動作には影響しません。 (`KILL` ステートメントを使用して、既存の接続を終了します。)無効にしたログインの権限を保持したまま、偽装を継続することができます。  
  
 PASSWORD **='***password***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 変更するログインのパスワードを指定します。 パスワードでは大文字と小文字が区別されます。  
  
 SQL データベースに対するアクティブな接続が (データベース エンジンによって実行されます) を再認証を必要と継続的に、少なくとも 10 時間。 データベース エンジンは、最初に送信されたパスワードを使用して再認証を試行して、ユーザー入力は必要ありません。 パフォーマンス上の理由から、SQL データベースで、パスワードがリセットされたとき、接続はできません、再認証場合でも、接続プールのために、接続がリセットします。 これは、内部設置型 SQL Server の動作と異なります。 接続が最初に承認されているために、パスワードは変更されている場合、は、接続を終了する必要があり、新しいパスワードを使用して新しい接続が作成します。 KILL DATABASE CONNECTION 権限を持つユーザーは、KILL コマンドを使用して SQL データベースへの接続を明示的に終了できます。 詳しくは、「[KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md)」をご覧ください。  
  
 PASSWORD **=***hashed_password*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 HASHED キーワードにのみ適用されます。 作成するログインのパスワードのハッシュ値を指定します。  
  
> [!IMPORTANT]  
>  ログイン (または包含データベース ユーザー) が接続して認証されると、接続にはログインに関する ID 情報がキャッシュされます。 Windows 認証ログインの場合、これには Windows グループのメンバーシップに関する情報も含まれます。 接続が維持されている限り、ログインの ID が認証された状態は継続します。 パスワードのリセットや Windows グループのメンバーシップの変更など、ID に関する変更を適用するには、認証機関 (Windows または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) からログオフしてもう一度ログインする必要があります。 **sysadmin** 固定サーバー ロールのメンバーまたは **ALTER ANY CONNECTION** 権限を持つすべてのログインは、 **KILL** コマンドを使用して接続を終了し、ログインの再接続を強制することができます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプ ローラーおよびクエリ エディター ウィンドウに複数の接続を開くときに、接続情報を再利用できます。 再接続を強制するには、すべての接続を閉じます。  
  
 HASHED   
   
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのみに適用されます。 PASSWORD 引数の後に入力されたパスワードが、ハッシュ済みであることを示します。 このオプションを選択しなかった場合、パスワードはハッシュされてからデータベースに格納されます。 このオプションは、2 つのサーバー間でログインを同期する場合にのみ使用してください。 パスワードを定期的に変更する場合は HASHED オプションを使用しないでください。  
  
 OLD_PASSWORD **='***oldpassword***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 新しいパスワードを割り当てるログインの、現在のパスワードを指定します。 パスワードでは大文字と小文字が区別されます。  
  
 MUST_CHANGE   
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ～ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、および Parallel Data Warehouse。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 このオプションを指定した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で変更後のログインを最初に使用するときには新しいパスワードの入力が求められます。  
  
 DEFAULT_DATABASE **=***database*  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 既定のデータベースをログインに割り当てます。  
  
 DEFAULT_LANGUAGE **=***language*  
 
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 既定の言語をログインに割り当てます。 すべての SQL Database ログインの既定の言語は英語で、変更できません。 Linux では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の `sa` ログインの既定の言語は英語ですが、変更することができます。  
  
 NAME = *login_name*  
 ログインの名前を変更する場合、新しい名前を指定します。 Windows ログインの場合は、新しい名前に対応する Windows プリンシパルの SID と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のログインに関連付けられている SID が一致する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの新しい名前には、円記号 (\\) は使用できません。  
  
 CHECK_EXPIRATION = { ON | **OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ～ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、および Parallel Data Warehouse。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 このログインに、パスワードの有効期限ポリシーを適用するかどうかを指定します。 既定値は OFF です。  
  
 CHECK_POLICY **=** { **ON** | OFF }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ～ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、および Parallel Data Warehouse。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 このログインに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの、Windows のパスワード ポリシーを適用するかどうかを指定します。 既定値は ON です。  
  
 CREDENTIAL = *credential_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップする資格情報の名前を指定します。 この資格情報はサーバー内に存在する必要があります。 詳しくは、「[資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)」をご覧ください。 資格情報は、sa ログインにマップすることはできません。  
  
 NO CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインからサーバー資格情報へのマッピングがある場合は削除します。 詳しくは、「[資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)」をご覧ください。  
  
 UNLOCK  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ～ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、および Parallel Data Warehouse。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 ロックされているログインのロックを解除します。  
  
 ADD CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 拡張キー管理 (EKM: Extensible Key Management) プロバイダー資格情報をログインに追加します。 詳しくは、「[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)」をご覧ください。  
  
 DROP CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
ログインから拡張キー管理 (EKM) プロバイダー資格情報を削除します。 詳しくは、「[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks  
 CHECK_POLICY が ON に設定されている場合、HASHED 引数は使用できません。  
  
 CHECK_POLICY を ON に変更した場合、次の動作が発生します。  
  
-   パスワードの履歴が、現在のパスワード ハッシュの値に初期化されます。  
  
 CHECK_POLICY を OFF に変更した場合、次の動作が発生します。  
  
-   CHECK_EXPIRATION も OFF に設定されます。  
  
-   パスワード履歴は消去されます。  
  
-   値 *lockout_time* がリセットされます。  
  
MUST_CHANGE が指定された場合、CHECK_EXPIRATION および CHECK_POLICY は ON に設定されなければなりません。 ON に設定しない場合、ステートメントは失敗します。  
  
CHECK_POLICY を OFF に設定した場合、CHECK_EXPIRATION を ON に設定することはできません。 このオプションの組み合わせで ALTER LOGIN ステートメントを実行すると、ステートメントは失敗します。  
  
ALTER_LOGIN を DISABLE 引数と共に使用して Windows グループへのアクセスを拒否することはできません。 たとえば、ALTER_LOGIN [*domain\group*] DISABLE を実行すると次のエラー メッセージが返されます。  
  
 "メッセージ 15151、レベル 16、状態 1、行 1"  
  
 "ログイン '*Domain\Group*' を変更できません。存在しないか、権限がありません。"  
  
 これは仕様です。  
  
[!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、接続の認証に必要なログイン データおよびサーバー レベルのファイアウォール規則は、各データベースで一時的にキャッシュされます。 このキャッシュは定期的に更新されます。 認証キャッシュを強制的に更新し、データベースにログイン テーブルの最新バージョンがあることを確認するには、[DBCC FLUSHAUTHCACHE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) を実行します。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY LOGIN 権限が必要です。  
  
 CREDENTIAL オプションを使用する場合は、ALTER ANY CREDENTIAL 権限も必要です。  
  
 変更するログインが固定サーバー ロール **sysadmin** のメンバーであるか、ログインに CONTROL SERVER 権限が与えられている場合、次の変更を行うには CONTROL SERVER 権限も必要になります。  
  
-   以前のパスワードを指定せずにパスワードをリセットする。  
  
-   MUST_CHANGE、CHECK_POLICY、または CHECK_EXPIRATION を有効にする。  
  
-   ログイン名を変更する。  
  
-   ログインを有効または無効にする。  
  
-   ログインを別の資格情報にマップする。  
  
 プリンシパルは、所有するログインのパスワード、既定の言語、および既定のデータベースを変更できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-enabling-a-disabled-login"></a>A. 無効なログインを有効にする  
 次の例では、ログイン `Mary5` を有効にします。  
  
```sql  
ALTER LOGIN Mary5 ENABLE;  
```  
  
### <a name="b-changing-the-password-of-a-login"></a>B. ログインのパスワードを変更する  
 次の例では、ログイン `Mary5` のパスワードを強力なパスワードに変更します。  
  
```sql  
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
### <a name="c-changing-the-name-of-a-login"></a>C. ログインの名前を変更する  
 次の例では、ログイン `Mary5` の名前を `John2` に変更します。  
  
```sql  
ALTER LOGIN Mary5 WITH NAME = John2;  
```  
  
### <a name="d-mapping-a-login-to-a-credential"></a>D. ログインを資格情報にマップする  
 次の例では、ログイン `John2` を資格情報 `Custodian04` にマップします。  
  
```sql  
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;  
```  
  
### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. ログインを拡張キー管理資格情報にマップする  
 次の例では、ログイン `Mary5` を EKM 資格情報 `EKMProvider1` にマップします。  
  
 
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```sql  
ALTER LOGIN Mary5  
ADD CREDENTIAL EKMProvider1;  
GO  
```  
  
### <a name="f-unlocking-a-login"></a>F. ログインのロックを解除する  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのロックを解除するには、**** を必要なアカウントのパスワードに置き換えて、次のステートメントを実行します。  
  
  
```sql  
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;  

GO  
```  
  
 パスワードを変更しないでログインのロックを解除するには、チェック ポリシーをオフにしてからもう一度オンにします。  
  
```sql  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;  
GO  
```  
  
### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. HASHED を使用してログインのパスワードを変更する  
 次の例では、`TestUser` ログインのパスワードを既にハッシュされた値に変更します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```sql  
ALTER LOGIN TestUser WITH   
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;  
GO  
```  
  
 
  
## <a name="see-also"></a>参照  
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  


