---
title: "データ フィード ライブラリの作成またはカスタマイズ (Power Pivot for SharePoint) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ フィード ライブラリ"
  - "データ フィード [Analysis Services と SharePoint]"
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
caps.latest.revision: 22
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 22
---
# データ フィード ライブラリの作成またはカスタマイズ (Power Pivot for SharePoint)
  *データ フィード ライブラリ*は、特殊な用途の SharePoint ライブラリです。このライブラリでは、Atom データ サービス ドキュメント (.atomsvc) を登録して共有できます。 これらのドキュメントは、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックまたは Atom データ フィード形式をサポートするその他のクライアント アプリケーションに XML データ フィードを提供します。 データ フィード ライブラリは、以下を実行できる点で他の SharePoint ライブラリとは異なります。  
  
-   特定のフィードへの HTTP 接続を指定するために使用される*データ サービス ドキュメント*を作成または編集できます。  
  
-   集中管理された場所でデータ サービス ドキュメントを共有および管理できます。  
  
-   データ サービス ドキュメントがアイコン () で視覚的に示されるため、サービス ドキュメントを同じライブラリに格納されている他のドキュメントと簡単に区別できます。 ![GMNI_IconDataFeed](../../analysis-services/power-pivot-sharepoint/media/gmni-icondatafeed.png "GMNI_IconDataFeed")  
  
 データ フィード ライブラリには、データ フィード自体ではなく、常にデータ サービス ドキュメント (.atomsvc) ファイルが格納されます。 静的な XML データで構成されるデータ フィードとは異なり、データ サービス ドキュメントでは、要求時にフィードを生成するサービスまたはアプリケーションの URL を指定します。そのため、反復可能なインポート操作で接続情報を再利用できます。  
  
 このトピックには、次のセクションが含まれます。  
  
 [前提条件](#prereq)  
  
 [新しいデータ フィード ライブラリの作成](#createlib)  
  
 [任意のライブラリへのデータ フィード コンテンツ タイプの追加](#addtolib)  
  
##  <a name="prereq"></a> 前提条件  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能の統合を、データ フィード ライブラリを作成するサイトに対してアクティブ化する必要があります。 データ フィード ライブラリ テンプレート タイプが使用できない場合、この前提条件を満たしていないことが考えられます。 詳細については、「[サイト コレクションを対象とした Power Pivot 機能の統合をサーバーの全体管理でアクティブ化する方法](../../analysis-services/power-pivot-sharepoint/activate power pivot integration for site collections in ca.md)」を参照してください。  
  
 ライブラリを作成するには、サイト所有者である必要があります。  
  
##  <a name="createlib"></a> 新しいデータ フィード ライブラリの作成  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのデータ フィードを有効にするには、最初にデータ フィード ライブラリを作成します。 データ サービス ドキュメントのアプリケーション ページと管理ページはデータ フィード ライブラリによって提供されるため、新しいドキュメントを作成する前にこのライブラリを用意する必要があります。  
  
 データ フィード ライブラリは、組み込みのテンプレートと、データ サービス ドキュメントのプロパティと動作を定義する事前に構成された*データ サービス ドキュメントのコンテンツのタイプ*に基づきます。  
  
1.  ページの左上にある **[サイトの操作]** をクリックします。  
  
2.  **[その他のオプション…]** をクリックします。  
  
3.  [ライブラリ] の **[データ フィード ライブラリ]** をクリックします。  
  
4.  名前、説明、起動、およびバージョン設定を入力します。 このライブラリがデータ サービス ドキュメントのストレージであることがユーザーにわかるように説明情報を入力してください。  
  
5.  **[作成]**をクリックします。  
  
 データ フィード ライブラリへのリンクが、現在のサイトのナビゲーションのクイック起動ペインに表示されます。  
  
 ライブラリを作成した後、そのライブラリを使用してデータ サービス ドキュメントを作成できます。 詳細については、「[データ フィードの使用 (PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/use-data-feeds-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="addtolib"></a> 任意のライブラリへのデータ フィード コンテンツ タイプの追加  
 専用のデータ フィード ライブラリは作成せずに、SharePoint サイトからデータ サービス ドキュメントを作成して管理する場合は、データ サービス ドキュメント (.atomsvc) ファイルの共有に使用する任意のライブラリ用にデータ サービス ドキュメント コンテンツ タイプを手動で追加して構成できます。  
  
 コンテンツ タイプを追加および構成するには、管理リスト権限以上の権限が必要です。 この権限は、デザイン権限レベル以上の権限に組み込まれています。  
  
 データ フィード登録ドキュメントを作成または編集するライブラリごとに、次の手順を繰り返す必要があります。  
  
#### 手順 1: コンテンツ タイプを管理できるようにする  
  
1.  複数のコンテンツ タイプを有効にする対象のドキュメント ライブラリを開きます。  
  
2.  SharePoint リボンで、[ライブラリ ツール] の **[ライブラリ]** をクリックします。  
  
3.  **[設定]** をクリックします。  
  
4.  **[ライブラリの設定]**をクリックします。  
  
5.  [全般設定] の **[詳細設定]** をクリックします。  
  
6.  [コンテンツ タイプ] の [コンテンツ タイプの管理を許可する]  セクションで **[はい]** をクリックします。  
  
7.  **[OK]**をクリックします。  
  
#### 手順 2: データ サービス ドキュメント コンテンツ タイプを追加する  
  
1.  [コンテンツ タイプ] セクションの **[既存のサイト コンテンツ タイプから追加]** をクリックします。 このページが表示されない場合は、サイトに戻って [ライブラリ ツール] の **[ライブラリ]** をクリックし、**[ライブラリの設定]** をクリックします。  
  
2.  [コンテンツ タイプ] の **[既存のサイト コンテンツ タイプから追加]** をクリックします。  
  
3.  [サイト コンテンツ タイプの選択元] で **[ビジネス インテリジェンス]** をクリックします。  
  
4.  [利用可能なサイト コンテンツ タイプ] で **[データ サービス ドキュメント]** をクリックしてから **[追加]** をクリックし、選択したコンテンツ タイプを [追加するコンテンツ タイプ] ボックスの一覧に追加します。  
  
5.  **[OK]**をクリックします。  
  
#### 手順 3: データ サービス ドキュメントの構成を確認する  
  
1.  サイトのホーム ページを開きます。  
  
2.  ライブラリを開きます。  
  
3.  SharePoint リボンで、**[ドキュメント]** をクリックします。  
  
4.  [新しいドキュメント] の下矢印をクリックし、**[データ サービス ドキュメント]** をクリックします。 [新しいデータ サービス ドキュメント] ページが表示されます。  
  
## 参照  
 [データ フィードの使用 (PowerPivot for SharePoint)](../../analysis-services/power-pivot-sharepoint/use-data-feeds-power-pivot-for-sharepoint.md)   
 [Power Pivot データ フィード ライブラリの削除](../../analysis-services/power-pivot-sharepoint/delete-a-power-pivot-data-feed-library.md)   
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Power Pivot データ フィード](../../analysis-services/power-pivot-sharepoint/power-pivot-data-feeds.md)  
  
  