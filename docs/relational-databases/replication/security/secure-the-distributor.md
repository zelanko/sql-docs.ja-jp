---
title: "ディストリビューターのセキュリティ保護 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セキュリティ [SQL Server レプリケーション], ディストリビューター"
  - "ディストリビューター [SQL Server レプリケーション], セキュリティ"
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# ディストリビューターのセキュリティ保護
  レプリケーション エージェントのうち、ログ リーダー エージェント、スナップショット エージェント、キュー リーダー エージェント、ディストリビューション エージェント、およびマージ エージェントは、ディストリビューターに接続します。 最低限必要な権限のみを与え、かつすべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを指定することは重要です。  
  
-   ログインとパスワードを管理する方法の詳細については、次を参照してください。 [レプリケーションの管理のログインとパスワード](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)します。  
  
-   各エージェントに必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
 ログインとパスワードを適切に管理するだけでなくの役割を理解しておく、 **repl_distributor** リモート サーバーへのリンク、および **distributor_admin** アカウントです。  
  
## パブリッシャーからディストリビューターへの接続の保護  
 通信をサポートするために必要な管理用のストアド プロシージャの実行で、ディストリビューターでパブリッシャーと更新プログラムの情報と、レプリケーションに自動的にサーバーを構成、リモート **repl_distributor**します。  **Repl_distributor** リモート サーバー エントリがディストリビューション データベースのパブリッシャー インスタンス (ローカル ディストリビューター) 内に含まれるか、または、リモート存在しているかどうかに関係なく、ディストリビューション データベースへの通信に使用される [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス (リモート ディストリビューター)。  
  
 ディストリビューション データベースがローカル インスタンスに含まれる場合は、ランダムなパスワードが生成され自動的に構成されます。 管理者は、パブリッシャーとディストリビューターのセットアップ時に、共有パスワードを構成、ディストリビューション データベースがリモート インスタンスに配置されている場合このパスワードを通過するトラフィックの認証に使用し、 **repl_distributor** リンクします。  
  
 ディストリビューターを使用して、 **repl_distributor** 実行中にストアド プロシージャを呼び出し元のサーバーにディストリビューターでパブリッシャーとして構成し、発行元によって指定されたパスワードを検証し、ストアド プロシージャがレプリケーションであることを検証ことを確認するリモート サーバー エントリです。  
  
 用に構成されたパスワード、 **repl_distributor** セットアップ中にリモート サーバー エントリに関連付けられて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログイン、 **distributor_admin**, に追加する、 **sysadmin** 、ディストリビューター側の固定サーバー ロールです。  **Distributor_admin** ディストリビューターに接続するときに、レプリケーション ストアド プロシージャによってログインが使用されます。  
  
> [!NOTE]  
>  パスワードは変更しないで、 **distributor_admin** 手動でします。 常に使用する、 **sp_changedistributor_password** ストアド プロシージャ、または **ディストリビューターのプロパティ** または **レプリケーション パスワードの更新** のダイアログ ボックス [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], 、パスワードは、ローカルに適用されているパブリケーションの変更を自動的にします。  
  
## スナップショット フォルダーのセキュリティ  
 スナップショット共有には、マージ エージェント (マージ レプリケーションの場合) またはディストリビューション エージェント (スナップショット レプリケーションまたはトランザクション レプリケーションの場合) の実行に使用するアカウントに読み取りアクセスが許可され、スナップショット エージェントの実行に使用するアカウントに書き込みアクセスが許可されていることを確認してください。 スナップショット フォルダーの詳細については、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
## 参照  
 [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [データベース エンジンと #40; への暗号化接続を有効にします。SQL Server 構成マネージャーと #41 です。](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  