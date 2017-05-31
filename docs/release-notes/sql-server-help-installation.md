---
title: "SQL Server のヘルプ ビューアー | Microsoft Docs"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fc2435ccea3b01328c3c4623e62fbf12ee53e400
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="help-viewer-for-sql-server"></a>SQL Server のヘルプ ビューアー
  
  
  
この記事では、ローカル ヘルプのインストール方法と、オンラインおよびローカル ヘルプの表示方法について説明します。 この記事では、Microsoft ヘルプ ビューアー 1.1 および 2.2 と、[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] および [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] のドキュメントをカバーしています。 

>[!IMPORTANT]
>ヘルプ ビューアーでは、プロキシ設定はサポートされておらず、ISO 形式もサポートされていません。  

>**F1 とヘルプ**
>>F1 キーを押すと、対応するトピックがオンラインで表示されます。 このトピックはローカル ヘルプでは表示できません。

## <a name="includesscurrentmdincludessscurrent-mdmd-and-help-viewer-22"></a>[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] とヘルプ ビューアー 2.2  
ヘルプ ビューアー 2.2 は、2016 年 4 月プレビュー (13.0.12500.29) 以降の [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio と、Visual Studio 2015 で提供されています。  

> [![SSMS をダウンロードする](../release-notes/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[最新バージョンの SQL Server Management Studio をダウンロードする](https://msdn.microsoft.com/library/mt238290.aspx)**  

**ヘルプ ビューアー 2.2 で使用するローカル ヘルプをインストールするには**  
1. SQL Server Management Studio または Visual Studio を起動し、**[ヘルプ]** メニューの **[ヘルプ コンテンツの追加と削除]** をクリックして、ヘルプ ビューアー 2.2 を開きます。  
2. **[コンテンツの管理]** タブをクリックします。  
3. オンライン ソースからヘルプをインストールするには、**[インストール元]** 領域で **[オンライン]** をクリックします。  
![HelpViewer2_ManageContent_OnlineSource](../release-notes/media/helpviewer2-managecontent-onlinesource.png)  
7. インストールするドキュメントの横の **[追加]** をクリックし、**[更新]** をクリックします。  
![HelpViewer2_ManageContent_AddContent](../release-notes/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >SQL Server Management Studio と Visual Studio では、ドキュメントの追加プロセス中に、ヘルプ ビューアーのアプリケーションが凍結 (ハング) することがあります。 この問題を解決するには、以下の手順を実行します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](https://msdn.microsoft.com/library/mt654096.aspx)」を参照してください。  
   >>メモ帳で %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings ファイルを開き、次のコード内の日付を将来の日付に変更します。 このファイルは、Visual Studio をインストールした場合にのみ、ローカル コンピューターで利用できます。 
   >>>Cache LastRefreshed="12/31/2017 00:00:00"  
  
    左ペインにある目次が自動的に更新され、追加したドキュメントが反映されます。  
![HelpViewer2_withContentInstalled](../release-notes/media/helpviewer2-withcontentinstalled.png)

1. (省略可能) **[コンテンツの管理]** タブの **[ローカル ストア パス]** ボックスに、ローカル コンピューター上でのドキュメントのインストール先が表示されます。 ドキュメントを別の場所に移動するには、**[移動]** をクリックし、**[コンテンツの移動]** ダイアログ ボックスの **[To (移動先)]** フィールドにフォルダー パスを入力して、**[OK]** をクリックします。

   ![HelpViewer2_Move Content Dialog](../release-notes/media/helpviewer2-move-content-dialog.png)

   コンテンツが移動されると、**[ローカル ストア パス]** に新しい場所が表示されます。
      
   >[!IMPORTANT]
   > 移動操作が失敗したことを示すメッセージが表示された場合は、メッセージ ボックスを閉じ、ヘルプ ビューアーを閉じた後、ヘルプ ビューアーを再度開きます。 **[ローカル ストア パス]** に、コンテンツの新しい場所が表示されます。   
  
**SQL Server Management Studio でローカル ヘルプまたはオンライン ヘルプを表示するには**  
* ローカル ヘルプを表示するには、**[ヘルプ]** メニューの **[ヘルプ コンテンツの追加と削除]** をクリックし、**[ヘルプ ビューアー ホーム]** タブをクリックしてドキュメントを表示します。  
    >[!NOTE]
    >**[ヘルプ ビューアー ホーム]** というテキストは、目次でクリックしたトピックに応じて変わります。   
* オンライン ヘルプを表示するには、**[ヘルプ]** メニューの **[ヘルプの表示]** をクリックします。 ブラウザーにドキュメントが表示されます。  
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)  
  
  
**Visual Studio でローカル ヘルプまたはオンライン ヘルプを表示するには**  
* **[ヘルプ]** メニューの **[ヘルプ設定の設定]** をクリックし、次のいずれかの操作を行います。  
   * オンライン ヘルプを表示するには、**[ブラウザーで起動]** をクリックします。 **[ヘルプ]** メニューの **[ヘルプの表示]** をクリックすると、ブラウザーにドキュメントが表示されます。  
   * ローカル ヘルプを表示するには、**[ヘルプ ビューアーで起動]** をクリックします。 **[ヘルプ]** メニューの **[ヘルプの表示]** をクリックすると、ヘルプ ビューアーにドキュメントが表示されます。  
     
     ![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)  
  
  
## <a name="includesssql14mdincludessssql14-mdmd-and-help-viewer-11"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] とヘルプ ビューアー 1.1  
 ヘルプ ビューアー 1.1 は、[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] Management Studio と、Visual Studio 2012 より前のバージョンの Visual Studio で利用できます。   
 
>[!NOTE]
> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 用のローカル ヘルプは、**ディスクからコンテンツをインストール**した場合に限り、ヘルプ ビューアー 2.2 でも表示できます。 ヘルプ ビューアー 2.2 は、2016 年 4 月プレビュー (13.0.12500.29) 以降の [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio と、Visual Studio 2015 で提供されています。 
   
**ヘルプ ビューアー 1.1 で使用するローカル ヘルプをインストールするには**  
1. ヘルプ コンテンツの[ダウンロード サイト](https://www.microsoft.com/en-us/download/details.aspx?id=42557)に移動し、**[ダウンロード]** をクリックします。  
2. メッセージ ボックスの **[保存]** をクリックして、 SQLServer2014Documentation_*.exe ファイルをコンピューターに保存します。  
   >[!NOTE]
   >ファイアウォールとプロキシによる制限がある環境では、環境内に持ち込むことができる USB ドライブか、その他のポータブル メディアにダウンロードを保存します。   
3. .exe をダブルクリックしてヘルプ コンテンツ ファイルをアンパックし、ローカルまたは共有のフォルダーにファイルを保存します。  
4. SQL Server Management Studio または Visual Studio を起動し、**[ヘルプ]** メニューの **[ヘルプの設定の管理]** をクリックして、**[ヘルプ ライブラリ マネージャー]** を開きます。  
7. **[ディスクからコンテンツをインストール]** をクリックし、ヘルプ コンテンツ ファイルをアンパックしたフォルダーを参照します。  
  
[ディスクからコンテンツをインストール] を選択する  |ヘルプ コンテンツ ファイルを参照する   
---------|---------  
![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
>[!IMPORTANT]
> 目次の一部しかないローカル ヘルプ コンテンツがインストールされるのを防ぐには、**[ヘルプ ライブラリ マネージャー]** の **[ディスクからコンテンツをインストール]** オプションを使用します。  
>>**[オンラインからコンテンツをインストール]** オプションを使用した場合は、ヘルプ ビューアーに部分的な目次が表示されます。トラブルシューティング手順については、こちらの[ブログ投稿](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/)をご覧ください。 

8. HelpContentSetup.msha ファイルをクリックし、**[開く]** をクリックして、**[次へ]** をクリックします。  
9. インストールするドキュメントの横の **[追加]** をクリックし、**[更新]** をクリックします。  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. **[完了]** をクリックし、**[終了]** をクリックした後、**[ヘルプ]** メニューの **[ヘルプの表示]** をクリックしてヘルプ ビューアーを開き、コンテンツを表示します。 左ペインの目次に、インストールしたコンテンツが表示されます。  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
**ローカル ヘルプまたはオンライン ヘルプを表示するには**  
1. **[ヘルプ]** メニューの **[ヘルプの設定の管理]** をクリックして、**ヘルプ ライブラリ マネージャー**を開きます。  
2. **[ヘルプ ライブラリ マネージャー]** ダイアログ ボックスで、**[オンラインまたはローカル ヘルプの選択]** をクリックします。  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. 次のいずれかの操作を行い、**[OK]** をクリックして、**[終了]** をクリックします。  
   * **[I want to use online help (オンライン ヘルプを使用します)]** をクリックする  
   * **[I want to use local help (ローカル ヘルプを使用します)]** をクリックする。  
  
   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)  
  
オンライン ヘルプを使用するよう選択した場合は、**[ヘルプ]** メニューの **[ヘルプの表示]** をクリックすると、ブラウザーが起動し、MSDN の「[Books Online for SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx)」記事が表示されます。 ローカル ヘルプを使用するように選択した場合は、**[ヘルプの表示]** をクリックするとヘルプ ビューアーが起動します。  

## <a name="additional-information"></a>関連情報
[Microsoft ヘルプ ビューアー - Visual Studio 2015](https://msdn.microsoft.com/library/hh580782.aspx)

