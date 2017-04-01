---
title: "[スナップショット フォルダー] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replicationutilities.specifysnapshotfolder.f1"
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# [スナップショット フォルダー]
   **スナップショット フォルダー** ディストリビューションの構成ウィザードとパブリケーションの新規作成ウィザードにページが表示されます。 このウィザードで有効なすべてのパブリッシャーの既定値として使用されるスナップショット フォルダー用に指定した場所 (既定のスナップショット フォルダーを使用して後で有効になっているパブリッシャーには適用されません、 **ディストリビューターのプロパティ** ] ダイアログ ボックス)。 任意のパブリッシャーに対してこの既定をオーバーライドできる、 **パブリッシャー** ディストリビューションの構成ウィザードのページまたは **ディストリビューターのプロパティ** ] ダイアログ ボックス。  
  
 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 詳細については、フォルダーを適切にセキュリティで保護する、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。 レプリケーションを実装する前に、レプリケーション エージェントがスナップショット フォルダーに接続できることをテストします。 各エージェントで使用されるアカウントを使用してログオンした後、スナップショット フォルダーへのアクセスを試行します。  
  
## オプション  
 **[スナップショット フォルダー]**  
 スナップショット ファイルを保存するフォルダーのパスを入力します。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] スナップショット フォルダーの場所には、ネットワーク共有を使用することをお勧めします。 ローカル パス (c: などのドライブ文字で始まる\\) は、他のコンピューター上のエージェントにアクセスできません。  
  
## 参照  
 [スナップショット フォルダーの代替位置](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)   
 [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  