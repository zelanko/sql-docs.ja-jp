---
title: "Reporting Services スクリプト ファイルを実行する | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
caps.latest.revision: "36"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 764f1d8fca32f706ab719c06b6a243096f7bad98
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="run-a-reporting-services-script-file"></a>Reporting Services スクリプト ファイルを実行する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト ファイルは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境 (RS.exe) を使用してコマンド プロンプトから実行します。 RS.exe には、ユーザーが使用できるコマンド プロンプト引数が多数用意されています。 コマンド プロンプト オプションの詳細については、「[RS.exe ユーティリティ &#40;SSRS&#41;](../../reporting-services/tools/rs-exe-utility-ssrs.md)」を参照してください。 他のスクリプトのサンプルについては、「 [SQL Server Reporting Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。  
  
## <a name="sample-command-lines"></a>コマンド ラインでの実行例  
  
-   スクリプト環境で Script.rss を次のように実行すると、ターゲット レポート サーバーが指定されます。 既定では、Windows 認証が適用されます。  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、Web サービスの呼び出しを認証するためのユーザー名とパスワードが指定されます。  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、30 秒のサーバー タイムアウトが指定されます。  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、 *report*と呼ばれるグローバル スクリプト変数が指定されます。  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、スクリプト ファイルの Web サービス操作がバッチとして実行するように指定されます。  
  
    ```  
    rs –i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>参照  
 [テクニカル リファレンス (SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
