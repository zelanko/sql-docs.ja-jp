---
title: Microsoft Surface デバイスと Apple iOS デバイスでの Reporting Services レポートの表示 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
caps.latest.revision: 21
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 683a20afc442b7e10a64cac86aa0502c57dabbc0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166323"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a>Microsoft Surface デバイスと Apple iOS デバイスでの Reporting Services レポートの表示
  このトピックでは、Microsoft Surface デバイス、Apple iOS 6 と Apple Safari を搭載したデバイス (iPad など) でサポートされる [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能とワークフローについて説明します。  
  
## <a name="view-and-interact-with-reports"></a>レポートの表示および操作  
 以降で[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Microsoft Surface デバイス、および Apple iOS 6 および Apple Safari ブラウザー、iPad などのデバイスの表示と基本的なレポート対話機能をサポートしています。 Microsoft Surface デバイスを使用してレポートをパブリッシュすることもできます。  
  
 ![IPad デスクトップ](media/videothumbnail.jpg "IPad デスクトップ")  
iPad でレポートを表示する方法の例をご覧ください。  
  
 Windows Phone 8 デバイスで [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポートを表示することもできます。  
  
 ここで説明する機能を使用するには、次のいずれかをインストールします。  
  
-   ネイティブ モードのレポート サーバーの場合は、[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 以降のバージョンをインストールします。  
  
     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] ダウンロードできますが、 [Microsoft ダウンロード センター](http://www.microsoft.com/download/details.aspx?id=35575)します。  
  
-   SharePoint モードのレポート サーバー インストール[!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]またはそれ以降の[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 製品用アドイン。  
  
 **IPad デバイスまたは Microsoft Surface デバイスに関するレポートを表示して操作するには**  
  
1.  レポートが存在するレポート サーバーまたは SharePoint サイトに接続できることを確認します。  
  
2.  次のいずれかの手順に従って、レポートを開きます。  
  
    -   **電子メールからの起動:** によって作成される電子メールから、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]サブスクリプション、レポートの URL をタップします。 レポートがブラウザーで開かれます。  
  
    -   **レポート サーバーからの起動:** でディレクトリを参照、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート サーバーとレポートを開くレポート名をタップします。  
  
    -   **SharePoint ドキュメント ライブラリからの起動:** を含む SharePoint ドキュメント ライブラリを参照[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート、およびレポート名をタップします。 レポートを表示および操作できます。  
  
        > [!IMPORTANT]  
        >  iPad の場合は、Safari の **[プライベート ブラウズ]** プロパティがオフになっていることを確認します。  
  
    -   **SharePoint web パーツ:** web パーツが SharePoint ページに追加されている場合は表示できます[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポートします。  
  
3.  Microsoft Surface デバイスでは、レポート マネージャーを使用してレポートを開くこともできます。 ディレクトリを参照[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]レポート マネージャーとレポートを開くレポート名をタップします。  
  
    > [!IMPORTANT]  
    >  iPad では、レポート マネージャーでのレポートの表示はサポートされていません。  
  
4.  次のように操作することによって、スクロールやズームを行います。  
  
    -   レポートをスクロールするには、画面上で指をドラッグします (上、下、左、または右)。 これはスワイプ ジェスチャです。  
  
    -   拡大するには、画面に指を 2 本当て、指と指の距離を広げます。 縮小するには、画面に指を 2 本当て、指と指の距離を狭めます。 これはピンチ ジェスチャです。  
  
5.  次のように操作することによって、レポートでの移動と操作を行います。  
  
    -   レポート アイテムや、グループに関連付けられている行と列を折りたたむにはプラス記号 (+) をタップし、展開するにはマイナス記号 (-) をタップします。  
  
    -   テーブルの行またはマトリックスの行と列を昇順および降順で並べ替えるには、並べ替えボタンをタップします。 並べ替えボタンは、通常、列ヘッダーにあります。  
  
    -   パラメーター ペインを展開したり折りたたんだりするには、レポートの上部にある矢印ボタンをタップします。  
  
    -   パラメーター値を選択するには、パラメーターの横にあるボックスまたはコントロールをタップします。 パラメーター値をレポートに適用するには、 **[レポートの表示]** をタップします。  
  
    -   レポートの内容を検索するには、 **[検索]** の横にあるボックスをタップし、検索語句を入力して、 **[検索]** をタップします。  
  
    -   レポートのページ間を移動するには、ナビゲーション ボタンをタップするか、ボタンの横にあるテキスト ボックスをタップしてページ番号を入力します。  
  
    -   URL に移動するには、レポート アイテムに追加されたテキスト ボックス、画像、グラフ、ゲージなどのハイパーリンクをタップします。  
  
    -   レポートをエクスポートするには、 **[エクスポート]** メニューのアイコンをタップし、ファイル形式をタップします。  
  
        -   Microsoft Surface デバイスでレポートを表示している場合は、次のいずれかの形式にレポートをエクスポートできます。  
  
            -   レポート データが含まれている XML ファイル  
  
            -   CSV (コンマ区切り)  
  
            -   PDF  
  
            -   MHTML (Web アーカイブ)  
  
            -   [エクスポート]  
  
            -   TIFF  
  
            -   Word  
  
        -   iPad でレポートを表示している場合は、TIFF ファイルまたは PDF ファイルとしてエクスポートできます。  
  
## <a name="authentication"></a>[認証]  
 RSWindowsNTLM 認証と RSWindowsBasic 認証の使用[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]ネイティブ モードと iPad でします。  
  
 一般に、この種類の認証は転送資格認証に機密性を提供しないため、RSWindowsBasic は HTTPS 環境以外では使用しないことをお勧めします。  
  
 RSWindowsNTLM 認証と RSWindowsBasic 認証の詳細については、次を参照してください。[レポート サーバーでの認証](security/authentication-with-the-report-server.md)します。  
  
## <a name="uploading-reports"></a>レポートのアップロード  
 適切な権限がある場合は、次のどちらかの方法を使用して Microsoft Surface デバイスからレポートをパブリッシュできます。  
  
> [!IMPORTANT]  
>  iPad ではこれらの方法はサポートされません。  
  
-   ライブラリを開き、 **[ドキュメントのアップロード]** をタップして、SharePoint ドキュメント ライブラリにレポート定義ファイル (.rdl) をアップロードします。  
  
-   レポート マネージャーを開き、 **[ファイルのアップロード]** をタップして、レポート サーバー データベースにレポート定義ファイルをアップロードします。  
  
## <a name="additional-information"></a>追加情報  
 詳細については[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]し、サポートされているブラウザーを参照してください。  
  
-   [Reporting Services と Power View のブラウザー サポートの計画&#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)  
  
 Microsoft Business Intelligence およびモバイル デバイスの詳細については、以下を参照してください。  
  
-   [モバイル デバイスと SharePoint 2013 の概要](http://technet.microsoft.com/library/fp161351\(v=office.15\).aspx)(http://technet.microsoft.com/library/fp161351(v=office.15).aspx)します。  
  
-   [SharePoint 2013 でサポートされているモバイル デバイス ブラウザー](http://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (http://technet.microsoft.com/library/fp161353(v=office.15).aspx)します。  
  
-   [Apple iPad デバイス (SharePoint Server 2010) でレポートとスコアカードの表示](http://technet.microsoft.com/library/hh697482.aspx)(http://technet.microsoft.com/library/hh697482.aspx)します。  
  
-   [IPad (ビデオ) で Reporting Services レポートの表示](http://technet.microsoft.com/sqlserver/jj873792.aspx)(http://technet.microsoft.com/sqlserver/jj873792.aspx)します。  
  
-   [Microsoft Surface RT デバイスの (ビデオ) で Reporting Services レポートを表示します。](http://technet.microsoft.com/sqlserver/dn146017)  
  
  
