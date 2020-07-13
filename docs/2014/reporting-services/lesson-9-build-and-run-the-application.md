---
title: 'レッスン 9: アプリケーションをビルドして実行する | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b21ee398eade4878d4f2273f17314dd184af2310
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176868"
---
# <a name="lesson-9-build-and-run-the-application"></a>レッスン 9: アプリケーションをビルドして実行する
  データ テーブルのデータ フィルターを作成した後は、Web サイト アプリケーションをビルドして実行します。

### <a name="to-build-and-run-the-application"></a>アプリケーションをビルドして実行するには

1.  **Ctrl キーを押しながら F5 キー** を押して Default.aspx ページをデバッグせずに実行するか、または F5 キーを押してページをデバッグしながら実行します。

     ビルド プロセスの一部としてレポートがコンパイルされます。検出されたエラー (レポートで使用されている式の構文エラーなど) は、Visual Studio ウィンドウの下部にある **[タスク一覧]** に追加されます。

     Web ページがブラウザーに表示されます。 ReportViewer コントロールにレポートが表示されます。 ツール バーを使用して、レポート内の移動、ズーム、およびレポートの Excel へのエクスポートを行うことができます。

2.  **[名前]** 列の任意の行にマウス カーソルを合わせます。 手の形のマウス カーソルが表示されます。

3.  **[名前]** 列の値をクリックします。 対応するフィルター選択されたデータを含む子レポートが表示されます。

4.  **ReportViewer**ツール バーの **[親レポートに戻る]** アイコンをクリックして、 **親** レポートに戻ります。

     ![ReportViewer を使用した ssrs ドリルスルー](../../2014/tutorials/media/ssrs-drillthrough-report.png "ReportViewer を使用した ssrs ドリルスルー")

5.  ブラウザーを閉じて終了します。


