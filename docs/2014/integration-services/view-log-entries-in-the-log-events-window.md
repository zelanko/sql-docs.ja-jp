---
title: ログ イベント ウィンドウでログ エントリを表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 51c08b271229e207f72b594d87e3c9f95b6770f6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172732"
---
# <a name="view-log-entries-in-the-log-events-window"></a>[ログ イベント] ウィンドウでログ エントリを表示する
  この手順では、パッケージを実行して、パッケージが書き込むログ エントリを表示する方法について説明します。 ログ エントリはリアルタイムで表示できます。 **[ログ イベント]** ウィンドウに書き込まれたログ エントリは、さらに詳しく分析するためにコピーして保存することもできます。  
  
 **[ログ イベント]** ウィンドウにエントリを書き込むために、ログ エントリをログに書き込む必要はありません。  
  
### <a name="to-view-log-entries"></a>ログ エントリを表示するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  **[SSIS]** メニューの **[ログ イベント]** をクリックします。 必要に応じて、View.LogEvents コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[ログ イベント]** ウィンドウを表示することもできます。  
  
3.  **[デバッグ]** メニューの **[デバッグの開始]** をクリックします。  
  
     実行時に、ログ記録可能なイベントやカスタム メッセージが見つかると、各イベントまたはメッセージのログ エントリが **[ログ イベント]** ウィンドウに書き込まれます。  
  
4.  **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
     **[ログ イベント]** ウィンドウのログ エントリは、パッケージを再実行するか、別のパッケージを実行するか、または [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]を終了するまでは、そのまま使用できます。  
  
5.  **[ログ イベント]** ウィンドウで、ログ エントリを表示します。  
  
6.  必要に応じて、コピーするログ エントリを右クリックして **[コピー]** をクリックします。  
  
7.  必要に応じて、ログ エントリをダブルクリックし、 **[ログ エントリ]** ダイアログ ボックスで、1 つのログ エントリの詳細を表示します。  
  
8.  **[ログ エントリ]** ダイアログ ボックスで、上矢印および下矢印をクリックして前後のログ エントリを表示し、コピー アイコンをクリックしてログ エントリをコピーします。  
  
9. テキスト エディターを開いて貼り付けた後、ログ エントリをテキスト ファイルに保存します。  
  
## <a name="see-also"></a>参照  
 [Integration Services &#40;SSIS&#41; のログ記録](performance/integration-services-ssis-logging.md)  
  
  
