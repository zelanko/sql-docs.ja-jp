---
title: "拒否する非対称キーの権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], asymmetric keys
- encryption [SQL Server], asymmetric keys
- permissions [SQL Server], asymmetric keys
- asymmetric keys [SQL Server], permissions
- DENY statement, asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: dd7d8cd5-536b-460c-ab5b-cb4752bbdfaa
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 386db84b88813109e10d951689868a5c3931cff9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-asymmetric-key-permissions-transact-sql"></a>DENY (非対称キーの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  非対称キーに対する権限を拒否します。  
   
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DENY { permission  [ ,...n ] }   
    ON ASYMMETRIC KEY :: asymmetric_key_name   
        TO database_principal [ ,...n ]  
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 非対称キーに対して拒否できる権限を指定します。 下の表をご覧ください。  
  
 非対称キーに対する**::***asymmetric_key_name*  
 権限を拒否する非対称キーを指定します。 スコープ修飾子 "::" が必要です。  
  
 *database_principal*  
 アクセス許可を拒否するプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
 CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
 *denying_principal*  
 このクエリを実行するプリンシパルが権限を拒否する権利の派生元のプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
  
-   データベース ロール (database role)  
  
-   アプリケーション ロール (application role)  
  
-   Windows ログインにマップされるデータベース ユーザー  
  
-   Windows グループにマップされるデータベース ユーザー  
  
-   証明書にマップされるデータベース ユーザー  
  
-   非対称キーにマップされているデータベース ユーザー  
  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
 非対称キーは、データベース レベルの保護可能なアイテムで、権限の階層で親となっているデータベースに含まれています。 次に、非対称キーで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|非対称キーの権限|権限が含まれる非対称キー権限|権限が含まれるデータベース権限|  
|-------------------------------|------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASYMMETRIC KEY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 非対称キーに対する CONTROL 権限が必要です。 AS 句が使用されている場合、指定したプリンシパルが非対称キーを所有している必要があります。  
  
## <a name="see-also"></a>参照  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

