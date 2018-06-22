---
title: 'タスク 15: ビルドと、SSIS プロジェクトを実行している |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9a63fcf03591626d5b4c1351d5ce868ef7a9fb65
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082887"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>タスク 15: SSIS プロジェクトをビルドおよび実行する
  ここでは、SSIS プロジェクトをビルドおよび実行します。 値を設定する必要があります、コンピューターにインストールされている Excel 2010 の 64 ビット バージョンがあれば、 **Run64BitRuntime**に**False**作業する Excel ソースのです。  
  
1.  **ソリューション エクスプ ローラー**ウィンドウで、をクリックして**プロジェクト**メニューをクリックして [ **cleanseandcuratesuppliers Properties]** です。  
  
2.  **プロパティ** ダイアログ ボックスで、展開**構成プロパティ**クリックして、左側**デバッグ**です。  
  
3.  設定**Run64BitRuntime**に**False**です。  
  
     ![CleanseAndCurateSuppliers プロジェクトのプロパティ](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers プロジェクトのプロパティ")  
  
4.  をクリックして**OK**を閉じる、**プロパティ** ダイアログ ボックス。  
  
5.  をクリックして**ビルド**クリックしてメニュー バー **Build CleanseAndCurateSuppliers**です。 ビルド エラーがないことを確認します。  
  
6.  をクリックして**デバッグ**クリックしてメニュー バー**デバッグの開始**です。  
  
7.  表示されるメッセージで、**進行状況**ウィンドウし、そのパッケージが実行され、正常に終了したことを確認します。  
  
     ![進行状況ウィンドウの結果](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "進行状況ウィンドウの結果")  
  
     ![進行状況ウィンドウの最終状態](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "進行状況ウィンドウの最終状態")  
  
8.  をクリックして**デバッグ**クリックしてメニュー バー**デバッグの停止**デバッグ セッションを停止します。 パッケージの実行に失敗した場合、データ ビューアーを有効にしてコンポーネント間のデータ フローを確認する必要があります。  
  
## <a name="next-step"></a>次の手順  
 [タスク 16: マスター データ マネージャーを確認する](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  