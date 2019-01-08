---
title: Analysis Services 表形式および多次元モデルの比較 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d36c20e0278a90bc5afcbd312afea2cb596e9c51
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072545"
---
# <a name="comparing-tabular-and-multidimensional-solutions"></a>テーブルと多次元ソリューションのソリューションの比較
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  SQL Server Analysis Services には、business intelligence semantic model を作成するためのいくつかのアプローチが用意されています。表形式、多次元、および Power Pivot for SharePoint。
  
 複数のアプローチにより、さまざまなビジネスとユーザーの要件に応じたモデリング エクスペリエンスを実現できます。 多次元モデルは、オープン スタンダードに組み込まれている成熟したテクノロジで、多くの BI ソフトウェア ベンダーで採用されていますが、習得が難しい場合があります。 テーブル モデルは、多くの開発者にとって直感的なリレーショナル モデリング アプローチを提供します。 Power Pivot モデルはさらにシンプルで、Excel 形式でビジュアル データ モデリングを提供するほか、SharePoint 経由でサーバーのサポートが可能になっています。  
  
 すべてのモデルが Analysis Services インスタンスで実行されているデータベースとして配置され、1 つのデータ プロバイダー セットを使用してクライアント ツールでアクセスします。また、Excel、Reporting Services、Power BI、および他のベンダーの BI ツールによって、対話型レポートや静的レポートで視覚化されます。  
  
 テーブルと多次元ソリューションの SSDT を使用して組み込まれ、企業の BI プロジェクトをスタンドアロンで実行されるものでは[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、オンプレミスのインスタンスと表形式モデルで、 [Azure Analysis Services](https://azure.microsoft.com/services/analysis-services/)内のサーバー、クラウド。 両方のソリューションで、BI クライアントと簡単に統合できる高パフォーマンス分析データベースが作成されます。 ただし、各ソリューションの作成、使用、配置の方法は異なります。 このトピックでは、ユーザーが適切なアプローチを特定できるように、この 2 つの種類を比較します。  
  
 新しいプロジェクトでは、一般的な推奨事項の表形式モデル。 表形式モデルが設計、テスト、および配置には高速化最新のセルフ サービス BI アプリケーションとの共同作業し、クラウド サービスを Microsoft から。  
  
##  <a name="bkmk_overview"></a> モデリングの種類の概要  
 Analysis Services を初めて使用する場合は、 次の表で、各モデルのアプローチの概要と、最初のリリース媒体を確認してください。  
 
 > [!NOTE]  
>  **Azure Analysis Services** 1200 以降の互換性レベル表形式モデルをサポートしています。 ただし、このトピックで説明されているすべてのテーブル モデリング機能は Azure Analysis Services でサポートされています。 Azure Analysis Services を表形式モデルの配置の作成と、オンプレミスの場合とほぼ同じです、これが違いを理解する重要です。 詳細についてを参照してください[Azure Analysis Services とは何ですか?。](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview)
  
||||  
|-|-|-|  
|**型**|**モデリングの説明**|**リリース**|  
|テーブル|リレーショナル モデリング構造 (モデル、テーブル、列)。 内部的には、OLAP モデリング構造 (キューブ、ディメンション、メジャー) からメタデータが継承されます。 コードとスクリプトは OLAP メタデータを使用します。|SQL Server 2012 以降 (互換性レベル 1050 ～ 1103) <sup>1</sup>|  
|SQL Server 2016 のテーブル|リレーショナル モデリング構造 (モデル、テーブル、列) が互いに表形式メタデータ オブジェクト定義に[Tabular Model Scripting Language (TMSL)](../analysis-services/tabular-model-scripting-language-tmsl-reference.md)と[表形式オブジェクト モデル (TOM)](../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)コード。|SQL Server 2016 (互換性レベル 1200)| 
|SQL Server 2017 における表形式|リレーショナル モデリング構造 (モデル、テーブル、列) が互いに表形式メタデータ オブジェクト定義に[Tabular Model Scripting Language (TMSL)](../analysis-services/tabular-model-scripting-language-tmsl-reference.md)と[表形式オブジェクト モデル (TOM)](../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md)コード。|SQL Server 2017 (互換性レベル 1400)| 
|多次元|OLAP モデリング構造 (キューブ、ディメンション、メジャー)。|SQL Server 2000 以降|  
|Power Pivot|もともとはアドインですが、Excel に完全に統合されました。 内部テーブル インフラストラクチャにおけるビジュアル モデリングのみ。 Power Pivot モデルを SSDT にインポートして、Analysis Services インスタンスで実行される新しいテーブル モデルを作成できます。|Excel と Power Pivot BI Desktop を使用|  
  
 <sup>1</sup>互換性レベルが表形式メタデータ エンジンとシナリオを有効にするためのサポートは、現在のリリースで重要です。 上位のレベルでのみ使用できる機能。 以降のバージョンが以前の互換性レベルをサポートしますが、新しいモデルを作成または既存のモデルをサーバーのバージョンでサポートされている最も高い互換性レベルにアップグレードすることをお勧めします。
  
##  <a name="bkmk_models"></a> モデルの機能  
  次の表は、機能の利用の可否をモデルごとにまとめたものです。 この一覧で、必要な機能が、構築しようとしているモデルの種類で利用できるかどうかを確認してください。  
  
|||| 
|-|-|-|
||多次元|テーブル|
|アクション|はい|いいえ|
|集計|はい|いいえ|
|計算列|いいえ|はい|  
|計算されるメジャー|はい|はい| 
|計算テーブル|いいえ|可<sup>1</sup>|  
|カスタム アセンブリ|はい|いいえ|
|カスタム ロールアップ|はい|いいえ| 
|既定のメンバー|はい|いいえ|  
|表示フォルダー|はい|可<sup>1</sup>|  
|Distinct Count|はい|○ (DAX 経由)|
|ドリルスルー|はい|[はい]\(クライアント アプリケーションによって異なります)|
|階層|はい|はい|
|KPI|はい|はい| 
|リンク オブジェクト|はい|○ (リンク テーブル)|
|M 式|いいえ|可<sup>1</sup>|
|多対多リレーションシップ|はい|いいえ (がある[双方向クロス フィルター](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) 1200 以降の互換性レベル)| 
|名前付きセット|はい|いいえ| 
|不規則階層|はい|可<sup>1</sup>|  
|親子階層|はい|○ (DAX 経由)|
|[メジャー グループ]|はい|はい| 
|パースペクティブ|はい|はい|
|行レベルのセキュリティ|はい|はい| 
|オブジェクト レベルのセキュリティ|はい|可<sup>1</sup>|
|準加法メジャー|はい|はい| 
|翻訳|[可](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)|はい| 
|ユーザー定義階層|はい|はい|
|[書き戻し]|はい|いいえ| 
  
 <sup>1</sup>を参照してください[Compatibility Level for Tabular が Analysis Services でモデル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)互換性レベルの機能の違いについてはします。  
  
##  <a name="bkmk_ds"></a> データに関する考慮事項  
 表形式および多次元モデルでは、外部ソースからインポートされたデータを使用します。 どの種類のモデルがデータに最適であるかを判断する際に主に考慮しなければならないのが、インポートする必要があるデータの量と種類です。  
  
 **圧縮**  
  
 テーブル ソリューションと多次元ソリューションではデータ圧縮が使用されるため、Analysis Services データベースのサイズがデータのインポート元のデータ ウェアハウスに比べて小さくなります。 実際の圧縮は、基になるデータの特性によって異なるので、データが処理されてクエリで使用された後にどの程度のディスクおよびメモリがソリューションに必要なのかを正確に知る方法はありません。  
  
 多くの Analysis Services 開発者が使用する目安は、多次元データベースの 1 次記憶域が元のデータの約 3 分の 1 のサイズになるというものです。 テーブル データベースでは、特にデータの大部分がファクト テーブルからインポートされる場合、データをさらに小さく圧縮できることもあります (約 10 分の 1 のサイズ)。  
  
 **モデルとリソースの差のサイズ (メモリ内またはディスク)**  
  
 Analysis Services データベースのサイズは、そのデータベースの実行に使用可能なリソースによってのみ制限されます。 また、モデルの種類とストレージ モードも、データベースがどの程度大きくなるかに影響します。  
  
 テーブル データベースは、In-Memory モード、またはクエリ実行を外部データベースにオフロードする DirectQuery モードで実行されます。 テーブルのメモリ内分析データベースはすべて、データもクエリをサポートするために作成された追加のデータ構造をロードするだけでなく、十分なメモリをいる必要がありますメモリに完全に格納されます。  
  
 SQL Server 2016 で強化された DirectQuery では、少ないの前より制限とパフォーマンスが向上があります。 ストレージとクエリの実行にバックエンドのリレーショナル データベースを利用することで、大規模なテーブル モデル構築が以前よりも現実的なものになっています。  
  
 従来は、実稼働環境で最大のデータベースは、しますそれぞれに使用するために最適化されたそれぞれ専用のハードウェア上で個別に実行する処理とクエリのワークロードで多次元。  これを急速に追っているのがテーブル データベースで、DirectQuery の新しい強化機能により、その差はますます縮まっています。  
  
 多次元のオフロード データ ストレージとクエリの実行を利用し ROLAP します。   クエリ サーバーで行セットをキャッシュし、古いものはページ アウトできます。メモリとディスク リソースをバランスよく効率的に使用できることに惹かれ、多次元ソリューションを利用している顧客も少なくありません。  
  
 負荷が高い場合、どちらのソリューションでも、Analysis Services によるデータのキャッシュ、格納、スキャン、クエリに応じて必要なディスクとメモリが増加すると予想されます。 メモリ ページング オプションの詳細については、「 [メモリのプロパティ](../analysis-services/server-properties/memory-properties.md)」を参照してください。 スケールの詳細については、「 [Analysis Services の高可用性とスケーラビリティ](../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)」を参照してください。  
  
 Power Pivot for Excel では、ファイル サイズが 2 GB に制限されています。これは、Power Pivot for Excel で作成したブックを SharePoint にアップロードできるようにするためです (SharePoint ではファイルの最大アップロード サイズが設定されます)。 このファイル サイズの制限を回避することが、Power Pivot ブックをスタンドアロンの Analysis Services インスタンスのテーブル ソリューションに移行する主な理由の 1 つになります。 ファイルの最大アップロード サイズの構成の詳細については、「[アップロードするファイルの最大サイズの構成 (Power Pivot for SharePoint)](../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)」を参照してください。  
  
 **サポートされるデータ ソース**  
  
 テーブル モデルは、リレーショナル データ ソース、データ フィード、およびいくつかのドキュメント形式からデータをインポートできます。 表形式モデルを使用した ODBC プロバイダーの OLE DB を使用することもできます。 互換性レベル 1400 の表形式モデルでは、さまざまなデータのソースからインポートできますが、大幅に増加を提供します。 これは、しますデータ クエリし、インポート機能は、M 数式クエリ言語を使用して SSDT で新しい Get Data の導入により。   

  多次元ソリューションでは、ネイティブおよびマネージド OLE DB プロバイダーを使用してリレーショナル データ ソースからデータをインポートできます。  
  
 各モデルにインポートできる外部データ ソースの一覧については、以下のトピックを参照してください。  
  
-   [サポートされているデータ ソース](../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  

-   [サポートされるデータ ソース &#40;SSASSSAS - 多次元&#41;](../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  

  
##  <a name="bkmk_lang"></a> クエリおよびスクリプト言語のサポート  
 Analysis Services には MDX、DMX、DAX、XML/A、ASSL、および TMSL が用意されています。 これらの言語のサポート状況は、モデルの種類によって異なる場合があります。 クエリとスクリプト言語の要件が重要な検討事項である場合は、次の一覧を参考にしてください。  

-   テーブル モデル データベースは、DAX の計算、DAX クエリ、および MDX クエリをサポートします。 これは、すべての互換性レベルに当てはまります。 スクリプト言語は ASSL (XMLA 経由) 互換性レベル 1050 ~ 1103 の場合、および TMSL (XMLA) 経由の互換性レベル 1200 以上です。 

-   Power Pivot ブックは、計算には DAX を使用し、クエリには DAX または MDX を使用します。  
  
-   多次元モデル データベースでは、MDX 計算、MDX クエリ、DAX クエリ、および ASSL をサポートします。 
  
-   データ マイニング モデルは DMX と ASSL をサポートします。  
  
-   Analysis Services PowerShell は、テーブル モデルとデータベースおよび多次元モデルとデータベースでサポートされます。  
  
 すべてのデータベースは XML/A をサポートします。 詳細については、「[クエリと式言語のリファレンス (Analysis Services)](http://msdn.microsoft.com/library/9597533d-35f4-4742-9d8c-7af392163527)」と「[開発者ガイド (Analysis Services)](../analysis-services/analysis-services-developer-documentation.md)」を参照してください。  
  
##  <a name="bkmk_sec"></a> セキュリティ機能  
 Analysis Services のすべてのソリューションは、データベース レベルでセキュリティを確保できます。 それよりも詳細なセキュリティ オプションは、モードによって異なります。 きめ細かなセキュリティ設定がソリューションに求められる場合は、構築しようとしているソリューションの種類でサポートされるセキュリティのレベルを次の一覧で確認してください。  

  
-   表形式モデル データベースには、ロール ベースのアクセス許可を使用して、行レベル セキュリティを使用できます。  
  
-   ディメンションおよびセル レベルのセキュリティ、ロールベースのアクセス許可を使用して、多次元モデル データベースを使用できます。  

-   [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのセキュリティは、SharePoint の権限を使用して、ファイル レベルで確保されます。  
  
 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックは、テーブル モードのサーバーに復元できます。 復元されたファイルは、行レベル セキュリティを含め、すべてのテーブル モデリング機能を使用することができます、SharePoint から切り離されます。  
  
##  <a name="bkmk_designer"></a> デザイン ツール  
 分析モデルの構築に携わるユーザーごとにデータ モデリングのスキルと技術的な専門知識は大きく異なることが考えられます。 ツールへの慣れやユーザーの専門知識がソリューションの検討対象に含まれる場合は、モデルの作成に関して次の経験を比較します。  
  
|モデリング ツール|用途|  
|-------------------|--------------|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|データ マイニング ソリューションおよびテーブル、多次元、作成に使用します。 この作成環境は、Visual Studio シェルを使用して、ワークスペース、プロパティ ペイン、およびオブジェクトのナビゲーションを提供します。 Visual Studio を既に利用している技術系ユーザーのほとんどは、ビジネス インテリジェンス アプリケーションの構築手段としてこのツールを選びます。|  
|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel|後で [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint がインストールされている SharePoint ファームに配置する [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックを作成する目的で使用します。 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for Excel には、Excel を通じて開く専用のアプリケーション ワークスペースがあります。 Excel と同じビジュアル要素 (タブ ページ、グリッド レイアウト、および数式バー) が使用されます。 Excel に習熟しているユーザーは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]よりもこのツールを好みます。|  
  
##  <a name="bkmk_client"></a> クライアント アプリケーションのサポート  
 [全般] で、テーブルと多次元ソリューションでは、Analysis Services クライアント ライブラリ (MSOLAP、AMOMD、ADOMD) の 1 つ以上を使用するクライアント アプリケーションをサポートします。 たとえば、Excel、Power BI Desktop、およびカスタム アプリケーションにします。   
 
 Reporting Services を使用している場合、使用できるレポート機能は、エディションおよびサーバー モードによって異なります。 このため、構築しようとするレポートの種類が、インストールするサーバー モードの選択を左右する場合があります。  
  
 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]は、SharePoint で動作する Reporting Services 作成ツールです。SharePoint 2010 ファームに配置されたレポート サーバーで利用できます。 このレポートで使用できるデータ ソースの種類は、Analysis Services テーブル モデル データベースまたは [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのみです。 つまり、この種類のレポートによって使用されるデータ ソースをホストするためのテーブル モード サーバーまたは [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint サーバーが必要となります。 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートのデータ ソースとして多次元モデルを使用することはできません。 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] レポートのデータ ソースとして使用する、 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] BI セマンティック モデル接続または Reporting Services 共有データ ソースを作成する必要があります。  
  
 レポート ビルダーおよびレポート デザイナーは、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] for SharePoint でホストされている [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックも含め、Analysis Services のすべてのデータベースを使用できます。  
  
 Excel ピボットテーブル レポートは、すべての Analysis Services データベースでサポートされます。 テーブル データベース、多次元データベース、 [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ブックのいずれでも、Excel の機能は変わりません。ただし、書き戻しがサポートされるのは多次元データベースのみです。  
 
  
  
## <a name="see-also"></a>参照  
 [Analysis Services インスタンス管理](../analysis-services/instances/analysis-services-instance-management.md)   
 [Analysis Services の新機能](../analysis-services/what-s-new-in-analysis-services.md)     

  
  
