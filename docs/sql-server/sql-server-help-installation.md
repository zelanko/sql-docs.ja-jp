---
title: "SQL Server のヘルプ ビューアーとオフライン コンテンツ | Microsoft Docs"
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: b8e93b7afb8845398e23ca52c5c3f3bf3901898c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="help-viewer-and-offline-content-for-sql-server"></a>SQL Server のヘルプ ビューアーとオフライン コンテンツ
  
  
  
この記事では、ヘルプ ビューアーをインストールして SQL Server のドキュメントをオフラインで表示する方法を説明します。 この記事の対象は、[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)]、SQL Server 2016、SQL Server 2017 のドキュメントです。 

## <a name="install-help-viewer"></a>ヘルプ ビューアーをインストールする
次の表では、SQL Server のバージョンごとにヘルプ ビューアーをインストールするツールを示します。 ヘルプ ビューアーをインストールするには、いずれかのツールをインストールします。


|**SQL Server のバージョン**|**ヘルプ ビューアーをインストールするツール**|**インストールされるヘルプ ビューアーのバージョン**|
|---------|---------|---------|
|SQL Server 2017<br>SQL Server 2016     |   [SQL Server Management Studio の最新バージョン](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)<br><br>[Visual Studio 2015 の SQL Server Data Tools の最新バージョン](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)<br><br>Visual Studio 2017 (*SQL Server 2016* のみをサポート)  |  v2.x       |
|SQL Server 2014    | SQL Server 2014 Management Studio<br><br>Visual Studio 2012 より前のバージョンの Visual Studio        |  v1.x       |


> [!IMPORTANT]
> SQL Server 2016 でインストールされるヘルプ ビューアー 1.1 は、SQL Server 2016 および 2017 のドキュメントを表示できません。
> <br>
> <br>
> SQL Server 2017 では、ヘルプ ビューアーはインストールされません。
> <br>
> <br>
> Visual Studio 2017 でヘルプ ビューアーをインストールするには、**Visual Studio インストーラー** プログラムで **[個別のコンポーネント]** タブをクリックし、**[コード ツール]** カテゴリで **[ヘルプ ビューアー]** をクリックして、**[インストール]** をクリックします。 
> <br>
> <br>
> [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 用のローカル ヘルプは、**ディスクからコンテンツをインストール**した場合に限り、ヘルプ ビューアー 2.x で表示できます。 


## <a name="sql-server-2016-sql-server-2017-offline-content"></a>SQL Server 2016、SQL Server 2017 のオフライン コンテンツ  
 
**オフライン コンテンツをインストールするには**  
1. SQL Server Management Studio または Visual Studio を起動し、**[ヘルプ]** メニューの **[ヘルプ コンテンツの追加と削除]** をクリックして、ヘルプ ビューアーを開きます。  
2. **[コンテンツの管理]** タブをクリックします。  
3. オンライン ソースからヘルプをインストールするには、**[インストール元]** 領域で **[オンライン]** をクリックします。  
![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/helpviewer2-managecontent-onlinesource.png)  
7. インストールするドキュメントの横の **[追加]** をクリックし、**[更新]** をクリックします。  
![HelpViewer2_ManageContent_AddContent](../sql-server/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >SQL Server Management Studio と Visual Studio では、ドキュメントの追加プロセス中に、ヘルプ ビューアーのアプリケーションが凍結 (ハング) することがあります。 この問題を解決するには、以下の手順を実行します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](https://msdn.microsoft.com/library/mt654096.aspx)」を参照してください。  
   >>メモ帳で %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings ファイルを開き、次のコード内の日付を将来の日付に変更します。 このファイルは、Visual Studio をインストールした場合にのみ、ローカル コンピューターで利用できます。 
   >>>Cache LastRefreshed="12/31/2017 00:00:00"  
  
    左ペインにある目次が自動的に更新され、追加したドキュメントが反映されます。  
![HelpViewer2_withContentInstalled](../sql-server/media/helpviewer2-withcontentinstalled.png)

1. (省略可能) **[コンテンツの管理]** タブの **[ローカル ストア パス]** ボックスに、ローカル コンピューター上でのドキュメントのインストール先が表示されます。 ドキュメントを別の場所に移動するには、**[移動]** をクリックし、**[コンテンツの移動]** ダイアログ ボックスの **[To (移動先)]** フィールドにフォルダー パスを入力して、**[OK]** をクリックします。

   ![HelpViewer2_Move Content Dialog](../sql-server/media/helpviewer2-move-content-dialog.png)

   コンテンツが移動されると、**[ローカル ストア パス]** に新しい場所が表示されます。
      
   >[!IMPORTANT]
   > 移動操作が失敗したことを示すメッセージが表示された場合は、メッセージ ボックスを閉じ、ヘルプ ビューアーを閉じた後、ヘルプ ビューアーを再度開きます。 **[ローカル ストア パス]** に、コンテンツの新しい場所が表示されます。   
 
## <a name="includesssql14mdincludessssql14-mdmd-offline-content"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] のオフライン コンテンツ 
 
  
**オフライン コンテンツをインストールするには**  
1. ヘルプ コンテンツの[ダウンロード サイト](https://www.microsoft.com/en-us/download/details.aspx?id=42557)に移動し、**[ダウンロード]** をクリックします。  
2. メッセージ ボックスの **[保存]** をクリックして、 SQLServer2014Documentation_*.exe ファイルをコンピューターに保存します。  

 ファイアウォールとプロキシによる制限がある環境では、環境内に持ち込むことができる USB ドライブか、その他のポータブル メディアにダウンロードを保存します。   

3. .exe をダブルクリックしてヘルプ コンテンツ ファイルをアンパックし、ローカルまたは共有のフォルダーにファイルを保存します。  
4. SQL Server Management Studio または Visual Studio を起動し、**[ヘルプ]** メニューの **[ヘルプの設定の管理]** をクリックして、**[ヘルプ ライブラリ マネージャー]** を開きます。  
5. **[ディスクからコンテンツをインストール]** をクリックし、ヘルプ コンテンツ ファイルをアンパックしたフォルダーを参照します。  
  
     [ディスクからコンテンツをインストール] を選択する  |ヘルプ コンテンツ ファイルを参照する   
     ---------|---------  
     ![HelpLibraryManager_MainPage_InstallFromDisk](../sql-server/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../sql-server/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
     >[!IMPORTANT]
     > 目次の一部しかないローカル ヘルプ コンテンツがインストールされるのを防ぐには、**[ヘルプ ライブラリ マネージャー]** の **[ディスクからコンテンツをインストール]** オプションを使用します。  
     >>**[オンラインからコンテンツをインストール]** オプションを使用した場合は、ヘルプ ビューアーに部分的な目次が表示されます。トラブルシューティング手順については、こちらの[ブログ投稿](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/)をご覧ください。 

8. HelpContentSetup.msha ファイルをクリックし、**[開く]** をクリックして、**[次へ]** をクリックします。  
9. インストールするドキュメントの横の **[追加]** をクリックし、**[更新]** をクリックします。  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../sql-server/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. **[完了]** をクリックし、**[終了]** をクリックします。
11. **[ヘルプ ライブラリ マネージャー]** を再び開き、**[オンラインまたはローカル ヘルプの選択]** をクリックして、**[ローカル ヘルプを使用する]** をクリックします。
12. **[ヘルプ]** メニューの **[ヘルプの表示]** をクリックしてヘルプ ビューアーを開き、コンテンツを表示します。 左ペインの目次に、インストールしたコンテンツが表示されます。  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../sql-server/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
## <a name="view-online-content-in-help-viewer"></a>ヘルプ ビューアーでオンライン コンテンツを表示する

ヘルプ ビューアー v2.x では、次のいずれかの方法でオンライン コンテンツを表示できます。

- SQL Server Management Studio で、**[ヘルプ]** メニューの **[ヘルプの表示]** をクリックします。 ブラウザーにドキュメントが表示されます。
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../sql-server/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)

- Visual Studio で、**[ヘルプ]** メニューの **[ヘルプ設定の設定]** をクリックし、**[ブラウザーで起動]** をクリックします。 **[ヘルプ]** メニューの **[ヘルプの表示]** をクリックすると、ブラウザーにドキュメントが表示されます。

![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../sql-server/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)   

ヘルプ ビューアー v1.x では、次の方法でオンライン コンテンツを表示できます。
1. **[ヘルプ]** メニューの **[ヘルプの設定の管理]** をクリックして、**ヘルプ ライブラリ マネージャー**を開きます。  
2. **[ヘルプ ライブラリ マネージャー]** ダイアログ ボックスで、**[オンラインまたはローカル ヘルプの選択]** をクリックします。  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../sql-server/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. **[オンライン ヘルプを使用する]**、**[OK]**、**[終了]** の順にクリックします。  

   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../sql-server/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)

## <a name="f1-help-and-other-tips"></a>F1 ヘルプおよびその他のヒント

F1 キーを押すと、対応するトピックがオンラインで表示されます。 このトピックはローカル ヘルプでは表示できません。

また、ヘルプ ビューアーは、プロキシ設定および ISO 形式をサポートしていません。 

## <a name="additional-information"></a>関連情報
[Microsoft ヘルプ ビューアー - Visual Studio 2015](https://msdn.microsoft.com/library/hh580782.aspx)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
