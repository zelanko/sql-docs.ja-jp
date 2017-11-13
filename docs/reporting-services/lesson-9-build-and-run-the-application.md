---
title: "レッスン 9: アプリケーション ビルドし、実行、|Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: 9
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c3e9d3ca3b3b708105bf428508ff52c021bd5dd0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="lesson-9-build-and-run-the-application"></a>レッスン 9: アプリケーションをビルドして実行する
データ テーブルのデータ フィルターを作成した後は、Web サイト アプリケーションをビルドして実行します。  
  
### <a name="to-build-and-run-the-application"></a>アプリケーションをビルドして実行するには  
  
1.  **Ctrl キーを押しながら F5 キー** を押して Default.aspx ページをデバッグせずに実行するか、または F5 キーを押してページをデバッグしながら実行します。  
  
    ビルド プロセスの一部としてレポートがコンパイルされます。検出されたエラー (レポートで使用されている式の構文エラーなど) は、Visual Studio ウィンドウの下部にある **[タスク一覧]** に追加されます。  
  
    Web ページがブラウザーに表示されます。 ReportViewer コントロールにレポートが表示されます。 ツール バーを使用して、レポート内の移動、ズーム、およびレポートの Excel へのエクスポートを行うことができます。  
  
2.  **[名前]** 列の任意の行にマウス カーソルを合わせます。 手の形のマウス カーソルが表示されます。  
  
3.  **[名前]** 列の値を選択します。 対応するフィルター選択されたデータを含む子レポートが表示されます。  
  
4.  **ReportViewer**ツール バーの **[親レポートに戻る]** アイコンを選択し、 **親** レポートに戻ります。  
  
5.  ブラウザーを閉じて終了します。  
  
  
  


