---
title: レポート ビルダー (レポート ビルダー) を起動 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 50
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: bb09858869f76fd32a1e05151eef48870f96f68a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176567"
---
# <a name="start-report-builder-report-builder"></a>レポート ビルダーの起動 (レポート ビルダー)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] スタンドアロンが含まれていますと[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]レポート ビルダーのバージョン。 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンは、ネイティブ モードまたは SharePoint 統合モードでインストールされた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共に使用できます。  
  
> [!NOTE]  
>  レポート ビルダーは、Itanium 64 ベースのコンピューターにはインストールできません。 これに適用されます、[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]およびレポート ビルダーのスタンドアロン バージョンです。  
  
 場合、[!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]表示されるレポート ビルダーのバージョンが以前のバージョンのレポート ビルダーを使用するには、レポート マネージャーおよび SharePoint サイトを更新できる管理者に問い合わせて、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]バージョンのレポート ビルダー  
  
 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] バージョンのレポート ビルダーを使用して、SharePoint にパブリッシュされている [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ブックについてのレポートを作成することもできます。 レポート ビルダーの使用の詳細については[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]を参照してください[PowerPivot データを使用した Reporting Services レポートを作成する](http://go.microsoft.com/fwlink/?LinkId=185238)technet.microsoft.com のです。  
  
 レポート ビルダー スタンドアロンを起動する、**開始**メニューで、ローカル コンピューター、ユーザーまたは管理者は、ツールを使用するには前に、コンピューターに直接のレポート ビルダーをインストールする必要があります。 スタンドアロン バージョンは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインストール時にインストールされません。別途ダウンロードして、インストールする必要があります。 レポート ビルダーをダウンロードするを参照してください。 [Microsoft® SQL Server® 2012 レポート ビルダー](http://go.microsoft.com/fwlink/?LinkId=401502)です。  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>レポート マネージャーからレポート ビルダー ClickOnce を起動するには  
  
1.  Web ブラウザーで、アドレス バーにレポート サーバーの URL を入力します。 既定の URL は http://\<*servername*>/reports です。 レポート マネージャーが開きます。  
  
2.  **[レポート ビルダー]** をクリックします。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>URL を使用してレポート ビルダー ClickOnce を起動するには  
  
1.  Web ブラウザーでアドレス バーに次の URL を入力します。  
  
     http://\<servername >/reportserver/reportbuilder/ReportBuilder_3_0_0_0.application  
  
2.  Enter キーを押します。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>レポート ビルダー ClickOnce を SharePoint 統合モードで起動するには  
  
1.  目的のライブラリがある SharePoint サイトに移動します。  
  
2.  ライブラリを開きます。  
  
3.  **[ドキュメント]** をクリックします。  
  
4.  **[新しいドキュメント]** メニューの **[レポート ビルダー レポート]** をクリックします。  
  
     レポート ビルダーが開き、レポート サーバー上でレポートを作成したり、レポートを開いたりできます。  
  
     **注**場合、**新しいドキュメント**メニューに表示されない、**レポート ビルダー レポート**、**レポート ビルダーのモデル**、および**レポートデータソース**オプション、そのコンテンツの種類を SharePoint ライブラリに追加する必要があります。 詳細については、次を参照してください[追加レポート サーバー コンテンツ タイプをライブラリに&#40;Reporting Services SharePoint 統合モードで&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][オンライン ブック](http://go.microsoft.com/fwlink/?LinkId=154888)上。msdn.microsoft.com の「します。  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>[スタート] メニューからレポート ビルダー スタンドアロンを起動するには  
  
1.  [スタート] メニューをクリックして**すべてのプログラム**、クリックして[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]**レポート ビルダー**です。  
  
2.  **[レポート ビルダー]** をクリックします。  
  
     レポート ビルダーが開き、レポートを作成したり、レポートを開いたりできます。  
  
3.  新しいレポートを作成するには、レポート ビルダーの左上隅の SQL Server アイコンをクリックし、[新規作成] をクリックします。  
  
4.  ローカル コンピューターまたはレポート サーバーに保管された既存のレポートを開くには、左上隅の SQL Server アイコンをクリックし、[開く] をクリックします。  
  
     既存のサーバーの一覧で、レポート サーバーが見つからない場合は閉じます、**レポートを開く** ダイアログ ボックスに入力し**接続**サーバーへの接続にレポート ビルダーの下部にあります。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 のレポート ビルダー](report-builder-in-sql-server-2016.md)  
  
  