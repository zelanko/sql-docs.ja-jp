---
title: "レッスン 9: アプリケーションをビルドして実行する | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: "9"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 28fe6303c84e14cf6349b82eea626b15953705d0
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="lesson-9-build-and-run-the-application"></a>Lesson 9: Build and Run the Application
データ テーブルのデータ フィルターを作成した後は、Web サイト アプリケーションをビルドして実行します。  
  
### <a name="to-build-and-run-the-application"></a>アプリケーションをビルドして実行するには  
  
1.  **Ctrl キーを押しながら F5 キー** を押して Default.aspx ページをデバッグせずに実行するか、または F5 キーを押してページをデバッグしながら実行します。  
  
    ビルド プロセスの一部としてレポートがコンパイルされます。検出されたエラー (レポートで使用されている式の構文エラーなど) は、Visual Studio ウィンドウの下部にある **[タスク一覧]** に追加されます。  
  
    Web ページがブラウザーに表示されます。 ReportViewer コントロールにレポートが表示されます。 ツール バーを使用して、レポート内の移動、ズーム、およびレポートの Excel へのエクスポートを行うことができます。  
  
2.  
              **[名前]** 列の任意の行にマウス カーソルを合わせます。 手の形のマウス カーソルが表示されます。  
  
3.  **[名前]** 列の値を選択します。 対応するフィルター選択されたデータを含む子レポートが表示されます。  
  
4.  **ReportViewer**ツール バーの **[親レポートに戻る]** アイコンを選択し、 **親** レポートに戻ります。  
  
5.  ブラウザーを閉じて終了します。  
  
  
  

