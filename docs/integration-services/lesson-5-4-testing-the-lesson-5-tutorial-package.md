---
title: "手順 4: レッスン 5 のチュートリアル パッケージのテスト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
caps.latest.revision: "25"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f761097d3e2b7bac98c8617a723927d132c9f30b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="lesson-5-4---testing-the-lesson-5-tutorial-package"></a>レッスン 5-4 - レッスン 5 のチュートリアル パッケージのテスト
パッケージを実行すると、そのときに更新される変数から **Directory** の値が取得されます。パッケージの作成時に指定した元の名前は使用されません。 この変数の値は、SSISTutorial.dtsConfig ファイルにより生成されます。  
  
パッケージの実行時に、Directory プロパティが新しい値に更新されているかどうかを確認するには、パッケージを実行してみます。 3 つのサンプル データ ファイルのみが新しいディレクトリにコピーされるため、データ フローは 3 回だけ実行されます。元のフォルダーの 14 ファイルには反復処理は実行されません。  
  
## <a name="checking-the-package-layout"></a>パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 5 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 4 の制御フローと同じである必要があります。 データ フローはレッスン 4 のデータ フローと同じである必要があります。  
  
**制御フロー**  
  
![パッケージ内の制御フロー](../integration-services/media/task4lesson2control.gif "パッケージ内の制御フロー")  
  
**データ フロー**  
  
![パッケージ内のデータ フロー](../integration-services/media/task9lesson1data.gif "パッケージ内のデータ フロー")  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a>レッスン 5 で作成したチュートリアル パッケージをテストするには  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
2.  パッケージの実行が完了したら、 **[デバッグ]** メニューの **[デバッグの停止]**をクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 6: SSIS でプロジェクト配置モデルを持つパラメーターを使用する](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
  
