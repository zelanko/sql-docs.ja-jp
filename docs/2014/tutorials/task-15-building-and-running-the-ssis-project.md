---
title: '作業 15: SSIS プロジェクトをビルドして実行する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 50b313f63ae434a96d6c0e38f3c8b600914c806d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66822997"
---
# <a name="task-15-building-and-running-the-ssis-project"></a>タスク 15: SSIS プロジェクトをビルドおよび実行する

  ここでは、SSIS プロジェクトをビルドおよび実行します。 コンピューターに64ビット版の Excel 2010 がインストールされている場合は、Excel ソースが機能するように**Run64BitRuntime**の値を**False**に設定する必要があります。  
  
1.  **ソリューションエクスプローラー**ウィンドウで、メニューの [**プロジェクト**] をクリックし、[ **CleanseAndCurateSuppliers Properties**] をクリックします。  
  
2.  [**プロパティ**] ダイアログボックスで、左側の [**構成プロパティ**] を展開し、[**デバッグ**] をクリックします。  
  
3.  **Run64BitRuntime**を**False**に設定します。  
  
     ![CleanseAndCurateSuppliers プロジェクトのプロパティ](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers プロジェクトのプロパティ")  
  
4.  **[OK]** をクリックして、**[プロパティ]** ダイアログ ボックスを閉じます。  
  
5.  メニューバーの [**ビルド**] をクリックし、[ **CleanseAndCurateSuppliers のビルド**] をクリックします。 ビルド エラーがないことを確認します。  
  
6.  メニューバーの [**デバッグ**] をクリックし、[**デバッグの開始**] をクリックします。  
  
7.  [**進行状況**] ウィンドウでメッセージを確認し、パッケージが実行されて正常に終了したことを確認します。  
  
     ![進行状況ウィンドウの結果](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "進行状況ウィンドウの結果")  
  
     ![進行状況ウィンドウの最終状態](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "進行状況ウィンドウの最終状態")  
  
8.  メニューバーの [**デバッグ**] をクリックし、[**デバッグの停止**] をクリックしてデバッグセッションを停止します。 パッケージの実行に失敗した場合、データ ビューアーを有効にしてコンポーネント間のデータ フローを確認する必要があります。  
  
## <a name="next-step"></a>次の手順  
 [タスク 16: マスター データ マネージャーを確認する](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
