---
title: "データベース スコープの資格情報 (TRANSACT-SQL) の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP DATABASE SCOPED CREDENTIAL
- DROP_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- DROP DATABASE SCOPED CREDENTIAL statement
- credential [SQL Server], DROP DATABASE SCOPED CREDENTIAL statement
ms.assetid: 319d59f4-fa82-47ca-869b-3a9cd52900b0
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3768e6b95fb991b784c7c4f29c70599970ac1453
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-database-scoped-credential-transact-sql"></a>データベース スコープ ベースの資格情報 (TRANSACT-SQL) を削除します。
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベース スコープの資格情報をサーバーから削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP DATABASE SCOPED CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>引数  
 *credential_name*  
 サーバーから削除するデータベース スコープの資格情報の名前です。  
  
## <a name="remarks"></a>解説  
 データベース スコープ資格情報自体を削除しない限り、データベース スコープ資格情報に関連付けられているシークレットを削除するには、使用[ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md)です。  
  
 データベース スコープ資格情報に関する情報は、 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)カタログ ビューです。  
  
## <a name="permissions"></a>Permissions  
 必要があります`ALTER`資格情報に対する権限。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれるデータベース スコープ資格情報を削除する`SalesAccess`です。  
  
```tsql  
DROP DATABASE SCOPED CREDENTIAL AppCred;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [データベース スコープの資格情報 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER データベース スコープの資格情報 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

