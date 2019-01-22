---
title: 手順 1:レッスン 3 のパッケージのコピー | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ba011dbb600ca2903aca6f9a3c6415f4663aea0a
ms.sourcegitcommit: e2fa721b6f46c18f1825dd1b0d56c0a6da1b2be1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54211073"
---
# <a name="lesson-4-1-copy-the-lesson-3-package"></a>レッスン 4-1: レッスン 3 のパッケージをコピーする

ここでは、レッスン 3 で作成した Lesson 3.dtsx パッケージのコピーを作成します。 レッスン 3 を終了していない場合は、チュートリアルに含まれている、レッスン 3 を完了した状態のパッケージをプロジェクトに追加し、作業用のコピーを作成することもできます。 レッスン 4 の実習では、このパッケージの新しいコピーを使用します。  
  
## <a name="create-the-lesson-4-package"></a>レッスン 4 のパッケージを作成する  
  
完了したレッスン 3 をコピーする場合は、この手順を使用します。  レッスン 3 のサンプルをコピーするには、次のセクションを参照してください。

1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、**[開始]** > **[すべてのプログラム]** > **[Microsoft SQL Server 2017]** の順に選択し、次に **[SQL Server Data Tools]** を選択します。

2.  **[ファイル]** メニューで、**[開く]** > **[プロジェクト/ソリューション]** の順に選択し、**[SSIS Tutorial]** フォルダーを選択し、**[開く]** を選択してから、**[SSIS Tutorial.sln]** をダブルクリックします。

3.  **ソリューション エクスプローラー**で、**Lesson 3.dtsx** を右クリックし、**[コピー]** を選択します。

4.  **ソリューション エクスプローラー**で、**[SSIS パッケージ]** を右クリックし、**[貼り付け]** を選択します。

    コピーしたパッケージの既定の名前は、**Lesson 4.dtsx** です。

5.  **ソリューション エクスプローラー**で **Lesson 4.dtsx** をダブルクリックし、パッケージを開きます。

6.  **[制御フロー]** デザイン画面の背景上で任意の場所を右クリックし、**[プロパティ]** を選択します。

7.  **[プロパティ]** ウィンドウで、**[Name]** プロパティを「**Lesson 4**」に変更します。

8.  **ID** プロパティのボックスを選択し、ドロップダウン矢印を選択し、**[\<新しい ID の生成>]** を選択します。

## <a name="add-the-completed-lesson-3-package"></a>レッスン 3 を完了した状態のパッケージを追加する

1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools を開き、SSIS Tutorial プロジェクトを開きます。

2.  **ソリューション エクスプローラー**で **[SSIS パッケージ]** を右クリックし、**[既存のパッケージを追加]** を選択します。

3.  **[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]** で、 **[ファイル システム]** をクリックします。

4.  参照ボタン **[...]** を選択し、ご利用のコンピューター上の **Lesson 3.dtsx** に移動して、**[開く]** を選択します。

5.  前のセクションの手順 3 から 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。

  
## <a name="go-to-next-task"></a>次の実習に進む  
[手順 2: 破損したファイルを作成する](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
