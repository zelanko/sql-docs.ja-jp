---
title: "スナップショット適用前および適用後のスクリプトの実行 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スナップショット [SQL Server レプリケーション], スクリプト"
  - "スクリプト [SQL Server レプリケーション], スナップショット"
  - "スナップショット レプリケーション [SQL Server], スクリプト"
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# スナップショット適用前および適用後のスクリプトの実行 (SQL Server Management Studio)
  実行前に、または後に、スナップショットが適用されるオプションのスクリプトを指定、 **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
> [!NOTE]  
>  これらのオプションが表示されない場合、 **スナップショットの形式** にオプションが設定されている **文字**します。  
  
### スナップショット適用前または適用後にスクリプトを実行するには  
  
1.   **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
    -   スナップショットが適用される前に実行するスクリプトを指定する] をクリックして **参照** 、スクリプトを開くか、パス内のスクリプトを入力する、 **スナップショットを適用する前に、以下のスクリプトを実行** テキスト ボックスです。  
  
        > [!NOTE]  
        >  ディストリビューション エージェントまたはマージ エージェントは、指定するディレクトリに対し、読み取り権限を持つ必要があります。 プル サブスクリプションを使用している場合、必要があります、共有ディレクトリを指定汎用名前付け規則 (UNC) パスなど \\\computername\scripts\myscript.sql します。  
  
    -   スナップショットの適用後に実行するスクリプトを指定する] をクリックして **参照** 、スクリプトを開くか、スクリプトに UNC パスを入力する、 **スナップショットを適用すると、以下のスクリプトを実行** テキスト ボックスです。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [スナップショットのプロパティと #40; 構成します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットが適用される前および後のスクリプトの実行](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  