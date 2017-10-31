---
title: "アセンブリの許可 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- assemblies [CLR integration], permissions
- DENY statement, assemblies
- denying permissions [SQL Server], assemblies
ms.assetid: be0896b3-f793-44c9-9390-1c6e58f33b2b
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 64a2f7f80cdcf654d295e49535bb61f8ada0b41b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-assembly-permissions-transact-sql"></a>DENY (アセンブリの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アセンブリに対する権限を拒否します。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DENY { permission [ ,...n ] } ON ASSEMBLY :: assembly_name  
    TO database_principal [ ,...n ]   
        [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 アセンブリで拒否できる権限を指定します。 下の表をご覧ください。  
  
 アセンブリの**::***アセンブリ名*  
 権限を拒否するアセンブリを指定します。 スコープ修飾子 "::" が必要です。  
  
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
 アセンブリは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、アセンブリで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に一覧で示します。  
  
|アセンブリ権限|権限が含まれるアセンブリ権限|権限が含まれるデータベース権限|  
|-------------------------|------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASSEMBLY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 アセンブリに対する CONTROL 権限が必要です。 AS オプションを使用する場合、指定するプリンシパルはアセンブリを所有している必要があります。  
  
## <a name="see-also"></a>参照  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [アセンブリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

