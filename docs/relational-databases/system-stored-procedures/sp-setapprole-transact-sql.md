---
title: "sp_setapprole (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_setapprole
- sp_setapprole_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53d4842999b7f66dc731f41480a7beaa38942965
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spsetapprole-transact-sql"></a>sp_setapprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースのアプリケーション ロールに関連付けられている権限をアクティブにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }   
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 現在のデータベースで定義されているアプリケーション ロールの名前を指定します。 *ロール*は**sysname**、既定値はありません。 *ロール*現在のデータベースに存在する必要があります。  
  
 [  **@password =** ] **{暗号化 N'***パスワード***'}**  
 アプリケーション ロールをアクティブにするために必要なパスワードを指定します。 *パスワード*は**sysname**、既定値はありません。 *パスワード*、ODBC を使用して暗号化できます**暗号化**関数。 使用すると、**暗号化**関数の場合、パスワードは、配置することで Unicode 文字列に変換する必要があります**N**最初の引用符の前にします。  
  
 使用している接続で、暗号化オプションはサポートされていません**SqlClient**です。  
  
> [!IMPORTANT]  
>  ODBC**暗号化**関数では、暗号化は提供されません。 ネットワーク経由で転送されるパスワードを保護する場合は、この関数は使用しないでください。 情報をネットワーク経由で転送する場合は、SSL または IPSec を使用します。  
  
 **@encrypt'none' を =**  
 暗号化を使用しないことを示します。 パスワードはプレーンテキストとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に渡されます。 これは既定値です。  
  
 **@encrypt= 'odbc'**  
 ODBC が ODBC を使用して、パスワードを難読化ことを示す**暗号化**関数にパスワードを送信する前に、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 これは、ODBC クライアントまたは OLE DB Provider for SQL Server を使用している場合にのみ指定できます。  
  
 [  **@fCreateCookie =** ] **true** | **false**  
 クッキーを作成するかどうかを指定します。 **true**は 1 を暗黙的に変換します。 **false**は暗黙的に 0 に変換します。  
  
 [  **@cookie =** ]  **@cookie出力**  
 クッキーを含める出力パラメーターを指定します。 場合にのみ、クッキーが生成される値の **@fCreateCookie** は**true**です。 **varbinary (8000)**  
  
> [!NOTE]  
>  **sp_setapprole** のクッキーの **OUTPUT** パラメーターは現在、適切な最大長である **varbinary(8000)** としてドキュメントに記載されています。 ただし、現在の実装では **varbinary(50)**を返します。 アプリケーションが継続して予約する必要があります**varbinary (8000)**アプリケーションのサイズの増加、将来のリリースでクッキーの戻り値が正しく動作を継続できるようにします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 使用して、アプリケーション後ロールがアクティブ化された**sp_setapprole**、ユーザーがサーバーからの接続が切断またはが実行されるまで、ロールがアクティブなまま**sp_unsetapprole**です。 **sp_setapprole**直接でのみ実行できる[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 **sp_setapprole**別のストアド プロシージャまたはユーザー定義のトランザクション内で実行することはできません。  
  
 アプリケーション ロールの概要については、次を参照してください。[アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)です。  
  
> [!IMPORTANT]  
>  ネットワーク経由で送信されるアプリケーション ロールのパスワードを保護するには、アプリケーション ロールを有効化するとき常に、暗号化された接続を使用してください。  
>   
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC**暗号化**では、オプションはサポートされていない**SqlClient**です。 資格情報を格納する必要がある場合は、Crypto API 関数を使用して暗号化します。 パラメーター*パスワード*一方向のハッシュとして格納されます。 旧バージョンとの互換性を維持する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、パスワードの複雑性ポリシーは適用されません**sp_addapprole**です。 パスワードの複雑性ポリシーを適用するのには、使用[CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md)です。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要**パブリック**し、ロールのパスワードを認識します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. オプションを暗号化せずにアプリケーション ロールをアクティブにする  
 次の例では、アプリケーション ロール `SalesAppRole` をアクティブにします。このロールには、プレーンテキストのパスワード `AsDeF00MbXX` が設定されており、現在のユーザーが使用するアプリケーション用に特別に設計された権限が与えられています。  
  
```  
EXEC sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO  
```  
  
### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. クッキーの作成を指定してアプリケーション ロールをアクティブ化し、その後元のコンテキストに戻す  
 次の例では、パスワード `Sales11` が設定されているアプリケーション ロール `fdsd896#gfdbfdkjgh700mM` をアクティブ化し、クッキーを作成します。 この例では、現在のユーザーの名前が返されます。その後、`sp_unsetapprole` を実行して元のコンテキストに戻します。  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_unsetapprole &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)  
  
  
