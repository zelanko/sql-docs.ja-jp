---
title: "代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# 代替スナップショット フォルダーの場所の指定 (SQL Server Management Studio)
  上の代替スナップショットの場所の指定、 **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### スナップショットの代替位置を指定するには  
  
1.   **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
    1.  選択 **次のフォルダーにファイルを配置**, 、] をクリックし、 **参照** 、ディレクトリに移動したり、スナップショット ファイルを格納するディレクトリ パスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\computername\snapshot です。 詳細については、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
    2.  クリア **既定のフォルダーにファイルを配置** スナップショット ファイルの両方の場所に書き込まれるをする必要がないです。  
  
     スナップショット ファイルを圧縮する選択 **この場所にスナップショット ファイルを圧縮**します。 圧縮は通常、低帯域幅接続を使用する場合や、スナップショットの代替位置をリムーバブル メディア (CD-ROM など) にする場合に使用します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## 参照  
 [スナップショット フォルダーの代替位置](../../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [スナップショットのプロパティと #40; 構成します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [スナップショットの既定の場所と #40; を指定します。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  