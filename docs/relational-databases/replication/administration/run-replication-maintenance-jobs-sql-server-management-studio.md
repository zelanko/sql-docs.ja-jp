---
title: "レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio) | Microsoft Docs"
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
  - "ジョブ [SQL Server レプリケーション]"
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio)
  レプリケーションでは以下のメンテナンス ジョブを使用します。  
  
-   **データ検証で問題が見つかったサブスクリプションの再初期化**  
  
-   **エージェント履歴のクリーンアップ: ディストリビューション**  
  
-   **ディストリビューションのレプリケーション モニターの状態更新機能**  
  
-   **レプリケーション エージェントの検査**  
  
-   **ディストリビューションのクリーンアップ: ディストリビューション**  
  
-   **有効期限が切れたサブスクリプションのクリーンアップ**  
  
 開始および停止からこれらのジョブ、 **ジョブ** フォルダーに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] との間、 **エージェント** レプリケーション モニターでタブをクリックします。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。 内の各ジョブのプロパティ表示して、 **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスは、同じフォルダーおよびタブから利用可能です。  
  
### Management Studio でレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、をクリックし、 **ジョブの開始** または **ジョブの停止**します。  
  
### レプリケーション モニターでレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  クリックして、 **エージェント** ] タブをクリックします。  
  
3.  グリッドで、ジョブを右クリックし、 **ジョブの開始** または **ジョブの停止**します。  
  
### Management Studio でレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、をクリックし、 **プロパティ**します。  
  
4.   **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスで、必要に応じてプロパティを変更し、 **OK**します。  
  
### レプリケーション モニターでレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  クリックして、 **エージェント** ] タブをクリックします。  
  
3.  グリッドで、ジョブを右クリックし、 **プロパティ**します。  
  
4.   **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスで、必要に応じてプロパティを変更し、 **OK**します。  
  
## 参照  
 [開始および停止レプリケーション エージェントと #40 です。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [情報を表示し、パブリッシャーおよび #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  