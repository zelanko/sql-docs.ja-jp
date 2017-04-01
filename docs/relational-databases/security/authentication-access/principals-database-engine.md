---
title: "プリンシパル (データベース エンジン) | Microsoft Docs"
ms.custom: ""
ms.date: "01/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.roleproperties.selectroll.f1"
  - "sql13.swb.databaseuser.permissions.user.f1--May use common.permissions"
helpviewer_keywords: 
  - "証明書 [SQL Server], プリンシパル"
  - "ロール [SQL Server], プリンシパル"
  - "権限 [SQL Server], プリンシパル"
  - "##MS_SQLAuthenticatorCertificate##"
  - "プリンシパル [SQL Server]"
  - "##MS_SQLResourceSigningCertificate##"
  - "グループ [SQL Server], プリンシパル"
  - "##MS_AgentSigningCertificate##"
  - "認証 [SQL Server], プリンシパル"
  - "スキーマ [SQL Server], プリンシパル"
  - "プリンシパル [SQL Server], プリンシパルについて"
  - "セキュリティ [SQL Server], プリンシパル"
  - "ユーザー [SQL Server], プリンシパル"
  - "##MS_SQLReplicationSigningCertificate##"
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
caps.latest.revision: 57
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# プリンシパル (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../../includes/tsql-appliesto-ss2008-all-md.md)]

  *プリンシパル*は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] リソースを要求できるエンティティです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の承認モデルの他のコンポーネントと同様に、プリンシパルは階層内に配置できます。 プリンシパルの効力のスコープは、プリンシパルの定義のスコープ (Windows、サーバー、データベース) と、プリンシパルが分割できないアイテムであるかコレクションであるかによって異なります。 分割できないプリンシパルの例には Windows ログインがあり、コレクションであるプリンシパルの例には Windows グループがあります。 各プリンシパルには、1 つのセキュリティ識別子 (SID) があります。  
  
 **Windows レベルのプリンシパル**  
  
-   Windows ドメイン ログイン  
  
-   Windows ローカル ログイン  
  
 **SQL Server** **レベル**の**プリンシパル**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Login  
  
-   サーバー ロール  
  
 **データベースレベルのプリンシパル**  
  
-   データベース ユーザー  
  
-   データベース ロール  
  
-   アプリケーション ロール  
  
## SQL Server sa ログイン  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa ログインはサーバー レベルのプリンシパルです。 このログインは、インスタンスのインストール時に既定で作成されます。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より、sa の既定のデータベースは master です。 これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の動作から変更されています。  
  
## public データベース ロール  
 データベース ユーザーはすべて、public データベース ロールに属しています。 セキュリティ保護可能なリソースに対する特定の権限が与えられていないか権限が拒否されたユーザーは、public がそのリソースに対して許可されている権限を継承します。  
  
## INFORMATION_SCHEMA と sys  
 各データベースには、カタログ ビューにユーザーとして表示される 2 つのエンティティ INFORMATION_SCHEMA および sys が含まれています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はこれらを必要とします。 これらのエンティティはプリンシパルではなく、変更も削除もできません。  
  
## 証明書ベースの SQL Server ログイン  
 名前が 2 つの番号記号 (##) で囲まれたサーバー プリンシパルは、内部システムでのみ使用されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール時に証明書から作成される以下のプリンシパルは、削除しないでください。  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## guest ユーザー  
 各データベースには、**guest** が含まれます。 データベースにはアクセスできるが、データベース内のユーザー アカウントは持っていないユーザーは、**guest** ユーザーに許可された権限を継承します。 **guest** ユーザーを削除することはできませんが、**CONNECT** 権限を取り消すことで無効にすることはできます。 **CONNECT** 権限を取り消すには、master または tempdb 以外のデータベース内で `REVOKE CONNECT FROM GUEST` を実行します。  
  
## クライアントとデータベース サーバー  
 定義上、クライアントとデータベース サーバーはセキュリティ プリンシパルであり、セキュリティで保護できます。 これらのエンティティは、安全なネットワーク接続が確立される前に相互に認証できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、クライアントとネットワーク認証サービスとのやり取りを定義する [Kerberos](http://go.microsoft.com/fwlink/?LinkId=100758) 認証プロトコルをサポートしています。  
  
## 関連タスク  
 権限システムの設計の詳細については、「[データベース エンジンの権限の概要](../../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのこのセクションの内容は次のとおりです。  
  
-   [ログイン、ユーザー、およびスキーマの管理方法に関するトピック](../../../relational-databases/security/authentication-access/managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [サーバー レベルのロール](../../../relational-databases/security/authentication-access/server-level-roles.md)  
  
-   [データベース レベルのロール](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
-   [アプリケーション ロール](../../../relational-databases/security/authentication-access/application-roles.md)  
  
## 参照  
 [SQL Server の保護](../../../relational-databases/security/securing-sql-server.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.sql_logins &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [サーバー レベルのロール](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [データベース レベルのロール](../../../relational-databases/security/authentication-access/database-level-roles.md)  
  
  