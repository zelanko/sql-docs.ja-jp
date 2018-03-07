---
title: "アプリケーション ロール (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
f1_keywords:
- APPLICATION_ROLE_TSQL
- CREATE APPLICATION ROLE
- sql13.swb.applicationrole.permissions.f1
- APPLICATION
- APPLICATION ROLE
- CREATE_APPLICATION_ROLE_TSQL
- APPLICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE APPLICATION ROLE statement
- application roles [SQL Server], creating
ms.assetid: 647386da-ee80-41cf-86c9-dd590f9d66b6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 167b3b66439d352cac9632a9b9a2490c1ebaa95b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-application-role-transact-sql"></a>CREATE APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アプリケーション ロールを現在のデータベースに追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE APPLICATION ROLE application_role_name   
    WITH PASSWORD = 'password' [ , DEFAULT_SCHEMA = schema_name ]  
```  
  
## <a name="arguments"></a>引数  
 *application_role_name*  
 アプリケーション ロールの名前を指定します。 この名前は、データベース内のどのプリンシパルへの参照にも使用されていない名前である必要があります。  
  
 パスワード**='***パスワード***'**  
 データベース ユーザーがアプリケーション ロールのアクティブ化に使用するパスワードを指定します。 複雑なパスワードの使用をお勧めします。 *パスワード*のインスタンスを実行しているコンピューターの Windows パスワード ポリシーの要件を満たす必要がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 DEFAULT_SCHEMA  **=**  *schema_name*  
 このロール用のオブジェクトの名前を解決するときに、サーバーで最初に検索されるスキーマを指定します。 DEFAULT_SCHEMA が定義されていない場合、アプリケーション ロールでは既定のスキーマとして DBO が使用されます。 *schema_name*データベースに存在しないスキーマを指定できます。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  アプリケーション ロールのパスワードを設定するときには、パスワードの複雑性が確認されます。 アプリケーション ロールを呼び出すアプリケーションは、これらのパスワードを格納する必要があります。 アプリケーション ロールのパスワードは常に暗号化して保存する必要があります。  
  
 アプリケーション ロールは、 [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)カタログ ビューです。  
  
 アプリケーション ロールを使用する方法については、次を参照してください。[アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)です。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例と呼ばれるアプリケーション ロールを作成する`weekly_receipts`パスワードを持つ`987Gbv876sPYY5m23`と`Sales`既定のスキーマとして。  
  
```  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987G^bv876sPY)Y5m23'   
    , DEFAULT_SCHEMA = Sales;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_setapprole と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [パスワード ポリシー](../../relational-databases/security/password-policy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
