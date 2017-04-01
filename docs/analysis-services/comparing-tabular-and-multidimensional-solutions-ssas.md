---
title: "Comparing Tabular and Multidimensional Solutions (SSAS) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 76ee5e96-6a04-49af-a88e-cb5fe29f2e9a
caps.latest.revision: 49
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 47
---
# Comparing Tabular and Multidimensional Solutions (SSAS)
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、多次元、テーブル、Power Pivot など、ビジネス インテリジェンス セマンティック モデルを作成するためのアプローチが複数用意されています。  
  
 複数のアプローチにより、さまざまなビジネスとユーザーの要件に応じたモデリング エクスペリエンスを実現できます。 多次元モデルは、オープン スタンダードに組み込まれている成熟したテクノロジで、多くの BI ソフトウェア ベンダーで採用されていますが、習得が難しい場合があります。 テーブル モデルは、多くの開発者にとって直感的なリレーショナル モデリング アプローチを提供します。 Power Pivot モデルはさらにシンプルで、Excel 形式でビジュアル データ モデリングを提供するほか、SharePoint 経由でサーバーのサポートが可能になっています。  
  
 すべてのモデルが Analysis Services インスタンスで実行されているデータベースとして配置され、1 つのデータ プロバイダー セットを使用してクライアント ツールでアクセスします。また、Excel、Reporting Services、Power BI、および他のベンダーの BI ツールによって、対話型レポートや静的レポートで視覚化されます。  
  
 メモリ アーキテクチャとメタデータの違いにより、モデルの種類を入れ替えることはできませんが、テーブル 1050 ～ 1103 からテーブル 1200 へのモデル アップグレードは非常に簡単です。また、Power Pivot をインポートして、まったく新しいモデルをテーブル プロジェクトとして作成することもできます。  
  
 テーブル ソリューションと多次元ソリューションは、スタンドアロンの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスで実行される企業の BI プロジェクトを対象としており、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] を使用して作成されます。 両方のソリューションで、BI クライアントと簡単に統合できる高パフォーマンス分析データベースが作成されます。 ただし、各ソリューションの作成、使用、配置の方法は異なります。 このトピックでは、ユーザーが適切なアプローチを特定できるように、この 2 つの種類を比較します。  
  
 新しい開発プロジェクトの場合は、一般的には、テーブル ソリューションをお勧めします。 テーブル ソリューションは、デザイン、テスト、配置をよりすばやく行うことができます。また、Microsoft の最新のセルフサービス BI アプリケーションとクラウド サービスで使用するのにも適しています。  
  
##  <a name="a-namebkmkoverviewa-overview-of-modeling-types"></a><a name="bkmk_overview"></a> モデリングの種類の概要  
 Analysis Services を初めて使用する場合は、 次の表で、各モデルのアプローチの概要と、最初のリリース媒体を確認してください。  
  
||||  
|-|-|-|  
|**種類**|**モデリングの説明**|**リリース済み**|  
|多次元|OLAP モデリング構造 (キューブ、ディメンション、メジャー)。|SQL Server 2000 以降|  
|テーブル|リレーショナル モデリング構造 (モデル、テーブル、列)。<br /><br /> 内部的には、OLAP モデリング構造 (キューブ、ディメンション、メジャー) からメタデータが継承されます。 コードとスクリプトは OLAP メタデータを使用します。|SQL Server 2012 以降 (互換性レベル 1050 ～ 1103) <sup>1</sup>|  
|SQL Server 2016 のテーブル|リレーショナル モデリング構造 (モデル、テーブル、列)。スクリプトおよびコードで表形式メタデータ オブジェクト定義によって指定されます。|SQL Server 2016 (互換性レベル 1200)|  
|Power Pivot|もともとはアドインですが、Excel に完全に統合されました。 内部テーブル インフラストラクチャにおけるビジュアル モデリングのみ。 Power Pivot モデルを SSDT にインポートして、Analysis Services インスタンスで実行される新しいテーブル モデルを作成できます。|Excel と Power Pivot BI Desktop を使用|  
  
 <sup>1</sup> SQL Server 2012 で導入された互換性レベルは、新しいテーブル メタデータ エンジンと、上位レベルでのみ利用可能なシナリオ有効化機能のサポートのために、現在のリリースで重要です。 注目すべき進歩としては、DirectQuery、スクリプト、プログラミング機能などが挙げられます。 詳細については、「[Analysis Services の新機能](../analysis-services/what-s-new-in-analysis-services.md)」を参照してください。  
  
##  <a name="a-namebkmkmodelsa-model-features"></a><a name="bkmk_models"></a> モデルの機能  
  次の表は、機能の利用の可否をモデルごとにまとめたものです。 この一覧で、必要な機能が、構築しようとしているモデルの種類で利用できるかどうかを確認してください。  
  
|||||  
|-|-|-|-|  
||多次元|テーブル|Power Pivot|  
|アクション|可|いいえ|いいえ|  
|集計|可|いいえ|いいえ|  
|計算列|いいえ|[ユーザー アカウント制御]|可|  
|計算されるメジャー|可|[ユーザー アカウント制御]|可|  
|計算テーブル|いいえ|可 <sup>1</sup>|いいえ|  
|カスタム アセンブリ|可|いいえ|いいえ|  
|カスタム ロールアップ|可|いいえ|いいえ|  
|既定のメンバー|可|いいえ|いいえ|  
|表示フォルダー|可|可 <sup>1</sup>|いいえ|  
|Distinct Count|可|○ (DAX 経由)|○ (DAX 経由)|  
|ドリルスルー|可|○ (詳細情報が別個のワークシートに表示される)|可|  
|階層|はい|[ユーザー アカウント制御]|はい|  
|KPI|はい|[ユーザー アカウント制御]|可|  
|リンク オブジェクト|可|○ (リンク テーブル)|いいえ|  
|多対多リレーションシップ|可|いいえ (ただし、互換性レベル 1200 では[双方向クロス フィルター](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)があります)|いいえ|  
|名前付きセット|可|いいえ|いいえ|  
|親子階層|可|○ (DAX 経由)|○ (DAX 経由)|  
|パーティション|可|[ユーザー アカウント制御]|はい|  
|パースペクティブ|はい|[ユーザー アカウント制御]|可|  
|準加法メジャー|はい|[ユーザー アカウント制御]|はい|  
|翻訳|[可](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|可|[可](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)|  
|ユーザー定義階層|可|[ユーザー アカウント制御]|可|  
|[書き戻し]|可|いいえ|いいえ|  
  
 <sup>1</sup> テーブル モデルにおける機能の違いの詳細については、「[Analysis Services でのテーブル モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。  
  
##  <a name="a-namebkmkdsa-data-considerations"></a><a name="bkmk_ds"></a> データに関する考慮事項  
 テーブル モデルと多次元モデルの両方が、外部ソースからインポートしたデータを使用します。 どの種類のモデルがデータに最適であるかを判断する際に主に考慮しなければならないのが、インポートする必要があるデータの量と種類です。  
  
 **圧縮**  
  
 テーブル ソリューションと多次元ソリューションではデータ圧縮が使用されるため、Analysis Services データベースのサイズがデータのインポート元のデータ ウェアハウスに比べて小さくなります。 実際の圧縮は、基になるデータの特性によって異なるので、データが処理されてクエリで使用された後にどの程度のディスクおよびメモリがソリューションに必要なのかを正確に知る方法はありません。  
  
 多くの Analysis Services 開発者が使用する目安は、多次元データベースの 1 次記憶域が元のデータの約 3 分の 1 のサイズになるというものです。 テーブル データベースでは、特にデータの大部分がファクト テーブルからインポートされる場合、データをさらに小さく圧縮できることもあります (約 10 分の 1 のサイズ)。  
  
 **モデルとリソースの差のサイズ (メモリ内またはディスク)**  
  
 Analysis Services データベースのサイズは、そのデータベースの実行に使用可能なリソースによってのみ制限されます。 また、モデルの種類とストレージ モードも、データベースがどの程度大きくなるかに影響します。  
  
 テーブル データベースは、In-Memory モード、またはクエリ実行を外部データベースにオフロードする DirectQuery モードで実行されます。 テーブル インメモリ分析については、データベースは完全にメモリ内に格納されます。つまり、すべてのデータのほかに、クエリ サポート用に作成された追加のデータ構造を読み込めるだけのメモリが確保されている必要があります。  
  
 このリリースで強化された DirectQuery では制限が少なくなり、パフォーマンスも向上しました。 ストレージとクエリの実行にバックエンドのリレーショナル データベースを利用することで、大規模なテーブル モデル構築が以前よりも現実的なものになっています。  
  
 これまでは、実稼働環境で最大の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースは多次元モデルで、処理とクエリのワークロードが専用ハードウェアで個別に実行され、それぞれが個別の使用目的で最適化されていました。  これを急速に追っているのがテーブル データベースで、DirectQuery の新しい強化機能により、その差はますます縮まっています。  
  
 多次元モデルでは、ROLAP によってデータ ストレージとクエリ実行のオフロードを利用できます。   クエリ サーバーで行セットをキャッシュし、古いものはページ アウトできます。 メモリとディスク リソースをバランスよく効率的に使用できることに惹かれ、多次元ソリューションを利用している顧客も少なくありません。  
  
 負荷が高い場合、どちらのソリューションでも、Analysis Services によるデータのキャッシュ、格納、スキャン、クエリに応じて必要なディスクとメモリが増加すると予想されます。 メモリ ページング オプションの詳細については、「[メモリのプロパティ](../analysis-services/server-properties/memory-properties.md)」を参照してください。 スケールの詳細については、「[Analysis Services の高可用性とスケーラビリティ](../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)」を参照してください。  
  
 Power Pivot for Excel では、ファイル サイズが 2 GB に制限されています。これは、Power Pivot for Excel で作成したブックを SharePoint にアップロードできるようにするためです (SharePoint ではファイルの最大アップロード サイズが設定されます)。 このファイル サイズの制限を回避することが、Power Pivot ブックをスタンドアロンの Analysis Services インスタンスのテーブル ソリューションに移行する主な理由の 1 つになります。 ファイルの最大アップロード サイズの構成の詳細については、「[アップロードするファイルの最大サイズの構成 (Power Pivot for SharePoint)](../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)」を参照してください。  
  
 **サポートされるデータ ソース**  
  
 多次元ソリューションでは、ネイティブおよびマネージ OLE DB プロバイダーを使用してリレーショナル データ ソースからデータをインポートできます。  
  
 テーブル モデルは、リレーショナル データ ソース、データ フィード、およびいくつかのドキュメント形式からデータをインポートできます。 テーブル モデルで、OLE DB for ODBC プロバイダーを使用することもできます。  
  
 各モデルにインポートできる外部データ ソースの一覧については、以下のトピックを参照してください。  
  
-   [サポートされるデータ ソース &#40;SSAS - 多次元&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
-   [サポートされているデータ ソース &#40;SSAS テーブル&#41;](../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
##  <a name="a-namebkmklanga-query-and-scripting-language-support"></a><a name="bkmk_lang"></a> クエリおよびスクリプト言語のサポート  
 Analysis Services には MDX、DMX、DAX、XML/A、ASSL、および TMSL が用意されています。 これらの言語のサポート状況は、モデルの種類によって異なる場合があります。 クエリとスクリプト言語の要件が重要な検討事項である場合は、次の一覧を参考にしてください。  
  
-   Power Pivot ブックは、計算には DAX を使用し、クエリには DAX または MDX を使用します。  
  
-   テーブル モデル データベースは、DAX の計算、DAX クエリ、および MDX クエリをサポートします。 これは、すべての互換性レベルに当てはまります。 スクリプト言語は、互換性レベル 1050 ～ 1103 の場合は ASSL (XMLA 経由)、互換性レベル 1200 の場合は TMSL (XMLA 経由) です。  
  
-   多次元モデル データベースは、MDX の計算および MDX クエリと ASSL をサポートします。  
  
-   データ マイニング モデルは DMX と ASSL をサポートします。  
  
-   Analysis Services PowerShell は、テーブル モデルとデータベースおよび多次元モデルとデータベースでサポートされます。  
  
 すべてのデータベースは XML/A をサポートします。 詳細については、「[クエリと式言語のリファレンス (Analysis Services)](../Topic/Query%20and%20Expression%20Language%20Reference%20\(Analysis%20Services\).md)」と「[開発者ガイド (Analysis Services)](../analysis-services/analysis-services-developer-documentation.md)」を参照してください。  
  
##  <a name="a-namebkmkseca-security-features"></a><a name="bkmk_sec"></a> セキュリティ機能  
 Analysis Services のすべてのソリューションは、データベース レベルでセキュリティを確保できます。 それよりも詳細なセキュリティ オプションは、モードによって異なります。 きめ細かなセキュリティ設定がソリューションに求められる場合は、構築しようとしているソリューションの種類でサポートされるセキュリティのレベルを次の一覧で確認してください。  
  
-   [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのセキュリティは、SharePoint の権限を使用して、ファイル レベルで確保されます。  
  
-   テーブル モデル データベースには、Analysis Services のロール ベースの権限による行レベルのセキュリティが使用されます。  
  
-   多次元モデル データベースには、Analysis Services のロール ベースの権限によるディメンションおよびセル レベルのセキュリティが使用されます。  
  
 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックは、テーブル モードのサーバーに復元できます。 復元されたファイルは SharePoint から切り離され、これにより、行レベルのセキュリティを含め、すべてのテーブル モデリング機能を使用できます。  
  
##  <a name="a-namebkmkdesignera-design-tools"></a><a name="bkmk_designer"></a> デザイン ツール  
 分析モデルの構築に携わるユーザーごとにデータ モデリングのスキルと技術的な専門知識は大きく異なることが考えられます。 ツールへの慣れやユーザーの専門知識がソリューションの検討対象に含まれる場合は、モデルの作成に関して次の経験を比較します。  
  
|モデリング ツール|用途|  
|-------------------|--------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|テーブル、多次元、およびデータ マイニングの各ソリューションを作成する目的で使用します。 この作成環境は、Visual Studio シェルを使用して、ワークスペース、プロパティ ペイン、およびオブジェクトのナビゲーションを提供します。 Visual Studio を既に利用している技術系ユーザーのほとんどは、ビジネス インテリジェンス アプリケーションの構築手段としてこのツールを選びます。|  
|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel|後で [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint がインストールされている SharePoint ファームに配置する [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックを作成する目的で使用します。 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel には、Excel を通じて開く専用のアプリケーション ワークスペースがあります。 Excel と同じビジュアル要素 (タブ ページ、グリッド レイアウト、および数式バー) が使用されます。 Excel に習熟しているユーザーは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] よりもこのツールを好みます。|  
  
##  <a name="a-namebkmkclienta-client-application-support"></a><a name="bkmk_client"></a> クライアント アプリケーションのサポート  
 Reporting Services を使用している場合、使用できるレポート機能は、エディションおよびサーバー モードによって異なります。 このため、構築しようとするレポートの種類が、インストールするサーバー モードの選択を左右する場合があります。  
  
 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] は、SharePoint で動作する Reporting Services 作成ツールです。SharePoint 2010 ファームに配置されたレポート サーバーで利用できます。 このレポートで使用できるデータ ソースの種類は、Analysis Services テーブル モデル データベースまたは [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのみです。 つまり、この種類のレポートによって使用されるデータ ソースをホストするためのテーブル モード サーバーまたは [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint サーバーが必要となります。 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートのデータ ソースとして多次元モデルを使用することはできません。 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートのデータ ソースとして使用する、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] BI セマンティック モデル接続または Reporting Services 共有データ ソースを作成する必要があります。  
  
 レポート ビルダーおよびレポート デザイナーは、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint でホストされている [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックも含め、Analysis Services のすべてのデータベースを使用できます。  
  
 Excel ピボットテーブル レポートは、すべての Analysis Services データベースでサポートされます。 テーブル データベース、多次元データベース、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのいずれでも、Excel の機能は変わりません。ただし、書き戻しがサポートされるのは多次元データベースのみです。  
  
 PerformancePoint ダッシュボードは、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックも含め、すべての Analysis Services データベースに接続できます。 詳細については、「 [データ接続の作成 (PerformancePoint Services)](http://go.microsoft.com/fwlink/?linkdID=218155)」を参照してください。  
  
##  <a name="a-namebkmkdeploymentmodea-server-deployment-modes-for-multidimensional-and-tabular-solutions"></a><a name="bkmk_deploymentmode"></a> 多次元ソリューションとテーブル ソリューションのサーバー配置モード  
 Analysis Services インスタンスは、サーバーの操作コンテキストを設定する 3 つのモードのいずれかでインストールされます。 サーバーに配置できるソリューションの種類は、インストールするサーバー モードによって決まります。 モード間の主な違いはストレージとメモリのアーキテクチャですが、それ以外にも違いは存在します。 3 つのサーバー モードについて次の表で簡単に説明します。 詳細については、「[Analysis Services インスタンスのサーバー モードの決定](../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)」を参照してください。  
  
|配置モード|説明|  
|---------------------|-----------------|  
|0 - 多次元およびデータ マイニング|Analysis Services の既定のインスタンスに配置する多次元およびデータ マイニング ソリューションを実行します。 配置モード 0 は、Analysis Services のインストールの既定値です。|  
|1 - [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] データ アクセス用の配置モードです。Analysis Services は、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint インストールの内部コンポーネントです。 Analysis Services は配置モード 1 でインストールされ、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] サービスによって SharePoint 環境で排他的に使用されます。|  
|2 - テーブル|配置モード 2 用に構成されている Analysis Services のスタンドアロン インスタンスでテーブル ソリューションを実行します。|  
  
 詳細については、「[Analysis Services のインストール](../analysis-services/instances/install-windows/install-analysis-services.md)」を参照してください。  
  
##  <a name="a-namebkmksharepointa-sharepoint-requirements"></a><a name="bkmk_sharePoint"></a> SharePoint の要件  
 SQL Server は、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] データ アクセスおよびテーブル データ アクセスのサポートを追加することによって SharePoint と統合されます。 SharePoint と SQL Server の統合に対する投資は、各製品から使用される機能の数を最大にすると増大します。 SharePoint がある場合は、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] データ アクセスを有効にし、ネットワーク サーバー上の外部 Analysis Services インスタンスで実行されるテーブル データベースにアクセスするための [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] .bism 接続ファイルを取得するために、SQL Server [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint をインストールすることができます。  
  
 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] とテーブル データベースをデータ ソースとして使用する Power View レポートは、SQL Server によって提供される SharePoint 機能と Excel の組み込み機能の両方です。 テーブル データベースは SharePoint の外部の Analysis Services インスタンスで実行されますが、そのデータは、SharePoint で実行される Power View レポートによって使用されます。  
  
 SharePoint を使用しない場合、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel を使用して [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックを作成できますが、まとまりのあるデータ ビジュアル化環境は得られません。 スライサー、フィルター、およびピボットを使用したデータの操作と検索を行うには、ブックを使用する各ユーザーが、Excel で [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel アドインを使用して各ブックをダウンロードして表示する必要があります。 そうしないと、ブックの視覚化機能は、ブックを開いたときに表示される静的データに制限されます。  
  
 テーブル、多次元、およびデータ マイニング ソリューションは、SharePoint に依存せず、ネットワーク上の Analysis Services インスタンスで実行されます。  
  
##  <a name="a-namebkmkexta-programmability-and-extensibility-support"></a><a name="bkmk_ext"></a> プログラミングと拡張性のサポート  
 Power BI については開発者サポートがありますが、[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックに対する開発者サポートはありません。 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックを使用する場合は、組み込みのクライアント アプリケーションとサーバー アプリケーションをソリューションの一部として使用する必要があります。 Excel のプログラミングと SharePoint のプログラミングしか選択できません。  
  
 Power BI については、「[Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/)」を参照してください。  
  
 テーブル ソリューションでは、1 つのソリューションで使用できる model.bim ファイルは 1 つだけです。したがって、すべての作業を 1 つのファイルで行う必要があります。 1 つのソリューションで複数のプロジェクトを使って作業することに慣れている開発チームは、共有テーブル ソリューションを作成する際には作業方法を変更する必要があります。  
  
 互換性レベル 1200 のテーブル ソリューションは、テーブル メタデータを使用する新しいオブジェクト モデルにマップされています。 以前のテーブル モデルとすべての多次元モデルでは、多次元メタデータが記述子として使用されます。 カスタム コードおよびスクリプトの AMO でテーブル名前空間を使用できるように、以前のテーブル モデルは互換性レベル 1200 にアップグレードすることをお勧めします。  
  
 詳細については、「[開発者ガイド (Analysis Services)](https://msdn.microsoft.com/library/bb500153.aspx)」を参照してください。  
  
##  <a name="a-namebkmknexta-next-step-build-a-solution"></a><a name="bkmk_Next"></a> 次の手順: ソリューションを構築する  
 各ソリューションの基本的な違いがわかったら、以下のチュートリアルで、各ソリューションの作成手順を学ぶことができます。 以下のリンクをクリックすると、手順を説明するチュートリアルが表示されます。  
  
-   [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] モデルを作成します。 「[Power Pivot in Microsoft Excel の使用を開始します](https://support.office.com/article/Get-started-with-Power-Pivot-in-Microsoft-Excel-fdfcf944-7876-424a-8437-1a6c1043a80b)」を参照してください。  
  
-   テーブル モデルを作成します。 「[テーブル モデリング &#40;Adventure Works チュートリアル&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md)」を参照してください。  
  
-   多次元モデルを作成します。 「[多次元モデリング &#40;Adventure Works チュートリアル&#41;](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)」を参照してください。  
  
-   データ マイニング モデルを作成します。 「[基本的なデータ マイニング チュートリアル](../Topic/Basic%20Data%20Mining%20Tutorial.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンス管理](../analysis-services/instances/analysis-services-instance-management.md)   
 [Analysis Services の新機能](../analysis-services/what-s-new-in-analysis-services.md)     
 [PowerPivot の新機能](http://go.microsoft.com/fwlink/?LinkId=238141)   
 [Power Pivot BI セマンティック モデル接続 &#40;.bism&#41;](../analysis-services/power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)   
 [共有データ ソースを作成および管理する &#40;Reporting Services の SharePoint 統合モード&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)  
  
  