---
title: "レプリケーション セキュリティの推奨事項 | Microsoft Docs"
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
  - "セキュリティ [SQL Server レプリケーション], ベスト プラクティス"
  - "セキュリティ [SQL Server レプリケーション], ドメイン間"
  - "認証 [SQL Server レプリケーション]"
  - "インターネット [SQL Server レプリケーション], セキュリティ"
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# レプリケーション セキュリティの推奨事項
  レプリケーションでは、単一ドメインのイントラネットから、信頼できないドメイン間およびインターネット経由でデータにアクセスするアプリケーションに及ぶ分散環境でデータを移動します。 これらのさまざまな状況下でレプリケーション接続のセキュリティを確保するためには、推奨事項を理解することが重要です。  
  
 次の情報は、すべての環境のレプリケーションに関連します。  
  
-   レプリケーション トポロジ内のコンピューター間の接続を、仮想プライベート ネットワーク (VPN)、SSL (Secure Sockets Layer)、IPSEC (IP Secrity) などの業界標準の方式を使用して暗号化する。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。 VPN と SSL を使用して、インターネット経由でのデータをレプリケートする方法の詳細については、次を参照してください。 [、インターネット経由でレプリケーションをセキュリティで保護する](../../../relational-databases/replication/security/securing-replication-over-the-internet.md)です。  
  
     SSL を使用してレプリケーション トポロジ内のコンピューター間の接続をセキュリティで保護する場合の値を指定 **1** または **2** の **-encryptionlevel** 各レプリケーション エージェントのパラメーター (値の **2** をお勧め)。 値 **1** 暗号化を使用するは、エージェントが SSL サーバー証明書が信頼された発行者によって署名されたことを確認していないことを指定の値 **2** 証明書を検証することを指定します。 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
    -   [Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [表示および変更のレプリケーション エージェント コマンド プロンプト パラメーターと #40 です。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
-   異なる Windows アカウントで各レプリケーション エージェントを実行し、すべてのレプリケーション エージェント接続に対して Windows 認証を使用する。 詳細については、アカウントを指定し、次を参照してください。 [レプリケーションの管理のログインとパスワード](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)します。  
  
-   各エージェントに必要な権限のみを許可する。 詳細については、「エージェントにアクセス許可が必要」セクションを参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   マージ エージェントとディストリビューション エージェントのすべてのアカウントがパブリケーション アクセス リスト (PAL) に含まれているかどうかを確認する。 詳細については、次を参照してください。 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)します。  
  
-   最小特権の原則に従って、PAL 内のアカウントに、レプリケーション タスクを実行するために必要な権限のみを許可する。 レプリケーションに必要のない固定サーバー ロールにはログインを追加しないでください。  
  
-   すべてのマージ エージェントおよびディストリビューション エージェントによる読み取りアクセスを許可するようにスナップショット共有を構成する。 パラメーター化されたフィルターを使用するパブリケーションのスナップショットの場合は、適切なマージ エージェント アカウントへのアクセスのみを許可するように各フォルダーを設定してください。  
  
-   スナップショット エージェントによる書き込みアクセスを許可するようにスナップショット共有を構成する。  
  
-   プル サブスクリプションを使用する場合は、スナップショット フォルダーにローカル パスではなく、ネットワーク共有を使用する。  
  
 レプリケーション トポロジに、同じドメイン内に存在しないコンピューター、または相互に信頼関係を持たないドメインに存在するコンピューターが含まれている場合、エージェントが確立する接続には Windows 認証または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用できます (ドメインの詳細については、Windows のマニュアルを参照してください)。 セキュリティの推奨方法としては、Windows 認証の使用をお勧めします。  
  
-   Windows 認証を使用するには  
  
    -   適切なノードで、各エージェントのドメイン アカウントではない、ローカルの Windows アカウントを追加します (各ノードでは同じ名前とパスワードを使用します)。 たとえば、プッシュ サブスクリプションのディストリビューション エージェントをディストリビューターで実行し、ディストリビューターとサブスクライバーに接続しているとします。 この場合、ディストリビューション エージェントの Windows アカウントを、ディストリビューターおよびサブスクライバーに追加する必要があります。  
  
    -   指定されたエージェント (たとえば、サブスクリプションのディストリビューション エージェント) が、各コンピューターで同じアカウントを使用して実行されているかどうかを確認します。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するには  
  
    -   適切なノードで、各エージェントのローカルの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントを追加します (各ノードで同じ名前とパスワードを使用します)。 たとえば、プッシュ サブスクリプションのディストリビューション エージェントをディストリビューターで実行し、ディストリビューターとサブスクライバーに接続しているとします。 この場合、ディストリビューション エージェントの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アカウントを、ディストリビューターおよびサブスクライバーに追加する必要があります。  
  
    -   指定されたエージェント (たとえば、サブスクリプションのディストリビューション エージェント) が、各コンピューターで同じアカウントを使用して接続しているかどうかを確認します。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証が必要な状況では、多くの場合、UNC スナップショット共有へのアクセスは実行できません (たとえば、アクセスがファイアウォールでブロックされます)。 この場合は、ファイル転送プロトコル (FTP) を使用して、スナップショットをサブスクライバーに転送できます。 詳細については、次を参照してください。 [FTP でスナップショットを転送](../../../relational-databases/replication/transfer-snapshots-through-ftp.md)します。  
  
## 参照  
 [データベース エンジンと #40; への暗号化接続を有効にします。SQL Server 構成マネージャーと #41 です。](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)   
 [インターネット経由のレプリケーション](../../../relational-databases/replication/replication-over-the-internet.md)   
 [サブスクライバーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-subscriber.md)   
 [ディストリビューターのセキュリティ保護](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  