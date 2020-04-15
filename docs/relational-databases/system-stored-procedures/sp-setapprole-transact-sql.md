---
title: sp_setapprole (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b158c4571deadadeaee23ffa6e46eb48a8c8446e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299607"
---
# <a name="sp_setapprole-transact-sql"></a>sp_setapprole (トランザクション-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースのアプリケーション ロールに関連付けられている権限をアクティブにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>引数

`[ @rolename = ] 'role'`現在のデータベースで定義されているアプリケーション ロールの名前です。 *ロール*は**sysname**で、デフォルトはありません。 *ロール*は現在のデータベースに存在する必要があります。  
  
`[ @password = ] { encrypt N'password' }`アプリケーション ロールをアクティブ化するために必要なパスワードです。 *パスワード*は**sysname**で、デフォルトはありません。 *パスワード*は、ODBC**暗号化**機能を使用して難読化できます。 **暗号化**機能を使用する場合、パスワードは最初の引用符の前に**N**を置くことによって Unicode 文字列に変換する必要があります。  
  
 **SqlClient**を使用している接続では、暗号化オプションはサポートされていません。  
  
> [!IMPORTANT]  
> ODBC**暗号化**機能では暗号化は行われません。 ネットワーク経由で送信されるパスワードを保護するために、この機能に依存しないでください。 この情報がネットワーク経由で転送される場合は、TLS または IPSec を使用します。
  
 **@encrypt= 'なし'**  
 暗号化を使用しないことを示します。 パスワードはプレーンテキストとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に渡されます。 これは既定値です。  
  
 **@encrypt= 'odbc'**  
 ODBC がパスワードをに送信する前に、ODBC**暗号化**関数を使用してパスワードを難読[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]化することを指定します。 この指定は、ODBC クライアントまたは SQL Server 用 OLE DB プロバイダーを使用している場合にのみ指定できます。  
  
`[ @fCreateCookie = ] true | false`Cookie を作成するかどうかを指定します。 **true**は暗黙的に 1 に変換されます。 **false**は暗黙的に 0 に変換されます。  
  
`[ @cookie = ] @cookie OUTPUT`Cookie を格納する出力パラメーターを指定します。 このクッキーは**\@、fCreateCookie**の値が**true の**場合にのみ生成されます。 **varbinary(8000)**  
  
> [!NOTE]  
> **sp_setapprole** のクッキーの **OUTPUT** パラメーターは現在、適切な最大長である **varbinary(8000)** としてドキュメントに記載されています。 ただし、現在の実装では **varbinary(50)** を返します。 アプリケーションは、今後のリリースで Cookie の戻りサイズが大きくなるとアプリケーションが正しく動作し続けるため **、varbinary(8000) を**引き続き予約する必要があります。
  
## <a name="return-code-values"></a>リターン コードの値

 0 (成功) および 1 (失敗)  
  
## <a name="remarks"></a>解説

 sp_setapprole**を使用**してアプリケーション ロールをアクティブ化した後、ユーザーがサーバーから切断するか、**または sp_unsetapprole**を実行するまで、ロールはアクティブな状態のままになります。 **sp_setapprole**は、直接[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントによってのみ実行できます。 **sp_setapprole**は、別のストアド プロシージャ内またはユーザー定義トランザクション内では実行できません。  
  
 アプリケーション ロールの概要については、「[アプリケーション](../../relational-databases/security/authentication-access/application-roles.md)ロール 」を参照してください。  
  
> [!IMPORTANT]  
> アプリケーション ロールのパスワードをネットワーク経由で送信するときに保護するには、アプリケーション ロールを有効にするときには、常に暗号化された接続を使用する必要があります。
> [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC**暗号化**オプションは**SqlClient**ではサポートされていません。 資格情報を格納する必要がある場合は、Crypto API 関数を使用して暗号化します。 パラメータ*のパスワード*は、一方向のハッシュとして格納されます。 以前のバージョンの の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パスワード複雑度ポリシーとの互換性を維持するために **、sp_addapprole**ではパスワードの複雑さのポリシーは適用されません。 パスワード複雑度ポリシーを適用するには[、CREATE アプリケーション ロール](../../t-sql/statements/create-application-role-transact-sql.md)を使用します。  
  
## <a name="permissions"></a>アクセス許可

**パブリック**のメンバーシップとロールのパスワードの知識が必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. 暗号化オプションを使用しないアプリケーション ロールのアクティブ化

 次の例では、アプリケーション ロール `SalesAppRole` をアクティブにします。このロールには、プレーンテキストのパスワード `AsDeF00MbXX` が設定されており、現在のユーザーが使用するアプリケーション用に特別に設計された権限が与えられています。

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Cookie を使用してアプリケーション ロールをアクティブ化し、元のコンテキストに戻す

 次の例では、パスワード `Sales11` が設定されているアプリケーション ロール `fdsd896#gfdbfdkjgh700mM` をアクティブ化し、クッキーを作成します。 この例では、現在のユーザーの名前が返されます。その後、`sp_unsetapprole` を実行して元のコンテキストに戻します。  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>参照

 Transact-SQL&#41;セキュリティ ストアド プロシージャ[&#40;&#40;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)&#41;[作成アプリケーション ロール&#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md) drop アプリケーション[ロール&#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md) sp_unsetapprole &#40;[Transact-SQL&#41;&#40;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)システム ストアド プロシージャ[Security Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)
