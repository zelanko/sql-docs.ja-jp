---
title: "[ログ イベント] ウィンドウでログ エントリを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ [Integration Services]、表示"
  - "Integration Services パッケージ、ログ"
  - "パッケージ [Integration Services]、ログ"
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# [ログ イベント] ウィンドウでログ エントリを表示する
  この手順では、パッケージを実行して、パッケージが書き込むログ エントリを表示する方法について説明します。 ログ エントリはリアルタイムで表示できます。 **[ログ イベント]** ウィンドウに書き込まれたログ エントリは、さらに詳しく分析するためにコピーして保存することもできます。  
  
 **[ログ イベント]** ウィンドウにエントリを書き込むために、ログ エントリをログに書き込む必要はありません。  
  
### ログ エントリを表示するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  **[SSIS]** メニューの **[ログ イベント]** をクリックします。 必要に応じて、View.LogEvents コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、**[ログ イベント]** ウィンドウを表示することもできます。  
  
3.  **[デバッグ]** メニューの **[デバッグの開始]**をクリックします。  
  
     実行時に、ログ記録可能なイベントやカスタム メッセージが見つかると、各イベントまたはメッセージのログ エントリが **[ログ イベント]** ウィンドウに書き込まれます。  
  
4.  **[デバッグ]** メニューの **[デバッグの停止]** をクリックします。  
  
     **[ログ イベント]** ウィンドウのログ エントリは、パッケージを再実行するか、別のパッケージを実行するか、または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] を終了するまでは、そのまま使用できます。  
  
5.  **[ログ イベント]** ウィンドウで、ログ エントリを表示します。  
  
6.  必要に応じて、コピーするログ エントリを右クリックして **[コピー]** をクリックします。  
  
7.  必要に応じて、ログ エントリをダブルクリックし、**[ログ エントリ]** ダイアログ ボックスで、1 つのログ エントリの詳細を表示します。  
  
8.  **[ログ エントリ]** ダイアログ ボックスで、上矢印および下矢印をクリックして前後のログ エントリを表示し、コピー アイコンをクリックしてログ エントリをコピーします。  
  
9. テキスト エディターを開いて貼り付けた後、ログ エントリをテキスト ファイルに保存します。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  