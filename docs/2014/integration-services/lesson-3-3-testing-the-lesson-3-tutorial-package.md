---
title: 手順 3:レッスン 3 のチュートリアル パッケージのテスト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1096a476-93cf-4474-86f5-27d6357eb380
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ac6cb097990c33564c29dad6918c0b8cc883530d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751304"
---
# <a name="step-3-testing-the-lesson-3-tutorial-package"></a>手順 3:レッスン 3 のチュートリアル パッケージのテスト
  この実習では、Lesson 3.dtsx パッケージを実行します。 パッケージを実行すると、[ログ イベント] ウィンドウに、ログ ファイルに書き込まれているログ エントリの一覧が表示されます。 パッケージの実行が完了したら、ログ プロバイダーによって生成されたログ ファイルの内容を確認します。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
 パッケージをテストする前に、次の図に示すオブジェクトがレッスン 3 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 2 の制御フローと同じである必要があります。 データ フローはレッスン 1 および 2 のデータ フローと同じである必要があります。  
  
 **制御フロー**  
  
 ![パッケージ内の制御フロー](../../2014/tutorials/media/task4lesson2control.gif "パッケージ内の制御フロー")  
  
 **データ フロー**  
  
 ![パッケージ内のデータ フロー](../../2014/tutorials/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>レッスン 4 のチュートリアル パッケージを実行するには  
  
1.  [SSIS] メニューの [イベントの記録] をクリックします。  
  
2.  **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  
  
3.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
### <a name="to-examine-the-generated-log-file"></a>生成されたログ ファイルを検証するには  
  
-   メモ帳などのテキスト エディターを使用し、TutorialLog.log ファイルを開きます。  
  
-   情報のセマンティクスが生成されますが、`PipelineExecutionPlan`と`PipelineExecutionTrees`イベントは、このチュートリアルでは扱いませんが、最初の行で指定した情報フィールドが一覧表示されるを参照してください、**詳細**のタブ**SSIS ログの構成** ダイアログ ボックス。 また、Foreach ループが繰り返されるたびに、選択した 2 つのイベント、PipelineExecutionPlan および PipelineExecutionTrees が記録されていることも確認できます。  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 4:エラー フロー リダイレクションの追加](../integration-services/lesson-4-add-error-flow-redirection-with-ssis.md)  
  
  
