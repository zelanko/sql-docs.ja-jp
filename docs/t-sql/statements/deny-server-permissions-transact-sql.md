---
title: "サーバー アクセス許可 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], servers
- denying permissions [SQL Server], servers
- servers [SQL Server], permissions
- DENY statement, servers
ms.assetid: 68d6b2a9-c36f-465a-9cd2-01d43a667e99
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 424e0188b20d15831debf1e19ff17179fa3472c7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-server-permissions-transact-sql"></a>DENY (サーバーの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバーの権限を拒否します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission [ ,...n ]   
    TO <grantee_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS <grantor_principal> ]   
  
<grantee_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
  
<grantor_principal> ::= SQL_Server_login   
    | SQL_Server_login_mapped_to_Windows_login  
    | SQL_Server_login_mapped_to_Windows_group  
    | SQL_Server_login_mapped_to_certificate  
    | SQL_Server_login_mapped_to_asymmetric_key  
    | server_role  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 サーバーで拒否できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
 \<Server_principal >  
 権限を拒否するプリンシパルを指定します。  
  
 AS \<grantor_principal >  
 このクエリを実行するプリンシパルが権限を拒否する権利を取得した、元のプリンシパルを指定します。  
  
 *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_mapped_to_Windows_login*  
 指定します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインにマップされるログインです。  
  
 *SQL_Server_login_mapped_to_Windows_group*  
 指定します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows グループにマップされるログインです。  
  
 *SQL_Server_login_mapped_to_certificate*  
 証明書にマップされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。  
  
 *SQL_Server_login_mapped_to_asymmetric_key*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
 *server_role*  
 サーバー ロールを指定します。  
  
## <a name="remarks"></a>解説  
 サーバー スコープの権限を拒否できるのは、現在のデータベースが master のときだけです。  
  
 サーバー権限に関する情報を表示することができます、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)でカタログ ビュー、およびサーバー プリンシパルに関する情報を表示できます、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。 サーバー ロールのメンバーシップに関する情報を表示できます、 [sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)カタログ ビューです。  
  
 サーバーは権限の階層の最上位となります。 次の表に、サーバーで拒否できる最も限定的な権限を示します。  
  
|サーバーのアクセス許可|権限が含まれるサーバー権限|  
|-----------------------|----------------------------------|  
|ADMINISTER BULK OPERATIONS|CONTROL SERVER|  
|ALTER ANY AVAILABILITY GROUP<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|ALTER ANY CONNECTION|CONTROL SERVER|  
|ALTER ANY CREDENTIAL|CONTROL SERVER|  
|ALTER ANY DATABASE|CONTROL SERVER|  
|ALTER ANY ENDPOINT|CONTROL SERVER|  
|ALTER ANY EVENT NOTIFICATION|CONTROL SERVER|  
|ALTER ANY EVENT SESSION|CONTROL SERVER|  
|ALTER ANY LINKED SERVER|CONTROL SERVER|  
|ALTER ANY LOGIN|CONTROL SERVER|  
|ALTER ANY SERVER AUDIT|CONTROL SERVER|  
|ALTER ANY SERVER ROLE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|ALTER RESOURCES|CONTROL SERVER|  
|ALTER SERVER STATE|CONTROL SERVER|  
|ALTER SETTINGS|CONTROL SERVER|  
|ALTER TRACE|CONTROL SERVER|  
|AUTHENTICATE SERVER|CONTROL SERVER|  
|CONNECT ANY DATABASE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|CONNECT SQL|CONTROL SERVER|  
|CONTROL SERVER|CONTROL SERVER|  
|CREATE ANY DATABASE|ALTER ANY DATABASE|  
|CREATE AVAILABILITY GROUP<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|ALTER ANY AVAILABILITY GROUP|  
|CREATE DDL EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|CREATE ENDPOINT|ALTER ANY ENDPOINT|  
|CREATE SERVER ROLE<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|ALTER ANY SERVER ROLE|  
|CREATE TRACE EVENT NOTIFICATION|ALTER ANY EVENT NOTIFICATION|  
|EXTERNAL ACCESS ASSEMBLY|CONTROL SERVER|  
|IMPERSONATE ANY LOGIN<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|SELECT ALL USER SECURABLES<br /><br /> **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|CONTROL SERVER|  
|SHUTDOWN|CONTROL SERVER|  
|UNSAFE ASSEMBLY|CONTROL SERVER|  
|VIEW ANY DATABASE|VIEW ANY DEFINITION|  
|VIEW ANY DEFINITION|CONTROL SERVER|  
|VIEW SERVER STATE|ALTER SERVER STATE|  
  
## <a name="remarks"></a>解説  
 次の 3 つのサーバー アクセス許可が追加された[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]です。  
  
 **任意のデータベースを接続**権限  
 Grant **CONNECT ANY DATABASE**ログインにその将来的に作成されるすべての新しいデータベースに現在存在しているすべてのデータベースに接続する必要があります。 接続以外の権限はどのデータベースにおいても一切付与されません。 組み合わせる**SELECT ALL USER SECURABLES**または**VIEW SERVER STATE**のインスタンスのすべてのデータやデータベースの状態を表示する監査プロセスを許可する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 **任意のログインの権限を借用**権限  
 この権限が付与されていると、中間層プロセスがデータベースに接続するときに、そこに接続するクライアントのアカウントの権限を借用できます。 この権限が拒否されていると、高い特権を持つログインが他のログインの権限を借用するのをブロックできます。 たとえばを持つログインが**CONTROL SERVER**から他のログインを借用する権限がブロックされることができます。  
  
 **選択 ALL USER SECURABLES**権限  
 付与されていると、監査担当者などログインが、ユーザーが接続できるすべてのデータベースのデータを表示できます。 拒否されるにアクセスできなくなりますオブジェクトである場合を除いて、 **sys**スキーマです。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限またはセキュリティ保護可能なリソースの所有権が必要です。 AS 句を使用する場合、指定されたプリンシパルは、権限が拒否されるセキュリティ保護可能なリソースを所有している必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-denying-connect-sql-permission-to-a-sql-server-login-and-principals-to-which-the-login-has-regranted-it"></a>A. SQL Server ログインと、このログインが権限を許可したプリンシパルに対して CONNECT SQL 権限を拒否する  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン `CONNECT SQL` と、このログインが権限を許可したプリンシパルに対して、`Annika` 権限を拒否します。  
  
```  
USE master;  
DENY CONNECT SQL TO Annika CASCADE;  
GO  
```  
  
### <a name="b-denying-create-endpoint-permission-to-a-sql-server-login-using-the-as-option"></a>B. AS オプションを使用して、SQL Server ログインに対し CREATE ENDPOINT 権限を拒否する  
 次の例では、ユーザー `CREATE ENDPOINT` に対して `ArifS` 権限を拒否します。 この例では、`AS`を指定するオプション`MandarP`実行中のプリンシパルが、これを行う権限を派生元のプリンシパルとして。  
  
```  
USE master;  
DENY CREATE ENDPOINT TO ArifS AS MandarP;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [サーバー アクセス許可 (TRANSACT-SQL)](../../t-sql/statements/deny-server-permissions-transact-sql.md)   
 [サーバーのアクセス許可 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-server-permissions-transact-sql.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.fn_my_permissions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)  
  
  

