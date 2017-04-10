---
title: "[パブリケーションのプロパティ]、[FTP スナップショットとインターネット] | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1"
ms.assetid: 8e0198c3-5e4e-418c-9920-78ccbbfc1323
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# [パブリケーションのプロパティ]、[FTP スナップショットとインターネット]
  このページで以下の操作を実行できます。  
  
-   ファイル転送プロトコル (FTP) を通じてスナップショットを配信するためのプロパティを設定する。 詳細については、次を参照してください。 [FTP でスナップショットを転送](../../relational-databases/replication/transfer-snapshots-through-ftp.md)します。 スナップショットの配信に FTP を使用するには、FTP サーバーを設定する必要があります。 詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のマニュアルを参照してください。  
  
    > [!NOTE]  
    >  FTP 設定を変更するには、新しいスナップショットを生成する必要があります。  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでのマージ レプリケーションに対して、Web 同期のプロパティを設定して、サブスクリプションを HTTPS (安全なハイパーテキスト転送プロトコル) 経由で同期できるようにする。 Web 同期を使用するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバーを構成する必要があります。 詳細については、次を参照してください。 [マージ レプリケーション用に Web 同期](../../relational-databases/replication/web-synchronization-for-merge-replication.md)です。  
  
## オプション  
 **[FTP 経由でスナップショットにアクセス]**  
 選択 **FTP (ファイル転送プロトコル) を使用してスナップショット ファイルのダウンロードをサブスクライバーに許可**, 、し、指定 **FTP サーバーの名前**, 、**ポート番号**, 、**FTP ルート フォルダーからのパス**, 、**ログイン**, 、および **パスワード**, 、スナップショットの配信に FTP を使用するサブスクライバーを許可するようにします。  
  
 このオプションを選択すると、サブスクライバーは FTP を使用してスナップショット ファイルを取得できますが、この設定は必須ではありません。 このオプションを選択した場合、サブスクリプションの新規作成ウィザードでは、サブスクライバーがスナップショット ファイルを FTP 経由で取得する設定が既定で有効になります。 設定を変更するには、 **サブスクリプションのプロパティ** ] ダイアログ ボックス。 サブスクライバーは FTP でスナップショット ファイルにアクセスを許可する場合は、スナップショット ファイルの場所として FTP フォルダーをを指定、 **スナップショット** のページ、 **パブリケーションのプロパティ** ] ダイアログ ボックス。 これにより、スナップショット エージェントは、新しいスナップショットが生成されたときに FTP フォルダー内のファイルを自動的に更新します。 場所を FTP フォルダーに設定していない場合は、新しいスナップショットが生成されたときにファイルを手動で更新する必要があります。 詳細については、次を参照してください。 [FTP 経由のスナップショットを配信](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)します。  
  
 **[Web 同期]**  
 マージ レプリケーションのみです。 選択 **Web サーバーに接続して同期するサブスクライバーに許可する**, 、Web サーバーのアドレスを許可するように Web 同期を使用するサブスクライバーのマージを指定します。 Web サーバーは、SSL (Secure Sockets Layer) を使用する必要があります。また、Web アドレスは https://server.domain.com/synchronize のように完全修飾である必要があります。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  