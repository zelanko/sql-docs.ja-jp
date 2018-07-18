---
title: ログ イベント ウィンドウでログ エントリを表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
caps.latest.revision: 20
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 15afed05e62e6d03fb785df734afcb5c6dabd2d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279668"
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
  
  
