---
title: "スナップショット フォルダーの代替位置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット [SQL Server レプリケーション], 代替フォルダーの場所"
  - "スナップショット レプリケーション [SQL Server], 代替フォルダーの場所"
  - "代替スナップショット フォルダー [SQL Server レプリケーション]"
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# スナップショット フォルダーの代替位置
  スナップショットの代替位置を使用すると、既定の場所 (通常はディストリビューター上) 以外の場所、または既定の場所に加えて別の場所にスナップショット ファイルを格納できます。 代替位置には、別のサーバー、ネットワーク ドライブ、またはリムーバブル メディア (CD-ROM またはリムーバブル ディスクなど) を指定できます。  
  
 スナップショットの代替位置は、パブリケーションのプロパティとして格納されます。 スナップショットの代替位置はパブリケーション プロパティであるため、ディストリビューション エージェントおよびマージ エージェントは同期処理の過程で適切なスナップショットを見つけることができます。  
  
 代替スナップショット フォルダーを指定する必要がある場合、またはスナップショット ファイルを圧縮する必要がある場合には、パブリケーションの作成時に即座に初期スナップショットを作成せず、スナップショットの場所に関するパブリケーションのプロパティを設定してから、そのパブリケーションにスナップショット エージェントを実行してください。 初期スナップショットの作成後に代替位置を変更した場合、パブリケーションに対して生成されたすべてのスナップショットは、新しい代替位置には再配置されません。 この場合、パブリケーションの設定に応じて、マージ エージェントとディストリビューション エージェントが新しい代替位置でスナップショット ファイルを見つけることができなくなる可能性があります。  
  
> [!NOTE]  
>  別の場所を指定しない (を使用して、 **パブリケーションのプロパティ** ] ダイアログ ボックスまたは [sp_changepublication & #40 です。Transact-SQL と #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md))スナップショット フォルダーの既定の場所と同じです。  
  
> [!CAUTION]  
>  WebSync と代替スナップショット フォルダーの場所を同時に使用しないでください。  
  
 **スナップショットの代替位置を指定するには**  
  
-   [!含める [ssManStudioFull] (../Token/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/publish/specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   レプリケーション [!INCLUDE[tsql](../../includes/tsql-md.md)] プログラミング: [スナップショットのプロパティを構成する (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## 参照  
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [スナップショット オプション](../../relational-databases/replication/snapshot-options.md)  
  
  