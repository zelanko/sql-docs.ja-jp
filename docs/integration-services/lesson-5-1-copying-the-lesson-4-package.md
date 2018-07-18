---
title: '手順 1: レッスン 4 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 8aa7d690-4649-4c0a-ac6f-9504637ee426
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1a4ff0d81fb600fd41dc1e0edc6811078e957d66
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411194"
---
# <a name="lesson-5-1---copying-the-lesson-4-package"></a>レッスン 5-1 - レッスン 4 のパッケージのコピー
ここでは、レッスン 4 で作成した Lesson 4.dtsx パッケージのコピーを作成します。 または、チュートリアルに含まれている、レッスン 4 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。 レッスン 5 の実習では、このパッケージの新しいコピーを使用します。  
  
### <a name="to-copy-the-lesson-4-package"></a>レッスン 4 のパッケージをコピーするには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]** をクリックし、 **[プロジェクト/ソリューション]** をクリックします。次に、 **[SSIS Tutorial]** フォルダーをクリックして **[開く]** をクリックした後、 **SSIS Tutorial.sln**をダブルクリックします。  
  
3.  ソリューション エクスプローラーで、 **Lesson 4.dtsx**を右クリックし、 **[コピー]** をクリックします。  
  
4.  ソリューション エクスプローラーで **[SSIS パッケージ]** を右クリックし、 **[貼り付け]** をクリックします。  
  
    コピーしたパッケージの既定の名前は、Lesson 5.dtsx です。  
  
5.  ソリューション エクスプローラーで **Lesson 5.dtsx** をダブルクリックして、このパッケージを開きます。  
  
6.  **[制御フロー]** タブの背景上で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
7.  [プロパティ] ウィンドウで、 **[Name]** プロパティを「 **Lesson 5**」に変更します。  
  
8.  **[ID]** プロパティのボックスをクリックし、ドロップダウン矢印をクリックし、 **<Generate New ID>** をクリックします。  
  
### <a name="to-add-the-completed-lesson-4-package"></a>レッスン 4 を完了した状態のパッケージを追加するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools を開き、SSIS Tutorial プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで **[SSIS パッケージ]** を右クリックし、**[既存のパッケージを追加]** をクリックします。  
  
3.  **[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。  
  
4.  参照ボタン ( **[…]** ) をクリックし、コンピューター上の **Lesson 4.dtsx** に移動して、 **[開く]** をクリックします。  
  
    このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。  
  
    1.  「[Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  **[ダウンロード]** タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  前の手順の手順 3 ～ 8 の説明に従って、レッスン 4 パッケージをコピーして貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2 : パッケージ構成の有効化と構成](../integration-services/lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
