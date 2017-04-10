---
title: "手順 3: レッスン 6 のパッケージのテスト | Microsoft Docs"
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
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 手順 3: レッスン 6 のパッケージのテスト
パッケージを実行すると、VarFolderName パラメーターから Directory プロパティの値が取得されます。  
  
パッケージの実行時に、Directory プロパティが新しい値に更新されているかどうかを確認するには、パッケージを実行してみます。 3 つのサンプル データ ファイルのみが新しいディレクトリにコピーされるため、データ フローは 3 回だけ実行されます。元のフォルダーの 14 ファイルには反復処理は実行されません。  
  
## パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 6 のパッケージの制御フローとデータ フローに含まれていることを確認します。 制御フローはレッスン 5 の制御フローと同じである必要があります。 データ フローはレッスン 5 のデータ フローと同じである必要があります。  
  
**制御フロー**  
  
![制御フロー](../integration-services/media/task3lesson6control.jpg "制御フロー")  
  
**データ フロー**  
  
![データ フロー](../integration-services/media/task3lesson6data.jpg "データ フロー")  
  
### レッスン 6 のチュートリアル パッケージをテストするには  
  
1.  [デバッグ] メニューの [デバッグの開始] をクリックします。  
  
2.  パッケージの実行が完了したら、[デバッグ] メニューの [デバッグの停止] をクリックします。  
  
## このレッスンの次の作業  
[手順 4: レッスン 6 のパッケージの展開](../integration-services/step-4-deploying-the-lesson-6-package.md)  
  
  
  
