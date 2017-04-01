---
title: "[パブリケーションのプロパティ]、[スナップショット] | Microsoft Docs"
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
  - "sql13.rep.newpubwizard.pubproperties.snapshotformat.f1"
ms.assetid: 8e9133b1-fc37-4a85-8a7c-d5eaf172fbef
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# [パブリケーションのプロパティ]、[スナップショット]
   **スナップショット** のページ、 **パブリケーションのプロパティ** ] ダイアログ ボックスでは、スナップショットの形式、スナップショット フォルダーの場所、およびスナップショットの適用の前後に実行するためのスクリプトを設定することができます。 スナップショット フォルダーは、共有として指定する必要があり、エージェントがフォルダーでファイルを読み書きするための十分な権限を持っている必要があります。 詳細については、フォルダーを適切にセキュリティで保護する、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
> [!NOTE]  
>  変更する場合は、パブリケーションの新しいスナップショットが必要です。 詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
## オプション  
 **[スナップショットの形式]**  
 スナップショットの形式にネイティブ モードまたはキャラクター モードを選択します。  
  
-   選択 **ネイティブ SQL Server - すべてのサブスクライバーは SQL Server を実行しているサーバーである必要があります** のインスタンスである場合 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]します。 ネイティブ スナップショットの形式によってパフォーマンスが最適化されます。  
  
-   選択 **文字のかどうかパブリッシャーまたはサブスクライバーが実行されていない SQL Server は必須** すべてのサブスクライバーが実行されている場合 [!INCLUDE[ssEW](../../includes/ssew-md.md)] または非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーです。  
  
 **[スナップショット ファイルの場所]**  
 スナップショット ファイルを格納する場所を選択します。 既定の場所に格納するか、既定の場所ではなく代替位置に格納したり、既定の場所と代替位置の両方に格納したりできます。 代替位置に格納されたファイルは圧縮できます。  
  
-   選択 **既定のフォルダーにファイルを配置** パブリッシャーの既定のスナップショット フォルダーを使用します。 スナップショット フォルダーの場所は、このダイアログ ボックスでは読み取り専用でパブリッシャーにのみ変更できるため、 **ディストリビューターのプロパティ** ] ダイアログ ボックス。 詳細については、次を参照してください。 [指定、既定のスナップショットの場所と #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)します。  
  
-   選択 **次のフォルダーにファイルを配置** の代わりに、または既定の場所に加えて別の場所を指定します。 テキスト ボックスにパスを入力またはクリックして **参照** 場所に移動します。 選択 **このフォルダー内のスナップショット ファイルを圧縮** スナップショットの代替の場所にファイルを圧縮します。 他のサーバー、ネットワーク ドライブ、または CD-ROM やリムーバブル ディスクなどのリムーバブル メディアに代替位置を設定できます。 詳細については、「 [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md) 」および「 [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md)」を参照してください。  
  
 **[追加スクリプトの実行]**  
 サブスクライバーでスナップショットが適用される前後で実行するスクリプトを指定します。 スクリプトを指定できません **スナップショット形式** は **文字**します。  
  
 スクリプトはオプションです。スクリプトを使用すると、サブスクライバーでのコマンドの実行や管理上の変更の適用を容易に行うことができます。 詳細については、スクリプトを実行して、次を参照してください。 [スクリプトの実行前と後のスナップショットが適用される](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)します。  
  
-   パスを入力、 **スナップショットを適用する前に、以下のスクリプトを実行** やテキスト ボックスをクリックして **参照** スクリプトの場所を指定します。  
  
-   パスを入力、 **スナップショットを適用すると、以下のスクリプトを実行** やテキスト ボックスをクリックして **参照** スクリプトの場所を指定します。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [初期スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  