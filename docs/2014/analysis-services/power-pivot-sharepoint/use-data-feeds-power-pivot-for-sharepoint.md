---
title: データフィードを使用する (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 50140fdf-6fd1-41a1-9c14-8ecfb97ba2e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6efccad47f0d6670c87aeb1e9cc9ef9ec654a138
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070906"
---
# <a name="use-data-feeds-powerpivot-for-sharepoint"></a>データ フィードの使用 (PowerPivot for SharePoint)
  データ フィードは、オンライン データ ソースから生成され、宛先のドキュメントやアプリケーションに送信される 1 つ以上のデータ ストリームです。 PowerPivot for Excel を使用している場合、データ フィードを利用して、任意のデータ ソースにある既存の企業データやビジネス データを Excel 2010 ブック内の PowerPivot ウィンドウに取り込むことができます。 ブックにデータ フィードをインポートすると、SharePoint サーバーでスケジュールしたデータ更新操作でデータ フィードを参照できます。  
  
 Atom データ フィードをサポートするアプリケーションで組み込みのエクスポート機能を使用しているか、カスタムのデータ サービスを作成して使用しているかに応じて、データ フィードの使用方法は変わってきます。 Atom XML データのパブリッシュおよび読み取りを行うことができるアプリケーションでは、データ フィードとデータ サービスの機構をユーザーに意識させることなく、データをシームレスに転送できます。 ユーザーにとっては、単にアプリケーション間でデータを移動しているだけです。  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]および Microsoft SharePoint 2010 では、PowerPivot ブックで使用できるデータフィードを提供しています。 このトピックでは、既存のレポートとリストのデータ フィードにアクセスする方法について説明します。  
  
 このトピックには、次のセクションが含まれます。  
  
 [前提条件](#prereq)  
  
 [SharePoint リストからのデータ フィードの作成](#sharepointlist)  
  
 [Reporting Services レポートからのデータフィードの作成](#rsreport)  
  
 [データサービスドキュメントからのデータフィードの作成](#dsdoc)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> 前提条件  
 データ フィードを Excel 2010 にインポートするには、PowerPivot for Excel が必要です。  
  
 Atom 1.0 形式のデータを提供する Web サービスまたはデータ サービスが必要です。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]と SharePoint 2010 では、この形式でデータを提供でき[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ます。  
  
 SharePoint リストをデータ フィードとしてエクスポートする前に、ADO.NET Data Services を SharePoint サーバーにインストールする必要があります。 詳細については、「 [SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール方法](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)」を参照してください。  
  
##  <a name="create-a-data-feed-from-a-sharepoint-list"></a><a name="sharepointlist"></a>SharePoint リストからのデータフィードの作成  
 SharePoint 2010 ファームでは、SharePoint リストのリスト リボンに [データ フィードとしてエクスポート] ボタンがあります。 このボタンをクリックすると、リストをフィードとしてエクスポートできます。 最良の結果を得るには、PowerPivot クライアント アプリケーションと統合された Excel 2010 がワークステーションに必要です。 PowerPivot クライアント アプリケーションは、データ フィードのエクスポートに応答して起動し、リストを含む新しい PowerPivot テーブルを作成します。  
  
1.  SharePoint サイトでリストを開きます。  
  
2.  リスト ツールで、 **[リスト]** をクリックします。  
  
3.  [接続とエクスポート] で、 **[データ フィードとしてエクスポート]** をクリックします。  
  
    > [!NOTE]  
    >  [**データフィードとしてエクスポート**] ボタンは、PowerPivot を使って SharePoint に追加されます。 PowerPivot for SharePoint がインストールされていないか、PowerPivot 機能をアクティブ化していない場合、このボタンは使用できません。  
  
4.  PowerPivot for Excel がローカルにインストールされている場合は [**開く**] をクリックし、後でインポート操作のために .atomsvc ドキュメントをハードドライブに保存する場合は [**保存**] をクリックします。  
  
5.  **[開く]** をクリックした場合は、テーブルのインポート ウィザードを使用してデータ フィードをワークシートにインポートします。 データ フィードは新しいテーブルとして PowerPivot ウィンドウに追加されます。  
  
 ADO.NET Data Services 3.5.1 が SharePoint サーバーにインストールされていない場合はエラーが発生します。 エラーとその解決方法の詳細については、「 [SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール方法](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md)」を参照してください。  
  
##  <a name="create-a-data-feed-from-a-reporting-services-report"></a><a name="rsreport"></a> Reporting Services レポートからのデータ フィードの作成  
 SQL Server 2008 R2 Reporting Services を配置している場合は、新しい Atom 表示拡張機能を使用して既存のレポートからデータ フィードを生成できます。 最適な結果を得るには、PowerPivot for Excel と統合された Excel 2010 がワークステーションに必要です。 PowerPivot クライアント アプリケーションは、データ フィードのエクスポートに応答して起動します。そして、受信したテーブルと列が自動的に追加され、関連付けられます。  
  
 データ フィードをレポートからエクスポートする方法については、[レポート ビルダー ヘルプ ファイル](https://go.microsoft.com/fwlink/?LinkId=154494)の「[1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  SharePoint ライブラリにパブリッシュされた PowerPivot ブックにレポート データを再インポートする定期的なデータ更新スケジュールを設定するには、レポート サーバーが SharePoint 統合用に構成されている必要があります。 PowerPivot for SharePoint と Reporting Services の使用方法の詳細については、「[レポートサーバーの構成と管理」 &#40;Reporting Services SharePoint モード&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md)」を参照してください。  
  
##  <a name="create-a-data-feed-from-a-data-service-document"></a><a name="dsdoc"></a> データ サービス ドキュメントからのデータ フィードの作成  
 Atom フィードを生成するカスタム データ サービスを使用している場合は、ユーザーやアプリケーションがデータを利用できるようにする手段としてデータ サービス ドキュメントを設定できます。 *データ サービス ドキュメント* (.atomsvc) ファイルには、データを Atom ワイヤ形式でパブリッシュするオンライン ソースへの 1 つ以上の接続が指定されます。 データ サービス ドキュメントは *データ フィード ライブラリ*に作成できます。このライブラリは、SharePoint サーバーにパブリッシュされたデータ サービス ドキュメントを参照するための共通アクセス ポイントを提供する、特殊な用途のライブラリです。 データ フィード ライブラリ内のデータ サービス ドキュメントにアクセスする権限を持つインフォメーション ワーカーは、ドキュメントの SharePoint URL を参照し、データ フィードをブックとアプリケーションにインポートできます。  
  
1.  サイト管理者によって作成されたデータ フィード ライブラリを開きます。 詳細については、「[データフィードライブラリの作成またはカスタマイズ &#40;PowerPivot for SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md)」を参照してください。  
  
2.  [ライブラリ ツール] で **[ドキュメント]** をクリックします。  
  
3.  **[新しいドキュメント]** をクリックします。  
  
4.  ファイル名と説明を指定します。  
  
5.  フィードを提供する 1 つ以上の URL を指定します。  
  
    1.  **[ベース URL]** は省略可能です。 データ サービス ドキュメントが複数のフィードを提供する場合はベース URL を指定してください。 ベース URL には、すべてのフィードに共通する URL の部分 (サーバー名とサイトなど) を指定します。 Reporting Services レポートにデータ サービス ドキュメントを作成している場合、ベース URL はレポート サーバーの URL とレポートになります。  
  
    2.  **[Web サービス URL]** は必須です。 ベース URL を指定しない場合、この値のアドレスには http:// または https:// を含める必要があります。 ベース URL を指定した場合、Web サービス URL はベース URL の後に続く部分になります。 たとえば、完全な URL がhttp://adventure-works/inventory/today.aspxの場合、ベース url はhttp://adventure-works/inventoryになり、Web サービスの url は/today.aspx なりになります。  
  
         Web サービス URL には、データのサブセットを除外または選択するパラメーターを含めることができます。 フィードを提供するアプリケーションまたはサービスは、URL に指定するパラメーターをサポートしている必要があります。  
  
6.  フィードごとに 1 つのテーブルの **[テーブル名]** を入力します。 この値は必須です。 テーブル名は、データ フィードを使用するクライアント アプリケーションによって利用されます。 PowerPivot for Excel では、インポートしたデータを含む PowerPivot ウィンドウのテーブルに名前を付ける際にこのテーブル名が使用されます。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理でサイトコレクションの PowerPivot 機能の統合をアクティブ化する](activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [データフィードライブラリを使用してデータフィードを共有する &#40;PowerPivot for SharePoint&#41;](share-data-feeds-using-a-data-feed-library-power-pivot-for-sharepoint.md)  
  
  
