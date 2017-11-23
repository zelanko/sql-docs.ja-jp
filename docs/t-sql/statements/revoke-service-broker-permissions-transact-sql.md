---
title: "Service Broker の権限 (TRANSACT-SQL) を取り消す |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- routes [Service Broker], permissions
- Service Broker, permissions
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
- services [Service Broker], permissions
- REVOKE statement, Service Broker
ms.assetid: 70f1d938-97e2-48a4-9bc0-8be9f2f2c36d
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 077fe296f48de1658a56d0c3e7403904652603bc
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="revoke-service-broker-permissions-transact-sql"></a>REVOKE (Service Broker の権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssSB](../../includes/sssb-md.md)] コントラクト、メッセージ型、リモート サービス バインド、ルート、またはサービスに対する権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON  
    {   
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>引数  
 GRANT OPTION FOR  
 指定した権限を他のプリンシパルに与えるための権限が、取り消されます。 権限自体は取り消されません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 *アクセス許可*  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] のセキュリティ保護可能なリソースに対して取り消せる権限を指定します。 これらのアクセス許可の一覧は、このトピックの後半の「解説」セクションを参照してください。  
  
 コントラクト**::***contract_name*  
 権限を取り消すコントラクトを指定します。 スコープ修飾子**::**が必要です。  
  
 メッセージの種類**::***message_type_name*  
 権限を取り消すメッセージ型を指定します。 スコープ修飾子**::**が必要です。  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 権限を取り消すリモート サービス バインドを指定します。 スコープ修飾子**::**が必要です。  
  
 ルート**::***route_name*  
 権限を取り消すルートを指定します。 スコープ修飾子**::**が必要です。  
  
 サービス**::***message_type_name*  
 権限を取り消すサービスを指定します。 スコープ修飾子**::**が必要です。  
  
 *database_principal*  
 権限を取り消すプリンシパルを指定します。 *database_principal*次のいずれかになります。  
  
-   データベース ユーザー  
  
-   データベース ロール  
  
-   アプリケーション ロール  
  
-   Windows ログインにマップされているデータベース ユーザー  
  
-   Windows グループにマップされているデータベース ユーザー  
  
-   証明書にマップされているデータベース ユーザー  
  
-   非対称キーにマップされるデータベース ユーザー  
  
-   サーバー プリンシパルにマップされていないデータベース ユーザー  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS *revoking_principal*  
 このクエリを実行するプリンシパルが権限を取り消す権利を取得した、元のプリンシパルを指定します。 *revoking_principal*次のいずれかになります。  
  
-   データベース ユーザー  
  
-   データベース ロール  
  
-   アプリケーション ロール  
  
-   Windows ログインにマップされているデータベース ユーザー  
  
-   Windows グループにマップされているデータベース ユーザー  
  
-   証明書にマップされているデータベース ユーザー  
  
-   非対称キーにマップされるデータベース ユーザー  
  
-   サーバー プリンシパルにマップされていないデータベース ユーザー  
  
## <a name="remarks"></a>解説  
  
## <a name="service-broker-contracts"></a>Service Broker コントラクト  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]コントラクトは、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 特定限定的な権限のうち最もで取り消すことができます、[!INCLUDE[ssSB](../../includes/sssb-md.md)]コントラクトは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker コントラクト権限|権限が含まれる Service Broker コントラクト権限|権限が含まれるデータベース権限|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Service Broker メッセージ型  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージの種類は、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 次の表に、[!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージ型で取り消せる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|Service Broker メッセージ型権限|権限が含まれる Service Broker メッセージ型権限|権限が含まれるデータベース権限|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Service Broker リモート サービス バインド  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] リモート サービス バインドは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 特定限定的な権限のうち最もで取り消すことができます、[!INCLUDE[ssSB](../../includes/sssb-md.md)]リモート サービス バインドは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker リモート サービス バインド権限|権限が含まれる Service Broker リモート サービス バインド権限|権限が含まれるデータベース権限|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Service Broker ルート  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]ルートは、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 特定限定的な権限のうち最もで取り消すことができます、[!INCLUDE[ssSB](../../includes/sssb-md.md)]ルートは、次の表に、暗黙的に含む一般的な権限と共に一覧表示します。  
  
|Service Broker ルート権限|権限が含まれる Service Broker ルート権限|権限が含まれるデータベース権限|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Service Broker サービス  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]サービスは、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 特定限定的な権限のうち最もで取り消すことができます、[!INCLUDE[ssSB](../../includes/sssb-md.md)]サービスは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker サービス権限|権限が含まれる Service Broker サービス権限|権限が含まれるデータベース権限|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] コントラクト、メッセージ型、リモート サービス バインド、ルート、またはサービスに対する CONTROL 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)   
 [Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
