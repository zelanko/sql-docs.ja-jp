---
title: "プロジェクトまたはソリューションとしてスクリプトを保存する | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f2e8f9470fe28427a78eb74a41c4e76c400f3761
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-3-3---save-scripts-as-projects-or-solutions"></a>レッスン 3-3 - プロジェクトまたはソリューションとしてスクリプトを保存する
[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio を使い慣れている開発者であれば、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のソリューション エクスプローラーにもすぐに慣れることができます。 業務を支援するスクリプトはスクリプト プロジェクトにグループ化することができ、スクリプト プロジェクトはソリューションとしてまとめて管理できます。 スクリプト プロジェクトまたはソリューションに格納したスクリプトは、グループとして一括して開けるほか、Visual SourceSafe などのソース管理製品にまとめて保存することができます。 スクリプト プロジェクトは、スクリプトを適切に実行するための接続情報を保持し、テキスト ファイルなどの非スクリプト ファイルを保持することもできます。  
  
次の実習では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにクエリを実行する短いスクリプトを作成し、スクリプト プロジェクトとソリューションに格納します。  
  
## <a name="using-script-projects-and-solutions"></a>スクリプト プロジェクトとソリューションの使用  
  
#### <a name="to-create-a-script-project-and-solution"></a>スクリプト プロジェクトとソリューションを作成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開き、オブジェクト エクスプローラーを使用してサーバーに接続します。  
  
2.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。 **[新しいプロジェクト]** ダイアログ ボックスが開きます。  
  
3.  **[名前]** ボックスに「 **StatusCheck**」と入力し、 **[テンプレート]** で **[SQL Server スクリプト]**をクリックして、 **[OK]** をクリックします。新しいソリューションとスクリプト プロジェクトが開きます。  
  
4.  ソリューション エクスプローラーで **[接続]**を右クリックし、 **[新しい接続]**をクリックします。 **[サーバーへの接続]** ダイアログ ボックスが開きます。  
  
5.  **[サーバー名]** ボックスにサーバー名を入力します。  
  
6.  **[オプション]**をクリックし、 **[接続プロパティ]** タブをクリックします。  
  
7.  **[データベースへの接続]** ボックスで [サーバーの参照] をクリックし、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを選択して、 **[接続]**をクリックします。 指定したデータベースを含む接続情報がプロジェクトに追加されます。  
  
8.  [プロパティ] ウィンドウが表示されない場合は、ソリューション エクスプローラーで新しい接続をクリックし、F4 キーを押します。 接続のプロパティが表示され、 **初期データベース** が [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]であることなどの接続情報が示されます。  
  
9. ソリューション エクスプローラーで接続を右クリックし、 **[新しいクエリ]**をクリックします。 **SQLQuery1.sql** という名前の新しいクエリが作成され、サーバー上の [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに接続されます。さらに、スクリプト プロジェクトにこのクエリが追加されます。  
  
10. クエリ エディターに次のクエリを入力します。ここでは、期限が設けられており、まだ開始日に至っていない作業命令の数を調べます (チュートリアル ウィンドウからコードをコピーして、貼り付けることができます)。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    > クエリを入力するスペースが足りない場合は、Shift + Alt + Enter キーを押して全画面モードに切り替えてください。  
  
11. ソリューション エクスプローラーで **SQLQuery1**を右クリックし、 **[名前の変更]**をクリックします。 クエリの新しい名前として「 **Check Workorders****.sql** 」と入力し、Enter キーを押します。  
  
12. ソリューションとスクリプト プロジェクトを保存するには、 **[ファイル]** メニューの **[すべてを保存]**をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[まとめ : ソリューションとスクリプト プロジェクト](../../tools/sql-server-management-studio/lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
  
