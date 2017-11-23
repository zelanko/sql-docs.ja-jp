---
title: "GRANT アセンブリの権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- granting permissions [SQL Server], assemblies
- assemblies [CLR integration], permissions
- GRANT statement, assemblies
ms.assetid: dce1e027-f859-4967-bdda-16a95ae460d0
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d163245f90ce50defdea4b7a075ef9d0fb9b5afd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grant-assembly-permissions-transact-sql"></a>GRANT (アセンブリの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アセンブリに対する権限を許可します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GRANT { permission [ ,...n ] } ON ASSEMBLY :: assembly_name  
    TO database_principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 アセンブリで許可できる権限を指定します。 下の表をご覧ください。  
  
 アセンブリの**::***アセンブリ名*  
 権限を許可するアセンブリを指定します。 スコープ修飾子 "::" が必要です。  
  
 *database_principal*  
 権限を許可するプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
AS *granting_principal*  
 このクエリを実行するプリンシパルが権限を許可する権利を取得した、元のプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
 アセンブリは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次に、アセンブリで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|アセンブリ権限|権限が含まれるアセンブリ権限|権限が含まれるデータベース権限|  
|-------------------------|------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ASSEMBLY|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用する場合は、次の追加要件があります。  
  
|AS *granting_principal*|必要な追加権限|  
|------------------------------|------------------------------------|  
|データベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows ログインにマップされているデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows グループにマップされているデータベース ユーザー|メンバーシップである Windows グループのメンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|証明書にマップされているデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|非対称キーにマップされるデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|データベース ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|アプリケーション ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
  
 オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を許可できます。  
  
 メンバーなど、CONTROL SERVER 権限の付与、 **sysadmin**固定サーバー ロールは、いずれかに対する権限を許可できるサーバーのセキュリティ保護可能な。 メンバーなど、データベースに対する CONTROL 権限の付与、 **db_owner**固定データベース ロールがいずれかに対する権限を許可できるデータベースのセキュリティ保護可能な。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を許可できます。  
  
## <a name="see-also"></a>参照  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
