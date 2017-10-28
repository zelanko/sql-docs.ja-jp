---
title: "ジョブ ステップ情報の表示 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 11d5bd90cbe853d287dc0b20c6f036a0000f0355
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="view-job-step-information"></a>ジョブ ステップ情報の表示
このトピックでは、[ジョブ ステップのプロパティ] ダイアログ ボックスにジョブ ステップの詳細を表示する方法について説明します。 さらに、ジョブ ステップの出力の表示についても説明します。  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **ジョブ ステップの情報を表示する方法:**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
テーブルまたはファイルに出力を書き込むようにジョブ ステップが構成され、ジョブが 1 回でも実行されている場合は、 **[ジョブ ステップのプロパティ]** ダイアログ ボックスの **[詳細設定]** ページでジョブ ステップの出力を表示できます。 ジョブまたはジョブ ステップが削除されると、出力ログは自動的に削除されます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバー以外は、所有するジョブしか表示できません。 このロールのメンバーは、すべてのジョブとジョブ ステップの詳細を表示できます。  
  
## <a name="SSMS"></a>SQL Server Management Studio の使用  
  
#### <a name="to-view-job-step-information"></a>ジョブ ステップの情報を表示するには  
  
1.  **オブジェクト エクスプローラー** で、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[SQL Server エージェント]**、 **[ジョブ]**の順に展開し、表示するジョブ ステップが含まれているジョブを右クリックします。次に、 **[プロパティ]**をクリックします。  
  
3.  **[ジョブのプロパティ]** ダイアログ ボックスで、 **[ステップ]** ページをクリックします。  
  
4.  表示するジョブ ステップをクリックし、 **[編集]**をクリックします。  
  
5.  **[ジョブ ステップのプロパティ]** ダイアログ ボックスの **[全般]** ページで、ジョブ ステップの種類や説明を表示できます。  
  
6.  **[詳細設定]** ページをクリックすると、ジョブ ステップが正常終了または異常終了した場合に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって行われる操作、ジョブ ステップの試行回数、ジョブ ステップの出力の書き込み先、およびジョブ ステップを実行するユーザーが表示されます。  
  
#### <a name="to-view-job-step-output"></a>ジョブ ステップの出力を表示するには  
  
1.  **[ジョブ ステップのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** ページをクリックします。  
  
2.  接続している [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のバージョンに応じて、ジョブ ステップの出力ファイルまたは出力テーブルのいずれかを次のように表示できます。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 以降に接続しているときは、 **[テーブルにログ記録する]** チェック ボックスがオンになっている場合のみ **[表示]** をクリックできます。 この場合、 **msdb** データベースの **sysjobstepslogs** テーブルにジョブ ステップの出力が書き込まれます。  
  
    -   ジョブ ステップの出力がファイルに書き込まれるときは **[表示]** ボタンが無効になります。 ジョブ ステップの出力ファイルを表示するには、メモ帳を使用します。  
  

