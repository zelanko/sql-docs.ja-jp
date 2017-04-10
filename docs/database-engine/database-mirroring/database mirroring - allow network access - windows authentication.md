---
title: "Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows 認証 [SQL Server]"
  - "データベース ミラーリング [SQL Server], セキュリティ"
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 34
ms.author: "mikeray"
manager: "jhubbard"
---
# Windows 認証を使用してデータベース ミラーリング エンドポイントへのネットワーク アクセスを許可する (SQL Server)
  次のような条件下で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つのインスタンスのデータベース ミラーリング エンドポイントに接続するために Windows 認証を使用するときは、ログイン アカウントを手動で構成する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが (同じドメインまたは信頼関係のあるドメインの) 異なるドメイン アカウントでサービスとして実行される場合、各リモート サーバー インスタンス上の **master** に各アカウントのログインを作成する必要があります。また、そのログインには、エンドポイントに対する CONNECT 権限を与える必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがネットワーク サービス アカウントとして実行される場合、各リモート サーバー インスタンス上の **master** に各ホスト コンピューター アカウント (*DomainName***\\***ComputerName$*) のログインを作成する必要があります。また、そのログインには、エンドポイントに対する CONNECT 権限を与える必要があります。 これは、ネットワーク サービス アカウントで実行されているサーバー インスタンスではホスト コンピューターのドメイン アカウントを使用して認証を行うためです。  
  
> [!NOTE]  
>  各サーバー インスタンスのエンドポイントが存在することを確認してください。 詳細については、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」を参照してください。  
  
### Windows 認証のログインを構成するには  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスのユーザー アカウントについて、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスでログインを作成します。 [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) ステートメントと FROM WINDOWS 句を使用します。  
  
     詳細については、「[ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)」を参照してください。  
  
2.  ログイン ユーザーがエンドポイントにアクセスできるように、[GRANT](../../t-sql/statements/grant-transact-sql.md) ステートメントを使用して、エンドポイントへの接続権限をそのログインに許可します。 エンドポイントへの接続権限の許可は、管理者には不要なので注意してください。  
  
     詳細については、「[プリンシパルに対する権限の許可](../../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md)」を参照してください。  
  
## 例  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] の例では、`Otheruser` というドメインに所属するユーザー アカウント `Adomain` の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを作成します。 このユーザーには、`Mirroring_Endpoint` という既存のデータベース ミラーリング エンドポイントへの接続権限を許可します。  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [データベース ミラーリングと AlwaysOn 可用性グループのトランスポート セキュリティ &#40;SQL Server&#41;](../../database-engine/database-mirroring/transport security - database mirroring - always on availability.md)   
 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  