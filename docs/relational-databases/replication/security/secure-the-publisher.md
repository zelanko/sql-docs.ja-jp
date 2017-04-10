---
title: "パブリッシャーのセキュリティ保護 | Microsoft Docs"
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
  - "logins [SQL Server replication], publication access list"
  - "publications [SQL Server replication], publication access lists"
  - "publication access list (PAL)"
  - "PAL (パブリケーション アクセス リスト)"
  - "パブリッシャー [SQL Server レプリケーション], セキュリティ"
  - "パブリケーション [SQL Server レプリケーション], セキュリティ"
ms.assetid: 4513a18d-dd6e-407a-b009-49dc9432ec7e
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# パブリッシャーのセキュリティ保護
  次のレプリケーション エージェントはパブリッシャーに接続します。  
  
-   ログ リーダー エージェント (Log Reader Agent)  
  
-   スナップショット エージェント  
  
-   キュー リーダー エージェント (Queue Reader Agent)  
  
-   マージ エージェント  
  
 最低限必要な権限のみを与え、かつ、すべてのパスワードの格納を保護するという原則に従って、これらの各エージェントに対し適切なログインを提供することをお勧めします。 各エージェントに必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
 ログインとパスワードの適切な管理以外にも、パブリケーション アクセス リスト (PAL) の役割を理解しておく必要があります。 PAL は、パブリッシャーのデータベースへのアドホック アクセスを制限すると同時に、ログインしてパブリケーション データへのアクセスを可能にするために使用されます。  
  
## パブリケーション アクセス リスト  
 PAL は、パブリッシャーでパブリケーションの安全を確保する主要なメカニズムです。 PAL は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のアクセス制御リストによく似た機能を備えています。 パブリケーションを作成すると、レプリケーションによってそのパブリケーションから PAL が作成されます。 PAL は、パブリケーションへのアクセスを許可されているログインとグループのリストを含めるように構成できます。 エージェントがパブリッシャーまたはディストリビューターに接続し、パブリケーションへのアクセスを要求すると、PAL 内の認証情報が、エージェントによって提供されるパブリッシャー ログインと比較されます。 このプロセスでは、クライアント ツールがパブリッシャーとディストリビューターのログインを使用してパブリッシャー側で直接変更を行う危険性を回避できるので、パブリッシャーのセキュリティを向上できます。  
  
> [!NOTE]  
>  PAL のメンバーに含めるため、レプリケーションによって、各パブリケーションに対してパブリッシャー上にロールが作成されます。 ロールは、フォームの名前を持って **Msmerge_***\< PublicationID>* マージ レプリケーションと **msreplpal _***\< PublicationDatabaseID>***_***\< PublicationID>* トランザクション レプリケーションとスナップショット レプリケーション。  
  
 既定では、以下のログインが PAL に含まれる: のメンバー、 **sysadmin** 固定サーバー ロールは、パブリケーションの作成時と文書の作成に使用されるログイン。 既定では、すべてのログイン メンバーであるは **sysadmin** 固定サーバー ロールまたは **db_owner** パブリケーション データベースの固定データベース ロールが明示的に PAL に追加しなくても、パブリケーションにサブスクライブできます。  
  
 PAL を使用する場合は、次のガイドラインを考慮してください。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインを PAL に追加する前に、そのログインをパブリケーション データベースのデータベース ユーザーに関連付ける必要があります。  
  
-   最小特権の原則に従って、PAL 内のログインに、レプリケーション タスクを実行するために必要な権限のみを許可します。 レプリケーションに必要のない固定データベース ロールやサーバー ロールに、ログインを追加しないでください。 必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md) と [レプリケーション セキュリティのベスト プラクティス](../../../relational-databases/replication/security/replication-security-best-practices.md)します。  
  
-   リモート ディストリビューターを使用する場合、PAL 内のアカウントは、パブリッシャーとディストリビューターの両方で使用できる必要があります。 このアカウントは、どちらのサーバーでも定義されているドメイン アカウントまたはローカル アカウントにする必要があります。 両方のログインに関連付けられているパスワードは、同じにする必要があります。  
  
-   PAL に Windows アカウントが含まれており、ドメインで Active Directory が使用されている場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行する際に使用するアカウントが Active Directory から読み取りを行う権限を持っている必要があります。 Windows アカウントに関する問題が発生した場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行する際に使用するアカウントが十分な権限を持っていることを確認します。 詳細については、Windows のマニュアルを参照してください。  
  
 PAL を管理するには、次を参照してください。 [パブリケーション アクセス リストのログインを管理](../../../relational-databases/replication/security/manage-logins-in-the-publication-access-list.md)します。  
  
## スナップショット エージェント  
 パブリケーションごとに 1 つのスナップショット エージェントがあります。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
## FTP スナップショット配信  
 UNC 共有ではなく FTP 共有によりスナップショットを使用できるように指定する場合、FTP アクセスの構成時にログインおよびパスワードを指定する必要があります。 詳細については、次を参照してください。 [FTP 経由のスナップショットを配信](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)します。  
  
## ログ リーダー エージェント (Log Reader Agent)  
 トランザクション レプリケーション用にパブリッシュされるデータベースには、それぞれ 1 つのログ リーダー エージェントがあります。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
## キュー リーダー エージェント (Queue Reader Agent)  
 あるディストリビューターに関連付けられたすべてのパブリッシャーおよびパブリケーション (キュー更新サブスクリプションを許可するパブリケーション) に対し、1 つのキュー リーダー エージェントがあります。 詳細については、次を参照してください。 [トランザクション パブリケーションのサブスクリプションの更新を有効にする](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)です。  
  
## 参照  
 [データベース エンジンと #40; への暗号化接続を有効にします。SQL Server 構成マネージャーと #41 です。](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  