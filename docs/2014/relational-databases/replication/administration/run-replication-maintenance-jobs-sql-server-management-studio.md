---
title: レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 74c00479e5587c8662d81e554cae5add2e295183
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068758"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>レプリケーション メンテナンス ジョブの実行 (SQL Server Management Studio)
  レプリケーションでは以下のメンテナンス ジョブを使用します。  
  
-   **データ検証で問題が見つかったサブスクリプションの再初期化**
-   **エージェント履歴のクリーンアップ: ディストリビューション**
-   **ディストリビューションのレプリケーション モニターの状態更新機能**
-   **レプリケーション エージェントの検査**
-   **ディストリビューションのクリーンアップ: ディストリビューション**
-   **有効期限が切れたサブスクリプションのクリーンアップ**  
  
 上記のジョブの開始および停止は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[ジョブ]** フォルダー、およびレプリケーション モニターの **[エージェント]** タブから行います。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。 各ジョブのプロパティを表示および変更するには、[**ジョブのプロパティ- \<Job> ** ] ダイアログボックスを使用します。このダイアログボックスは、同じフォルダーおよびタブから使用できます。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Management Studio でレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]** をクリックします。  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>レプリケーション モニターでレプリケーション メンテナンス ジョブを開始または停止するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  **[エージェント]** タブをクリックします。  
  
3.  グリッド内のジョブを右クリックして **[ジョブの開始]** または **[ジョブの停止]** をクリックします。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Management Studio でレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  [**ジョブのプロパティ- \<Job> ** ] ダイアログボックスで、必要に応じてプロパティを変更し、[ **OK**] をクリックします。  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>レプリケーション モニターでレプリケーション メンテナンス ジョブのプロパティを表示および変更するには  
  
1.  レプリケーション モニターでパブリッシャー グループを展開し、パブリッシャーを選択します。  
  
2.  **[エージェント]** タブをクリックします。  
  
3.  グリッド内のジョブを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  [**ジョブのプロパティ- \<Job> ** ] ダイアログボックスで、必要に応じてプロパティを変更し、[ **OK**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーションエージェント &#40;SQL Server Management Studio を開始および停止する&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [レプリケーションモニターを使用して情報を表示し、タスクを実行する](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [レプリケーション エージェントの管理](../agents/replication-agent-administration.md)  
  
  
