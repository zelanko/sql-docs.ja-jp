---
title: "手順 1: レッスン 2 のパッケージのコピー | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d805e07ffbdf1cf5685ebcf20dc63dae5652ca7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-3-1---copying-the-lesson-2-package"></a>レッスン 3-1 - レッスン 2 のパッケージのコピー
ここでは、レッスン 2 で作成した Lesson 2.dtsx パッケージのコピーを作成します。 または、チュートリアルに含まれている、レッスン 2 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。 レッスン 3 の実習では、このパッケージの新しいコピーを使用します。  
  
### <a name="to-create-the-lesson-3-package"></a>レッスン 3 のパッケージを作成するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、**[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[Microsoft SQL Server 2012]** の順にポイントして、**[SQL Server Data Tools]** をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]**をクリックし、 **[プロジェクト/ソリューション]**をクリックします。次に、 **[SSIS Tutorial]** フォルダーをクリックして **[開く]**をクリックした後、 **SSIS Tutorial.sln**をダブルクリックします。  
  
3.  ソリューション エクスプローラーで、 **Lesson 2.dtsx**を右クリックし、 **[コピー]**をクリックします。  
  
4.  ソリューション エクスプローラーで **[SSIS パッケージ]** を右クリックし、**[貼り付け]** をクリックします。  
  
    コピーしたパッケージの既定の名前は、Lesson 3.dtsx です。  
  
5.  ソリューション エクスプローラーで **Lesson 3.dtsx** をダブルクリックし、パッケージを開きます。  
  
6.  **[制御フロー]** タブの背景上で任意の場所を右クリックし、 **[プロパティ]**をクリックします。  
  
7.  [プロパティ] ウィンドウで、**[Name]** プロパティを「**Lesson 3**」に変更します。  
  
8.  **[ID]** プロパティのボックスをクリックし、一覧で **[<Generate New ID>]** をクリックします。  
  
### <a name="to-add-the-completed-lesson2-package"></a>レッスン 2 を完了した状態のパッケージを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を開いて、SSIS Tutorial プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで **[SSIS パッケージ]**を右クリックし、 **[既存のパッケージを追加]**をクリックします。  
  
3.  **[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]**で、 **[ファイル システム]**をクリックします。  
  
4.  参照ボタン ( **[...]** ) をクリックし、コンピューター上の **Lesson 2.dtsx** に移動して、 **[開く]**をクリックします。  
  
    このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。  
  
    1.  「[Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  **[ダウンロード]** タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2:ログ機能の追加と設定](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
