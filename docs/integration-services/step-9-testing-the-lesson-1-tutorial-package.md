---
title: "手順 9: レッスン 1 のチュートリアル パッケージのテスト | Microsoft Docs"
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
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# 手順 9: レッスン 1 のチュートリアル パッケージのテスト
このレッスンでは次の作業を行いました。  
  
-   新しい [!INCLUDE[ssIS](../includes/ssis-md.md)] プロジェクトを作成しました。  
  
-   ソース データおよび変換先データに接続するための接続マネージャーをパッケージに追加し、構成しました。  
  
-   フラット ファイル ソースからデータを取得し、そのデータに対して必要な参照変換を実行した後、変換先に合わせてデータを構成するためのデータ フローを追加しました。  
  
これでパッケージは完成です。 次に、パッケージをテストします。  
  
## パッケージ レイアウトの確認  
パッケージをテストする前に、次の図に示すオブジェクトがレッスン 1 のパッケージの制御フローとデータ フローに含まれていることを確認します。  
  
**制御フロー**  
  
![Control flow in package](../integration-services/media/task9lesson1control.gif "Control flow in package")  
  
**データ フロー**  
  
![Data flow in package](../integration-services/media/task9lesson1data.gif "Data flow in package")  
  
### レッスン 1 のチュートリアル パッケージを実行するには  
  
1.  **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
    パッケージが実行されます。その結果、**AdventureWorksDW2012** の **FactCurrency** ファクト テーブルに 1,097 個の行が追加されます。  
  
2.  パッケージの実行が完了したら、**[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
## 次のレッスン  
[レッスン 2: SSIS でのループの追加](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## 参照  
[プロジェクトとパッケージの実行](../Topic/Execution%20of%20Projects%20and%20Packages.md)  
  
  
  
