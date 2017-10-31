---
title: "REVOKE データベース スコープ資格情報 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- REVOKE DATABASE SCOPED CREDENTIAL
- REVOKE_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statements, database scoped credentials
- revoking permissions [SQL Server], database scoped credentials
ms.assetid: b73233c5-9afa-48ca-ba34-a9f86b9b1d2e
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d05f1829878d31593c56f65dd25660bec9dfa23e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-database-scoped-credential-transact-sql"></a>REVOKE データベース スコープ資格情報 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

  データベース スコープ資格情報に対する権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>引数  
 GRANT OPTION FOR  
 指定した権限を与える許可を取り消します。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 *アクセス許可*  
 データベース スコープ資格情報を取り消すことのできる権限を指定します。 下の表をご覧ください。  
  
 証明書**::***credential_name*  
 これで、権限を取り消すデータベース スコープ資格情報を指定します。 スコープ修飾子 "::" が必要です。  
  
 *database_principal*  
 権限を取り消すプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
 CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS *revoking_principal*  
 このクエリを実行するプリンシパルが権限を取り消す権利を取得した、元のプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
 データベース スコープ資格情報は、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに含まれる、します。 データベース スコープ資格情報で取り消すことが最も限定的アクセス許可を暗黙的に含む一般的な権限と共に示します以下に挙げます。  
  
|データベース スコープの資格情報のアクセス許可|含まれるデータベース スコープ資格情報の権限|権限が含まれるデータベース権限|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 データベース スコープ資格情報に対する CONTROL 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [REVOKE (TRANSACT-SQL)](../../t-sql/statements/revoke-transact-sql.md)      
 [GRANT データベース スコープ資格情報 (TRANSACT-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)   
 [データベース スコープ資格情報 (TRANSACT-SQL) を拒否します。](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

