---
title: データ フィード (Power Pivot for SharePoint) の使用 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac7d32ccb99776a85d82c3bc310bc29cdd82954b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027752"
---
# <a name="use-data-feeds-power-pivot-for-sharepoint"></a>データ フィードの使用 (PowerPivot for SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ フィードは、オンライン データ ソースから生成され、宛先のドキュメントやアプリケーションに送信される 1 つ以上のデータ ストリームです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel を使用している場合、データ フィードを利用して、任意のデータ ソースにある既存の企業データやビジネス データを Excel 2010 ブック内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ウィンドウに取り込むことができます。 ブックにデータ フィードをインポートすると、SharePoint サーバーでスケジュールしたデータ更新操作でデータ フィードを参照できます。  
  
 Atom データ フィードをサポートするアプリケーションで組み込みのエクスポート機能を使用しているか、カスタムのデータ サービスを作成して使用しているかに応じて、データ フィードの使用方法は変わってきます。 Atom XML データのパブリッシュおよび読み取りを行うことができるアプリケーションでは、データ フィードとデータ サービスの機構をユーザーに意識させることなく、データをシームレスに転送できます。 ユーザーにとっては、単にアプリケーション間でデータを移動しているだけです。  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および Microsoft SharePoint 2010 では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックで使用できるデータ フィードを提供しています。 このトピックでは、既存のレポートとリストのデータ フィードにアクセスする方法について説明します。  
  
 このトピックには、次のセクションが含まれます。  
  
 [前提条件](#prereq)  
  
 [SharePoint リストからのデータ フィードの作成](#sharepointlist)  
  
 [Reporting Services レポートからのデータ フィードの作成](#rsreport)  
  
 [データ サービス ドキュメントからのデータ フィードの作成](#dsdoc)  
  
##  <a name="prereq"></a> 前提条件  
 データ フィードを Excel 2010 にインポートするには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel が必要です。  
  
 Atom 1.0 形式のデータを提供する Web サービスまたはデータ サービスが必要です。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と SharePoint 2010 では、この形式のデータを提供できます。  
  
 SharePoint リストをデータ フィードとしてエクスポートする前に、ADO.NET Data Services を SharePoint サーバーにインストールする必要があります。 詳細については、「 [SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール方法](http://msdn.microsoft.com/en-us/f32527ae-f623-4e08-adfb-6d3262f5c2ac)」を参照してください。  
  
##  <a name="sharepointlist"></a> SharePoint リストからのデータ フィードの作成  
 SharePoint 2010 ファームでは、SharePoint リストのリスト リボンに [データ フィードとしてエクスポート] ボタンがあります。 このボタンをクリックすると、リストをフィードとしてエクスポートできます。 最良の結果を得るには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クライアント アプリケーションと統合された Excel 2010 がワークステーションに必要です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クライアント アプリケーションは、データ フィードのエクスポートに応答して起動し、リストを含む新しい [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] テーブルを作成します。  
  
1.  SharePoint サイトでリストを開きます。  
  
2.  リスト ツールで、 **[リスト]** をクリックします。  
  
3.  [接続とエクスポート] で、 **[データ フィードとしてエクスポート]** をクリックします。  
  
    > [!NOTE]  
    >  **[データ フィードとしてエクスポート]** ボタンは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]によって SharePoint に追加されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされていないか、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能をアクティブ化していない場合、このボタンは使用できません。  
  
4.  **for Excel がローカルにインストールされている場合は** [開く] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] をクリックします。また、後でインポート操作を行う場合は、 **[保存]** をクリックして .atomsvc ドキュメントをハード ドライブに保存します。  
  
5.  **[開く]** をクリックした場合は、テーブルのインポート ウィザードを使用してデータ フィードをワークシートにインポートします。 データ フィードは新しいテーブルとして [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ウィンドウに追加されます。  
  
 ADO.NET Data Services 3.5.1 が SharePoint サーバーにインストールされていない場合はエラーが発生します。 エラーとその解決方法の詳細については、「 [SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール方法](http://msdn.microsoft.com/en-us/f32527ae-f623-4e08-adfb-6d3262f5c2ac)」を参照してください。  
  
##  <a name="rsreport"></a> Reporting Services レポートからのデータ フィードの作成  
 SQL Server 2008 R2 Reporting Services を配置している場合は、新しい Atom 表示拡張機能を使用して既存のレポートからデータ フィードを生成できます。 最良の結果を得るには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel と統合された Excel 2010 がワークステーションに必要です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クライアント アプリケーションは、データ フィードのエクスポートに応答して起動します。そして、受信したテーブルと列が自動的に追加され、関連付けられます。  
  
 データ フィードをレポートからエクスポートする方法については、[レポート ビルダー ヘルプ ファイル](http://go.microsoft.com/fwlink/?LinkId=154494)の「[1 つのレポートからのデータ フィードの生成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  SharePoint ライブラリにパブリッシュされた [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにレポート データを再インポートする定期的なデータ更新スケジュールを設定するには、レポート サーバーが SharePoint 統合用に構成されている必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint と Reporting Services を併用する場合の詳細については、「[レポート サーバーの構成と管理 (Reporting Services SharePoint モード)](../../reporting-services/report-server-sharepoint/configuration-and-administration-of-a-report-server.md)」を参照してください。  
  
##  <a name="dsdoc"></a> データ サービス ドキュメントからのデータ フィードの作成  
 Atom フィードを生成するカスタム データ サービスを使用している場合は、ユーザーやアプリケーションがデータを利用できるようにする手段としてデータ サービス ドキュメントを設定できます。 *データ サービス ドキュメント* (.atomsvc) ファイルには、データを Atom ワイヤ形式でパブリッシュするオンライン ソースへの 1 つ以上の接続が指定されます。 データ サービス ドキュメントは *データ フィード ライブラリ*に作成できます。このライブラリは、SharePoint サーバーにパブリッシュされたデータ サービス ドキュメントを参照するための共通アクセス ポイントを提供する、特殊な用途のライブラリです。 データ フィード ライブラリ内のデータ サービス ドキュメントにアクセスする権限を持つインフォメーション ワーカーは、ドキュメントの SharePoint URL を参照し、データ フィードをブックとアプリケーションにインポートできます。  
  
1.  サイト管理者によって作成されたデータ フィード ライブラリを開きます。 詳細については、「[データ フィード ライブラリの作成またはカスタマイズ (Power Pivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md)」を参照してください。  
  
2.  [ライブラリ ツール] で **[ドキュメント]** をクリックします。  
  
3.  **[新しいドキュメント]** をクリックします。  
  
4.  ファイル名と説明を指定します。  
  
5.  フィードを提供する 1 つ以上の URL を指定します。  
  
    1.  **[ベース URL]** は省略可能です。 データ サービス ドキュメントが複数のフィードを提供する場合はベース URL を指定してください。 ベース URL には、すべてのフィードに共通する URL の部分 (サーバー名とサイトなど) を指定します。 Reporting Services レポートにデータ サービス ドキュメントを作成している場合、ベース URL はレポート サーバーの URL とレポートになります。  
  
    2.  **[Web サービス URL]** は必須です。 ベース URL せず、この値を含める必要があります`http://`または`https://`アドレス。 ベース URL を指定した場合、Web サービス URL はベース URL の後に続く部分になります。 たとえば、完全な URL が`http://adventure-works/inventory/today.aspx`、ベース URL になります`http://adventure-works/inventory`、および Web サービスの URL は/today.aspx になります。  
  
         Web サービス URL には、データのサブセットを除外または選択するパラメーターを含めることができます。 フィードを提供するアプリケーションまたはサービスは、URL に指定するパラメーターをサポートしている必要があります。  
  
6.  フィードごとに 1 つのテーブルの **[テーブル名]** を入力します。 この値は必須です。 テーブル名は、データ フィードを使用するクライアント アプリケーションによって利用されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel では、インポートしたデータを含む [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ウィンドウのテーブルに名前を付ける際にこのテーブル名が使用されます。  
  
## <a name="see-also"></a>参照  
 [サイト コレクションを対象とした Power Pivot 機能の統合をサーバーの全体管理でアクティブ化する方法](../../analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [データ フィード ライブラリを使用したデータ フィードの共有 (PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/share-data-feeds-using-a-data-feed-library-power-pivot-for-sharepoint.md)  
  
  
