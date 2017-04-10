---
title: "[更新可能なサブスクリプション] のログイン | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.updatablesubscriptionslogin.f1"
ms.assetid: 301ea227-0455-40ba-9009-d38f8676b325
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# [更新可能なサブスクリプション] のログイン
  選択した場合、即時更新プログラムの **レプリケート** 上、 **更新可能なサブスクリプション** ページこのウィザードのサブスクライバーがパブリッシャーへの接続が確立されると、アカウントを指定する必要があります。 
  
 接続は、サブスクライバーで発生し、パブリッシャーに変更を反映するトリガーで使用されます。 このアカウントは、選択した場合でも、必要 **キューに変更して、コミット可能であれば** 上、 **更新可能なサブスクリプション** ページです。 既定ではサブスクリプションの新規作成ウィザードでは、必要な場合は、即時更新に切り替えることによるキュー更新を構成します。  
  
> **重要!!** 接続にする必要がありますのみに対して指定されたアカウントは、パブリケーション データベース内に作成、挿入、更新、およびビューのデータのレプリケーションを削除する権限を許可します。 その他の権限が与えられません必要があります。 パブリケーション データベースの形式で名前付きのビューに対する権限を与える **syncobj _***\< HexadecimalNumber>* サブスクライバーごとに構成したアカウントにします。  
  
 接続の種類として、3 つのオプションがあります。  
  
-   定義済みのリンク サーバーまたはリモート サーバー。  
  
-   レプリケーションによって作成されるリンク サーバー。このウィザードで指定した資格情報を使用して接続を行います。  
  
-   レプリケーションによって作成されるリンク サーバー。サブスクライバーで変更を行うユーザーの資格情報を使用して接続を行います。  
  
 最初の 2 つのオプションは、このウィザードで指定できます。 使用して、最後のオプションを指定することのみ [sp_link_publication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md)です。値を指定して **1** パラメーター **@security_mode**します。  
  
## オプション  
 **[SQL Server 認証を使用して接続するリンク サーバーを作成する]**  
 レプリケーションで指定された資格情報を使用してリンク サーバーの作成、 **ログイン** と **パスワード** フィールドです。  
  
 **Login**  
 入力、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をこのトピックで説明されているアクセス許可のみを持つログインします。  
  
 **Password**  
 指定されたログインの強力なパスワードを入力 **ログイン**します。  
    
 **[定義済みのリンク サーバーまたはリモート サーバーを使用する]**  
 このオプションを使用するには、定義済みのリンク サーバーまたはリモート サーバーが必要です。 詳細については、次を参照してください。 [リンク サーバーと #40; データベース エンジン、&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md) と [リモート サーバー](../../database-engine/configure-windows/remote-servers.md)します。 リンク サーバーまたはリモート サーバーに使用するログインに対して複雑なパスワードが設定されていて、このトピックに記載された権限だけが設定されていることを確認してください。  
  
## 参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの作成](https://msdn.microsoft.com/library/ms152769.aspx)   
 [レプリケーションのセキュリティ設定の表示および変更](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  