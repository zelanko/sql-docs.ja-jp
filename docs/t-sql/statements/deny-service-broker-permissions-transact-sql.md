---
title: "Service Broker の権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/09/2017
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
- denying permissions [Service Broker]
- routes [Service Broker], permissions
- Service Broker, permissions
- DENY statement, Service Broker
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- denying permissions [SQL Server], Service Broker
- contracts [Service Broker], permissions
- services [Service Broker], permissions
ms.assetid: 7c6de71b-865c-41db-9413-ad9b3562e579
caps.latest.revision: "22"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 100c447d3a258ecf8a590173a7c0ef161f0fad3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="deny-service-broker-permissions-transact-sql"></a>DENY (Service Broker の権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssSB](../../includes/sssb-md.md)] コントラクト、メッセージ型、リモート サービス バインド、ルート、またはサービスに対する権限を拒否します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission  [ ,...n ] ON  
    {    
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    TO database_principal [ ,...n ]   
    [ CASCADE ]  
        [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *permission*  
 拒否できる権限を示す、[!INCLUDE[ssSB](../../includes/sssb-md.md)]セキュリティ保護可能な。 権限の一覧については、後の「解説」を参照してください。  
  
 コントラクト **:: * * * contract_name*  
 権限を拒否するコントラクトを指定します。 スコープ修飾子**::**が必要です。  
  
 MESSAGE TYPE **::***message_type_name*  
 権限を拒否するメッセージ型を指定します。 スコープ修飾子**::**が必要です。  
  
 REMOTE SERVICE BINDING **:: * * * remote_binding_name*  
 権限を拒否するリモート サービス バインドを指定します。 スコープ修飾子**::**が必要です。  
  
 ROUTE **::***route_name*  
 権限を拒否するルートを指定します。 スコープ修飾子**::**が必要です。  
  
 サービス **:: * * * message_type_name*  
 権限を拒否するサービスを指定します。 スコープ修飾子**::**が必要です。  
  
 *database_principal*  
 アクセス許可を拒否するプリンシパルを指定します。 次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール  
-   アプリケーション ロール  
-   Windows ログインにマップされているデータベース ユーザー  
-   Windows グループにマップされているデータベース ユーザー  
-   証明書にマップされているデータベース ユーザー  
-   非対称キーにマップされるデータベース ユーザー  
-   サーバー プリンシパルにマップされていないデータベース ユーザー  
  
CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
*denying_principal*  
 このクエリを実行するプリンシパルが権限を拒否する権利の派生元のプリンシパルを指定します。 次のいずれかです。  
  
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
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] コントラクトは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 最も限定的な権限を拒否できる、[!INCLUDE[ssSB](../../includes/sssb-md.md)]コントラクトは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker コントラクト権限|権限が含まれる Service Broker コントラクト権限|権限が含まれるデータベース権限|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Service Broker メッセージ型  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージの種類は、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 最も限定的な権限を拒否できる、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージの種類は、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker メッセージ型権限|権限が含まれる Service Broker メッセージ型権限|権限が含まれるデータベース権限|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Service Broker リモート サービス バインド  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] リモート サービス バインドは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 最も限定的な権限を拒否できる、[!INCLUDE[ssSB](../../includes/sssb-md.md)]リモート サービス バインドは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker リモート サービス バインド権限|権限が含まれる Service Broker リモート サービス バインド権限|権限が含まれるデータベース権限|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Service Broker ルート  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]ルートは、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 最も限定的な権限を拒否できる、[!INCLUDE[ssSB](../../includes/sssb-md.md)]ルートは、次の表に、暗黙的に含む一般的な権限と共に一覧表示します。  
  
|Service Broker ルート権限|権限が含まれる Service Broker ルート権限|権限が含まれるデータベース権限|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Service Broker サービス  
 A[!INCLUDE[ssSB](../../includes/sssb-md.md)]サービスは、データベース レベルのセキュリティ保護可能な権限の階層で親となっているデータベースに格納されています。 最も限定的な権限を拒否できる、[!INCLUDE[ssSB](../../includes/sssb-md.md)]サービスは、次の表に、暗黙的に含む一般的な権限と共に一覧表示されます。  
  
|Service Broker サービス権限|権限が含まれる Service Broker サービス権限|権限が含まれるデータベース権限|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>権限  
 に対する CONTROL 権限が必要です、[!INCLUDE[ssSB](../../includes/sssb-md.md)]コントラクト、メッセージの種類、リモート サービス バインド、ルート、またはサービス。 AS 句を使用する場合、指定されるプリンシパルは、権限の拒否対象となるセキュリティ保護可能なリソースを所有している必要があります。  
  
## <a name="see-also"></a>参照  
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)  
  
  
