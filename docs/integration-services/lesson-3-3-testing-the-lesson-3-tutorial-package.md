---
title: 手順 3:レッスン 3 のチュートリアル パッケージのテスト | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 31f08374ad46929c52305cb6558b603a03b439bd
ms.sourcegitcommit: dd794633466b1da8ead9889f5e633bdf4b3389cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54143342"
---
# <a name="lesson-3-3-test-the-lesson-3-tutorial-package"></a>レッスン 3-3:レッスン 3 で作成したチュートリアル パッケージのテスト

この実習では、**Lesson 3.dtsx** パッケージを実行します。 パッケージが実行されると、**[ログ イベント]** ウィンドウに、SSIS によってログ ファイルに書き込まれるログ エントリがログ プロバイダー別に一覧表示されます。 パッケージ実行が完了したら、ログ ファイルの内容を閲覧できます。  
  
## <a name="check-the-package-layout"></a>パッケージ レイアウトを確認する  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 3 のパッケージの制御フローとデータ フローに似ていることを確認します。 この制御フローはレッスン 2 と同じに、データ フローはレッスン 1 および 2 と同じになるはずです。  
  
**制御フロー**  
  
![パッケージ内の制御フロー](../integration-services/media/task4lesson2control.gif "パッケージ内の制御フロー")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
## <a name="run-the-lesson-3-tutorial-package"></a>レッスン 3 のチュートリアル パッケージを実行する  
  
1.  SSIS メニューで **[ログ イベント]** を選択します。  
  
2.  **[デバッグ]** メニューの **[デバッグの開始]** を選択します。  
  
3.  パッケージの実行が完了したら、**[デバッグ]** メニューの **[デバッグの停止]** を選択します。  
  
## <a name="examine-the-generated-log-file"></a>生成されたログ ファイルを検証する  
  
-   メモ帳などのテキスト エディターを使用し、TutorialLog.log ファイルを開きます。  
  
-   **PipelineExecutionPlan** イベントと **PipelineExecutionTrees** イベントに対して生成される情報について完全に説明することは、このチュートリアルの範囲を超えています。  ログ ファイルでは、**[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブに指定されている情報フィールドが最初の行に一覧表示されます。 また、Foreach ループが繰り返されるたびに、選択した 2 つのイベント、**PipelineExecutionPlan** と **PipelineExecutionTrees** が [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で記録されていることも確認できます。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 4:SSIS でエラー フロー リダイレクションを追加する](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
