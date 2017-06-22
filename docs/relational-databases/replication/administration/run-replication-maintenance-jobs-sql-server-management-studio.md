---
title: "レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3870cd3f172e7d24d99fe58867353311bb00e500
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio)
  レプリケーションでは以下のメンテナンス ジョブを使用します。  
  
-   **データ検証で問題が見つかったサブスクリプションの再初期化**  
  
-   **エージェント履歴のクリーンアップ: ディストリビューション**  
  
-   **ディストリビューションのレプリケーション モニターの状態更新機能**  
  
-   **レプリケーション エージェントの検査**  
  
-   **ディストリビューションのクリーンアップ: ディストリビューション**  
  
-   **有効期限が切れたサブスクリプションのクリーンアップ**  
  
 上記のジョブの開始および停止は、 **** の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] and from the **Agents** tab in Replication Monitor. レプリケーション モニターの開始の詳細については、「[レプリケーション モニターの開始](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)」を参照してください。 各ジョブのプロパティの表示および変更は、同じフォルダーおよびタブからアクセスできる **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで行います。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Management Studio でレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]**をクリックします。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>レプリケーション モニターでレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  **[エージェント]** タブをクリックします。  
  
3.  グリッド内のジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]**をクリックします。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Management Studio でレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、 **[プロパティ]**をクリックします。  
  
4.  **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで、必要に応じてプロパティを変更し、**[OK]** をクリックします。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>レプリケーション モニターでレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  **[エージェント]** タブをクリックします。  
  
3.  グリッド内のジョブを右クリックし、 **[プロパティ]**をクリックします。  
  
4.  **[ジョブのプロパティ - \<Job>]** ダイアログ ボックスで、必要に応じてプロパティを変更し、**[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [パブリッシャーの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
