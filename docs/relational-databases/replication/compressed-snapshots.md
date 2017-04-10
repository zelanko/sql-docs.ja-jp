---
title: "圧縮スナップショット | Microsoft Docs"
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
  - "スナップショット [SQL Server レプリケーション], 圧縮"
  - "スナップショット レプリケーション [SQL Server], 圧縮スナップショット"
  - "圧縮スナップショット [SQL Server レプリケーション]"
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# 圧縮スナップショット
  低速なネットワークでスナップショットを転送する場合や、スナップショットをリムーバブル メディアに保存する際にそのままではメディアに収まらない場合は、スナップショット ファイルを圧縮することができます。 スナップショット ファイルを圧縮すると、このような場合に役に立つ反面、スナップショットの生成および適用に要する時間が増大します。  
  
 圧縮スナップショット ファイルは [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB ファイル形式で書き込まれます。このファイル形式では 2 GB 以下のファイルを圧縮できます (スナップショット ファイルのサイズが 2 GB を超える場合は圧縮できません)。 ファイルを圧縮するには、代替スナップショット フォルダーにファイルを書き込む必要があります (既定のスナップショット フォルダーに書き込まれるファイルは圧縮できません)。 代替スナップショット フォルダーの詳細については、次を参照してください。 [代替スナップショット フォルダーの場所](../../relational-databases/replication/alternate-snapshot-folder-locations.md)します。  
  
 ファイルは、ディストリビューション エージェントまたはマージ エージェントが実行されている場所で圧縮解除されます。一般にプル サブスクリプションで圧縮スナップショットを使用する場合、サブスクライバーでファイルの圧縮が解除されるようにします。 サブスクライバーが圧縮ファイルを受信すると、そのファイルは最初は一時的な場所に書き込まれます。 圧縮ファイルがサブスクライバーにコピーされた後、圧縮ファイル内のスナップショット ファイルは CAB ユーティリティによって 1 ファイルずつ順番に圧縮解除されます。 サブスクライバーで必要な空き容量は、圧縮ファイルと圧縮されていない最大のファイルを合計したサイズと同じです。  
  
> [!NOTE]  
>  圧縮スナップショットを使用すると、ネットワーク経由でスナップショット ファイルを移動する際のパフォーマンスが向上する場合があります。 ただし、スナップショットを圧縮すると、スナップショット ファイル生成時のスナップショット エージェント、およびスナップショット ファイル適用時のディストリビューション エージェントまたはマージ エージェントで、追加の処理が必要になります。 これにより、スナップショット生成が遅くなり、スナップショットを適用するための時間が延びることもあります。 また、ネットワークに障害が発生した場合、圧縮スナップショットを復旧することはできません。したがって、信頼性の低いネットワークには向いていません。 ネットワーク経由で圧縮スナップショットを使用するときは、これらのトレードオフを慎重に検討してください。  
  
 **スナップショット ファイルを圧縮および配信するには**  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [圧縮スナップショット ファイルと #40 です。SQL Server Management Studio と #41 です。](../../relational-databases/replication/publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング: [スナップショットのプロパティを構成する (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## 参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット オプション](../../relational-databases/replication/snapshot-options.md)  
  
  