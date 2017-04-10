---
title: "手順 3: レッスン 3 のチュートリアル パッケージのテスト | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 手順 3: レッスン 3 のチュートリアル パッケージのテスト
この実習では、Lesson 3.dtsx パッケージを実行します。 パッケージを実行すると、[ログ イベント] ウィンドウに、ログ ファイルに書き込まれているログ エントリの一覧が表示されます。 パッケージの実行が完了したら、ログ プロバイダーによって生成されたログ ファイルの内容を確認します。  
  
## パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 3 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 2 の制御フローと同じである必要があります。 データ フローはレッスン 1 および 2 のデータ フローと同じである必要があります。  
  
**制御フロー**  
  
![Control flow in package](../integration-services/media/task4lesson2control.gif "Control flow in package")  
  
**データ フロー**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### レッスン 4 のチュートリアル パッケージを実行するには  
  
1.  [SSIS] メニューの [イベントの記録] をクリックします。  
  
2.  **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  
  
3.  パッケージの実行が完了したら、**[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
### 生成されたログ ファイルを検証するには  
  
-   メモ帳などのテキスト エディターを使用し、TutorialLog.log ファイルを開きます。  
  
-   **PipelineExecutionPlan** および **PipelineExecutionTrees** イベントで生成される情報の見方については、このチュートリアルでは説明しません。しかし、ログ ファイルの 1 行目には、**[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブで指定した情報フィールドが一覧表示されます。 また、Foreach ループが繰り返されるたびに、選択した 2 つのイベント、PipelineExecutionPlan および PipelineExecutionTrees が記録されていることも確認できます。  
  
## 次のレッスン  
[レッスン 4: SSIS でエラー フロー リダイレクションを追加する](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
  
