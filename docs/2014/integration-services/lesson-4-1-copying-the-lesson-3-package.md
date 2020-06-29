---
title: '手順 1: レッスン 3 のパッケージのコピー | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1645a1dee923da3913d12e36bdd60829918bbf7b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440479"
---
# <a name="step-1-copying-the-lesson-3-package"></a>手順 1:レッスン 3 のパッケージのコピー
  ここでは、レッスン 3 で作成した Lesson 3.dtsx パッケージのコピーを作成します。 レッスン 3 を終了していない場合は、チュートリアルに含まれている、レッスン 3 を完了した状態のパッケージをプロジェクトに追加し、作業用のコピーを作成することもできます。 レッスン 4 の実習では、このパッケージの新しいコピーを使用します。  
  
### <a name="to-create-the-lesson-4-package"></a>レッスン 4 のパッケージを作成するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]** の順にポイントして、 **[SQL Server Data Tools]** をクリックします。  
  
2.  [**ファイル**] メニューの [**開く**] をクリックし、[**プロジェクト/ソリューション**] をクリックします。次に、[ **ssis チュートリアル**] を選択し、[**開く**] をクリックして、[ **ssis チュートリアル. .sln**] をダブルクリックします。  
  
3.  ソリューション エクスプローラーで、 **Lesson 3.dtsx**を右クリックし、 **[コピー]** をクリックします。  
  
4.  ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**貼り付け**] をクリックします。  
  
     コピーしたパッケージの既定の名前は、Lesson 4.dtsx です。  
  
5.  ソリューション エクスプローラーで **Lesson 4.dtsx** をダブルクリックし、パッケージを開きます。  
  
6.  **[制御フロー]** タブの背景上で任意の場所を右クリックし、 **[プロパティ]** をクリックします。  
  
7.  プロパティウィンドウで、 `Name` プロパティをに更新し `Lesson 4` ます。  
  
8.  **[ID]** プロパティのボックスをクリックし、一覧で **[\<Generate New ID>]** をクリックします。  
  
### <a name="to-add-the-completed-lesson-3-package"></a>レッスン 3 を完了した状態のパッケージを追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を開いて、SSIS Tutorial プロジェクトを開きます。  
  
2.  ソリューションエクスプローラーで、[ **SSIS パッケージ**] を右クリックし、[**既存のパッケージの追加**] をクリックします。  
  
3.  [**既存のパッケージのコピーを追加**] ダイアログボックスの [**パッケージの場所**] で、[**ファイルシステム**] を選択します。  
  
4.  参照ボタン **([...])** をクリックし、コンピューターの .dtsx に移動して、[**開く**] をクリックします。  
  
     このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  [**ダウンロード**] タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 2:破損ファイルの作成](lesson-4-2-creating-a-corrupted-file.md)  
  
  
