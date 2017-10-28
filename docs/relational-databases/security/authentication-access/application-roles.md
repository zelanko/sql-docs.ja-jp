---
title: "アプリケーション ロール | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application roles [SQL Server], about application roles
- principals [SQL Server], application roles
- credentials [SQL Server], roles
- application roles [SQL Server]
- roles [SQL Server], application
- permissions [SQL Server], roles
- users [SQL Server], application roles
- authentication [SQL Server], roles
- groups [SQL Server], roles
ms.assetid: dca18b8a-ca03-4b7f-9a46-8474d5b66f76
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a24b143d85660d979e61a103a077bddaef28029b
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="application-roles"></a>アプリケーション ロール
  アプリケーション ロールは、ユーザーのような独自の権限でアプリケーションを実行できるようにするデータベース プリンシパルです。 アプリケーション ロールを使用すると、特定のアプリケーションから接続しているユーザーに対してのみ、特定のデータへのアクセスを有効にできます。 アプリケーション ロールは、データベース ロールとは異なり、既定ではメンバーが含まれておらず、アクティブではありません。 アプリケーション ロールは、両方の認証モードで機能します。 アプリケーション ロールは **sp_setapprole**を使用して有効化され、これにはパスワードが必要です。 アプリケーション ロールはデータベース レベルのプリンシパルであるため、他のデータベースへのアクセスは、そのデータベースの **guest**に許可された権限を介してのみ可能になります。 したがって、 **guest** が無効になったデータベースには、他のデータベースのアプリケーション ロールからアクセスできなくなります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、アプリケーション ロールは、サーバー レベルのプリンシパルと関連付けられていないため、サーバー レベルのメタデータにはアクセスできません。 この制限を無効にして、アプリケーション ロールがサーバー レベルのメタデータにアクセスできるようにするには、グローバル フラグ 4616 を設定します。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」および「[DBCC TRACEON &#40;Transact-SQL&#41;](../../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md)」を参照してください。  
  
## <a name="connecting-with-an-application-role"></a>アプリケーション ロールを使用した接続  
 アプリケーション ロールがセキュリティ コンテキストを切り替える処理を行う手順は次のとおりです。  
  
1.  ユーザーがクライアント アプリケーションを実行します。  
  
2.  クライアント アプリケーションが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにユーザーとして接続します。  
  
3.  アプリケーションが、このアプリケーションのみに対して既知であるパスワードを使用して、 **sp_setapprole** ストアド プロシージャを実行します。  
  
4.  アプリケーション ロール名およびパスワードが有効であれば、アプリケーション ロールが有効になります。  
  
5.  この時点で、接続はユーザーの権限を失い、アプリケーション ロールの権限を取得します。  
  
 アプリケーション ロールを使用して取得した権限は、接続している間のみ有効です。  
  
 前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、アプリケーション ロールの開始後にユーザーが元のセキュリティ コンテキストを再取得するには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を切断して再接続する以外にありませんでした。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]以降の **sp_setapprole** には、クッキーを作成するオプションがあります。 クッキーには、アプリケーション ロールが有効になる前のコンテキスト情報が格納されます。 **sp_unsetapprole** でクッキーを使用すると、元のコンテキストにセッションを戻すことができます。 この新しいオプションの詳細と例については、「 [sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)に許可された権限を介してのみ可能になります。  
  
> [!IMPORTANT]  
>  **SqlClient** では、ODBC **encrypt**オプションはサポートされていません。 機密情報をネットワーク経由で送信する場合、SSL (Secure Sockets Layer) または IPsec を使用してチャネルを暗号化します。 クライアント アプリケーション内に資格情報を保持しておく必要がある場合、暗号化 API (Crypto API) 関数を使用して資格情報を暗号化します。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンでは、パラメーター *password* は一方向のハッシュとして格納されます。  
  
## <a name="related-tasks"></a>関連タスク  
  
|||  
|-|-|  
|アプリケーション ロールを作成する。|[アプリケーション ロールの作成](../../../relational-databases/security/authentication-access/create-an-application-role.md)および [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-application-role-transact-sql.md)|  
|アプリケーション ロールを変更する。|[ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-application-role-transact-sql.md)|  
|アプリケーション ロールを削除する。|[DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-application-role-transact-sql.md)|  
|アプリケーション ロールを使用する。|[sp_setapprole &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server の保護](../../../relational-databases/security/securing-sql-server.md)  
  
  

