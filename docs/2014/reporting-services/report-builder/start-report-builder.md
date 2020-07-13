---
title: レポートビルダーの開始 (レポートビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6fc123be862320cd35ccf4aec76d8bc9cf7877af
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107598"
---
# <a name="start-report-builder-report-builder"></a>レポート ビルダーの起動 (レポート ビルダー)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]には、スタンドアロン[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]バージョンとバージョンのレポートビルダーが含まれています。 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンは、ネイティブ モードまたは SharePoint 統合モードでインストールされた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共に使用できます。  
  
> [!NOTE]  
>  レポート ビルダーは、Itanium 64 ベースのコンピューターにはインストールできません。 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンおよびスタンドアロン バージョンのレポート ビルダーの場合も同様です。  
  
 開いて[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]いるレポートビルダーのバージョンがレポートビルダーの以前のバージョンである場合は、管理者に連絡して、の[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]バージョンを使用するようにレポートマネージャーおよび SharePoint サイトを更新することができレポートビルダー  
  
 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンのレポート ビルダーを使用して、SharePoint にパブリッシュされている [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ブックについてのレポートを作成することもできます。 で[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]レポートビルダーを使用する方法の詳細については、「Technet.microsoft.com で[PowerPivot データを使用して Reporting Services レポートを作成する](https://go.microsoft.com/fwlink/?LinkId=185238)」を参照してください。  
  
 ローカルコンピューターの [**スタート**] メニューからスタンドアロンレポートビルダー起動するには、ツールを使用できるようにする前に、ユーザーまたは管理者がレポートビルダーをコンピューターに直接インストールする必要があります。 スタンドアロン バージョンは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール時にインストールされません。別途ダウンロードして、インストールする必要があります。 レポートビルダーをダウンロードするには、「 [Microsoft® SQL Server®2012レポートビルダー](https://go.microsoft.com/fwlink/?LinkId=401502)」を参照してください。  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>レポート マネージャーからレポート ビルダー ClickOnce を起動するには  
  
1.  Web ブラウザーで、アドレス バーにレポート サーバーの URL を入力します。 既定では、URL は http://\<*servername*>/レポートです。 レポート マネージャーが開きます。  
  
2.  **[レポート ビルダー]** をクリックします。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>URL を使用してレポート ビルダー ClickOnce を起動するには  
  
1.  Web ブラウザーでアドレス バーに次の URL を入力します。  
  
     http://\<servername>/reportserver/reportbuilder/ReportBuilder_3_0_0_0 アプリケーション  
  
2.  Enter キーを押します。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>レポート ビルダー ClickOnce を SharePoint 統合モードで起動するには  
  
1.  目的のライブラリがある SharePoint サイトに移動します。  
  
2.  ライブラリを開きます。  
  
3.  **[ドキュメント]** をクリックします。  
  
4.  **[新しいドキュメント]** メニューの **[レポート ビルダー レポート]** をクリックします。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
     **メモ**[**新しいドキュメント**] メニューに [レポートの**レポートビルダー**、**レポートビルダーモデル**]、および [**レポートデータソース**] オプションが表示されない場合は、そのコンテンツの種類を SharePoint ライブラリに追加する必要があります。 詳細については、msdn.microsoft.com の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンラインブック](https://go.microsoft.com/fwlink/?LinkId=154888)の「 [SharePoint 統合&#41;モードでのレポートサーバーコンテンツタイプのライブラリへの追加 &#40;Reporting Services](../add-reporting-services-content-types-to-a-sharepoint-library.md) 」を参照してください。  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>[スタート] メニューからレポート ビルダー スタンドアロンを起動するには  
  
1.  [スタート] メニューの [**すべてのプログラム**] をクリック[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]し、[**レポートビルダー**] をクリックします。  
  
2.  **[レポート ビルダー]** をクリックします。  
  
     レポート ビルダーが開き、レポートを作成したり、レポートを開いたりできます。  
  
3.  新しいレポートを作成するには、レポート ビルダーの左上隅の SQL Server アイコンをクリックし、[新規作成] をクリックします。  
  
4.  ローカル コンピューターまたはレポート サーバーに保管された既存のレポートを開くには、左上隅の SQL Server アイコンをクリックし、[開く] をクリックします。  
  
     既存のサーバーの一覧にレポートサーバーが表示されない場合は、[**レポートを開く**] ダイアログボックスを閉じ、レポートビルダーの下部にある [**接続**] をクリックしてサーバーに接続します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のレポート ビルダー](report-builder-in-sql-server-2016.md)  
  
  
