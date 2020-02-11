---
title: プリンシパル (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 54aab33e754331482ef154d9172f0e41cd251db0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63011912"
---
# <a name="principals-database-engine"></a>プリンシパル (データベース エンジン)
  *プリンシパル*は、リソースを要求[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]できるエンティティです。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の承認モデルの他のコンポーネントと同様に、プリンシパルは階層内に配置できます。 プリンシパルの効力のスコープは、プリンシパルの定義のスコープ (Windows、サーバー、データベース) と、プリンシパルが分割できないアイテムであるかコレクションであるかによって異なります。 分割できないプリンシパルの例には Windows ログインがあり、コレクションであるプリンシパルの例には Windows グループがあります。 各プリンシパルには、1 つのセキュリティ識別子 (SID) があります。  
  
 **Windows レベルのプリンシパル**  
  
-   Windows ドメイン ログイン  
  
-   Windows ローカル ログイン  
  
 **SQL Server**-**レベル**の**プリンシパル**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ログイン  
  
-   サーバー ロール  
  
 **データベースレベルのプリンシパル**  
  
-   データベース ユーザー  
  
-   データベース ロール  
  
-   アプリケーション ロール  
  
## <a name="the-sql-server-sa-login"></a>SQL Server sa ログイン  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sa ログインはサーバー レベルのプリンシパルです。 このログインは、インスタンスのインストール時に既定で作成されます。 
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より、sa の既定のデータベースは master です。 これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の動作から変更されています。  
  
## <a name="public-database-role"></a>public データベース ロール  
 データベース ユーザーはすべて、public データベース ロールに属しています。 セキュリティ保護可能なリソースに対する特定の権限が与えられていないか権限が拒否されたユーザーは、public がそのリソースに対して許可されている権限を継承します。  
  
## <a name="information_schema-and-sys"></a>INFORMATION_SCHEMA と sys  
 各データベースには、カタログ ビューにユーザーとして表示される 2 つのエンティティ INFORMATION_SCHEMA および sys が含まれています。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]はこれらを必要とします。 これらのエンティティはプリンシパルではなく、変更も削除もできません。  
  
## <a name="certificate-based-sql-server-logins"></a>証明書ベースの SQL Server ログイン  
 名前が 2 つの番号記号 (##) で囲まれたサーバー プリンシパルは、内部システムでのみ使用されます。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール時に証明書から作成される以下のプリンシパルは、削除しないでください。  
  
-   
  \##MS_SQLResourceSigningCertificate##  
  
-   
  \##MS_SQLReplicationSigningCertificate##  
  
-   
  \##MS_SQLAuthenticatorCertificate##  
  
-   
  \##MS_AgentSigningCertificate##  
  
-   
  \##MS_PolicyEventProcessingLogin##  
  
-   
  \##MS_PolicySigningCertificate##  
  
-   
  \##MS_PolicyTsqlExecutionLogin##  
  
## <a name="the-guest-user"></a>guest ユーザー  
 各データベースには、 **guest**が含まれます。 データベースにはアクセスできるが、データベース内のユーザー アカウントは持っていないユーザーは、 **guest** ユーザーに許可された権限を継承します。 **Guest**ユーザーを削除することはできませんが、 `CONNECT`アクセス許可を取り消すことによって無効にすることができます。 権限`CONNECT`は、master または tempdb `REVOKE CONNECT FROM GUEST`以外のデータベース内で実行することで取り消すことができます。  
  
## <a name="client-and-database-server"></a>クライアントとデータベース サーバー  
 定義上、クライアントとデータベース サーバーはセキュリティ プリンシパルであり、セキュリティで保護できます。 これらのエンティティは、安全なネットワーク接続が確立される前に相互に認証できます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、クライアントがネットワーク認証サービスと対話する方法を定義する[Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758)認証プロトコルがサポートされています。  
  
## <a name="related-tasks"></a>Related Tasks  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックのこのセクションの内容は次のとおりです。  
  
-   [ログイン、ユーザー、およびスキーマの管理方法に関するトピック](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [サーバーレベルのロール](server-level-roles.md)  
  
-   [データベースレベルのロール](database-level-roles.md)  
  
-   [アプリケーションロール](application-roles.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server のセキュリティ保護](../securing-sql-server.md)   
 [database_principals &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)   
 [server_principals &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)   
 [sql_logins &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)   
 [database_role_members &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)   
 [サーバーレベルのロール](server-level-roles.md)   
 [データベースレベルのロール](database-level-roles.md)  
  
  
