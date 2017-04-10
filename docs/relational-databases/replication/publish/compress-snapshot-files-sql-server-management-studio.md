---
title: "スナップショット ファイルの圧縮 (SQL Server Management Studio) | Microsoft Docs"
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
  - "スナップショット [SQL Server レプリケーション], 圧縮"
  - "スナップショット レプリケーション [SQL Server], 圧縮スナップショット"
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# スナップショット ファイルの圧縮 (SQL Server Management Studio)
  上のファイルを圧縮するかを指定する、 **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### スナップショット ファイルを圧縮するには  
  
1.   **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
    1.  選択 **次のフォルダーにファイルを配置**, 、] をクリックし、 **参照** 、ディレクトリに移動したり、スナップショット ファイルを格納するディレクトリ パスを入力します。  
  
        > [!NOTE]  
        >  スナップショット エージェントには、指定したディレクトリに対する書き込み権限が必要です。また、ディストリビューション エージェントまたはマージ エージェントには、読み取り権限が必要です。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\computername\snapshot します。 詳細については、次を参照してください [スナップショット フォルダーをセキュリティで保護。](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
    2.  クリア **既定のフォルダーにファイルを配置** スナップショット ファイルの両方の場所に書き込まれるをする必要がないです。  
  
        > [!NOTE]  
        >  このチェック ボックスをオンにした場合、既定のフォルダーに格納されたファイルは圧縮されません。 圧縮されたファイルは、上記の手順で別途指定した場所にのみ格納できます。  
  
2.  選択 **このフォルダー内のスナップショット ファイルを圧縮**します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## 参照  
 [スナップショットのプロパティと #40; 構成します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [圧縮スナップショット](../../../relational-databases/replication/compressed-snapshots.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  