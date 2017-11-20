---
title: "手順 3: レッスン 3 のチュートリアル パッケージのテスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d6477267c95ffd200f70b2c93191dfaf0883a4af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-3-3---testing-the-lesson-3-tutorial-package"></a>レッスン 3-3、レッスン 3 のチュートリアル パッケージのテスト
この実習では、Lesson 3.dtsx パッケージを実行します。 パッケージを実行すると、[ログ イベント] ウィンドウに、ログ ファイルに書き込まれているログ エントリの一覧が表示されます。 パッケージの実行が完了したら、ログ プロバイダーによって生成されたログ ファイルの内容を確認します。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 3 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 2 の制御フローと同じである必要があります。 データ フローはレッスン 1 および 2 のデータ フローと同じである必要があります。  
  
**制御フロー**  
  
![パッケージ内のフローを制御](../integration-services/media/task4lesson2control.gif "パッケージ内のフロー制御")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>レッスン 4 のチュートリアル パッケージを実行するには  
  
1.  [SSIS] メニューの [イベントの記録] をクリックします。  
  
2.  **[デバッグ]** メニューの **[デバッグ開始]**をクリックします。  
  
3.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]**をクリックします。  
  
### <a name="to-examine-the-generated-log-file"></a>生成されたログ ファイルを検証するには  
  
-   メモ帳などのテキスト エディターを使用し、TutorialLog.log ファイルを開きます。  
  
-   **PipelineExecutionPlan** および **PipelineExecutionTrees** イベントで生成される情報の見方については、このチュートリアルでは説明しません。しかし、ログ ファイルの 1 行目には、 **[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブで指定した情報フィールドが一覧表示されます。 また、Foreach ループが繰り返されるたびに、選択した 2 つのイベント、PipelineExecutionPlan および PipelineExecutionTrees が記録されていることも確認できます。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 4: SSIS でエラー フロー リダイレクションを追加する](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  

