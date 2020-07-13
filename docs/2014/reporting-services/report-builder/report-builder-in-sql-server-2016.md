---
title: SQL Server 2014 | のレポートビルダーMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f03f0f4c210408324ee4a2cae255ba805e0377a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107708"
---
# <a name="report-builder-in-sql-server-2014"></a>SQL Server 2014 のレポート ビルダー
  レポートビルダーは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 環境での作業を好むビジネスユーザー向けのレポート作成環境です。 レポートをデザインする際には、データの取得場所、取得するデータ、およびデータの表示方法を指定します。 レポートを実行すると、指定した情報がすべてレポート プロセッサに渡されます。レポート プロセッサは、データを取得し、それをレポート レイアウトに結合して、レポートを生成します。 レポート ビルダーでレポートをプレビューすることも、レポート サーバーまたは SharePoint 統合モードのレポート サーバーにレポートをパブリッシュして、他のユーザーがそこからレポートを実行できるようにすることもできます。  
  
 この図に示すレポートでは、行グループ、列グループ、スパークライン、インジケーター、およびコーナー セルの概要円グラフが含まれたマトリックスが使用されています。色と円サイズで表される 2 組の地理データが含まれた地図も使用されています。  
  
 ![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")  
  
##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a> レポート作成の開始  
  
-   チームの他のユーザーによって作成された**レポートパーツを使用して、レポートを開始**します。 レポート パーツとは、レポート サーバー、またはレポート サーバーに統合されている SharePoint サイトに、個別にパブリッシュされたレポート アイテムです。 これらは、他のレポートに再利用できます。 テーブル、マトリックス、グラフ、画像などのレポート アイテムを、レポート パーツとしてパブリッシュできます。  
  
-   チーム内の他のユーザーによって作成された**共有データセットを使用**して開始します。 共有データセットは、共有データ ソースに基づくクエリで、レポート サーバーまたはレポート サーバーに統合されている SharePoint サイトに保存されます。  
  
-   **テーブル、マトリックス、グラフの各ウィザードから開始**します。 データ ソース接続を選択したり、フィールドをドラッグ アンド ドロップしてデータセット クエリを作成したりできます。また、レイアウトとスタイルを選択して、レポートをカスタマイズできます。  
  
-   **マップ ウィザードから開始** して、地図や幾何図形を背景として集計データを表示するレポートを作成します。 マップ データには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリや Environmental Systems Research Institute, Inc. (ESRI) シェープファイルの空間データを指定できます。 また、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing のマップ タイルの背景を追加することもできます。  
  

  
##  <a name="design-your-report"></a><a name="DesignRept"></a> レポートのデザイン  
  
-   **テーブル、マトリックス、グラフ、および自由形式のレポート レイアウトのレポートを作成します。** 列単位のデータにはテーブル形式のレポート、集約されたデータにはマトリックス形式のレポート (クロス集計レポートや PivotTable レポートなど)、グラフィック データにはグラフ形式のレポート、これ以外のすべてのデータには自由形式のレポートを作成します。 レポートでは、Web ベースの動的アプリケーションのリスト、グラフィック、およびコントロールと共に、他のレポートやグラフを埋め込むことができます。  
  
-   **さまざまなデータ ソースからレポートを作成します。** マネージデータプロバイダー、OLE DB プロバイダー、または ODBC データソース[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を持つ任意のデータソースの種類のデータを使用して、レポートを作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、Oracle、Hyperion、およびその他のデータベースのリレーショナル データおよび多次元データを使用するレポートを作成できます。 XML データ処理拡張機能を使用すると、任意の XML データ ソースからデータを取得できます。 テーブル値関数を使用すると、カスタム データ ソースをデザインできます。  
  
-   **既存のレポートを変更します。** レポートビルダーを使用すると、レポートデザイナーで[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]作成されたレポートをカスタマイズおよび更新できます。  
  
-   データのフィルター処理、グループ化と並べ替え、または数式や式の追加によって、**データを変更**します。  
  
-   データをビジュアルな形式でまとめ、大量の集計情報がひとめでわかるようにするため、**グラフ、ゲージ、スパークライン、およびインジケーターを追加します。**  
  
-   ドキュメント マップ、表示/非表示を切り替えるボタン、サブレポートおよび詳細レポートへのドリルスルー リンクなど、**対話機能を追加します** 。 パラメーターとフィルターを使用すると、カスタマイズされたビューのデータをフィルター処理できます。  
  
-   外部コンテンツなど、**画像やその他のリソースを埋め込んだり参照したりします。**  
  

  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a> レポートの管理  
  
-   コンピューターまたはレポート サーバーに**レポートの定義を保存** し、そこでレポートを管理し、他のユーザーと共有します。  
  
-   レポートを開くとき、またはレポートを開いた後、**表示形式を選択** します。 Web 指向、ページ指向、およびデスクトップ アプリケーションの形式を選択できます。 形式には、HTML、MHTML、PDF、XML、CSV、TIFF、Word、および Excel があります。  
  
-   **サブスクリプションを設定します。** レポート サーバーまたは SharePoint 統合モードのレポート サーバーにレポートをパブリッシュした後、特定の時刻にレポートを実行したり、レポート履歴の作成や、電子メール サブスクリプションの設定を行うなど、レポートに対するさまざまな構成を行うことができます。  
  
-   Reporting Services の Atom 表示拡張機能を使用して、レポートから**データ フィードを生成** します。  
  
> [!NOTE]  
>  パブリッシュされたレポートは、レポート サーバー上または SharePoint 統合モードのレポート サーバー上で、レポート サーバー管理者が管理します。 レポート サーバー管理者は、セキュリティの定義、プロパティの設定、および操作 (レポート履歴や電子メールによるレポート配信など) のスケジュール設定を行うことができます。 共有スケジュールおよび共有データ ソースを作成し、それらを一般的な用途で使用できます。 管理者はさらに、レポート サーバーのすべてのフォルダーの管理も行います。 実行できる管理タスクは、ユーザー権限により異なります。  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a>このセクションの説明  
 [SQL Server 2014 レポート ビルダーの新機能](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 このバージョンのレポートビルダーの新機能 (マップなど) について説明します。  
  
 [チュートリアル: オフラインでのクイック グラフ レポートの作成](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 レポート ビルダーとレポートの作成に使用できるウィザードを紹介します。 このチュートリアルには、作業用の一連のデータが用意されているため、データ ソースに接続せずに実習を開始できます。  
  
 [レポートの計画 (レポート ビルダー)](../report-design/planning-a-report-report-builder.md)  
 レポートを作成する前の考慮事項について説明します。  
  
 [レポート作成の概念 (レポート ビルダーおよび SSRS)](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 レポート ビルダーのドキュメント全体で使用する主要な概念について説明します。  
  
 [レポート デザイン ビュー &#40;レポート ビルダー&#41;](report-design-view-report-builder.md)  
 レポート デザイン ビューの各ペインと領域について説明します。  
  
 [共有データセット デザイン ビュー (レポート ビルダー)](shared-dataset-design-view-report-builder.md)  
 共有データセット デザイン ビューの各ペインと領域について説明します。  
  
 [キーボード ショートカット (レポート ビルダー)](keyboard-shortcuts-report-builder.md)  
 レポート ビルダーでレポートのナビゲーションとデザインに使用できるショートカット キーについて説明します。  
  
 [&#40;レポートビルダーを開始レポートビルダー&#41;](start-report-builder.md)  
 レポート ビルダーの 2 つの異なるバージョン (スタンドアロンと [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]) を起動する方法について説明します。  
  
  
