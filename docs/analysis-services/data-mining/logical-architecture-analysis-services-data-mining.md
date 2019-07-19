---
title: 論理アーキテクチャ (Analysis Services - データ マイニング) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2fe6eb33c95c54f7762c8c5c0feb08db87c01df3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209933"
---
# <a name="logical-architecture-analysis-services---data-mining"></a>論理アーキテクチャ (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニングは、複数のコンポーネントの相互作用を伴うプロセスです。  
  
-   SQL Server データベース内のデータのソースまたはその他のデータ ソースにアクセスし、トレーニング、テスト、または予測に使用します。  
  
-   データ マイニング構造とデータ マイニング モデルは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または Visual Studio を使用して定義します。  
  
-   データ マイニング オブジェクトの管理および予測やクエリの作成には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用します。  
  
-   ソリューションが完成したら、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスにそのソリューションを配置します。  
  
 これらのソリューション オブジェクトを作成するプロセスについては、既に他の場所で説明しています。 詳細については、「 [データ マイニング ソリューション](../../analysis-services/data-mining/data-mining-solutions.md)」を参照してください。  
  
 次のセクションでは、データ マイニング ソリューション内のオブジェクトの論理アーキテクチャについて説明します。  
  
 [データ マイニング ソース データ](#bkmk_SourceData)  
  
 [マイニング構造](#bkmk_Structures)  
  
 [[マイニング モデル]](#bkmk_Models)  
  
 [カスタム データ マイニング オブジェクト](#bkmk_CustomObjects)  
  
##  <a name="bkmk_SourceData"></a> データ マイニング ソース データ  
 データ マイニングで使用するデータは、データ マイニング ソリューションに格納されません。バインドのみが格納されます。 データは前のバージョンの SQL Server、CRM システム、またはフラット ファイルで作成されたデータベースにも存在する場合があります。 処理によって構造またはモデルをトレーニングすると、データの統計サマリーが作成され、キャッシュに格納されます。そのサマリーは、後の操作で使用するために保持することも、処理後に削除することもできます。 詳細については、「[マイニング構造 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソース ビュー (DSV) オブジェクト内のさまざまなデータを組み合わせることで、データ ソースの上に抽象化レイヤーが提供されます。 テーブル間の結合を指定できます。また、多対一のリレーションシップを持つテーブルを追加して、入れ子になったテーブル列を作成することができます。 これらのオブジェクト (データ ソースおよびデータ ソース ビュー) の定義は、*.ds および \*.dsv というファイル名拡張子でソリューション内に保存されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースおよびデータ ソース ビューの作成と使用の詳細については、「[サポートされるデータ ソース (SSASSSAS - 多次元)](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)」を参照してください。  
  
 AMO または XMLA を使用して、データ ソースおよびデータ ソース ビューを定義および変更することもできます。 プログラムによってこれらのオブジェクトを操作する方法の詳細については、「[論理アーキテクチャの概要 (Analysis Services - 多次元データ)](../../analysis-services/multidimensional-models/olap-logical/logical-architecture-overview-analysis-services-multidimensional-data.md)」を参照してください。  
  
  
##  <a name="bkmk_Structures"></a> Mining Structures  
 データ マイニング構造は、マイニング モデルの作成元のデータ ドメインを定義する論理データ コンテナーです。 1 つのマイニング構造で複数のマイニング モデルをサポートできます。  
  
 データ マイニング ソリューションでデータを使用する必要がある場合、Analysis Services ではソースからデータを読み込み、集計およびその他の情報のキャッシュを生成します。 既定では、トレーニング データを再利用して追加のモデルをサポートできるように、このキャッシュは保持されます。 キャッシュを削除する必要がある場合は、マイニング構造オブジェクトの **CacheMode** プロパティを値 **ClearAfterProcessing**に変更します。 詳細については、「 [AMO データ マイニング クラス](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)」を参照してください。  
  
 Analysis Services には、代表的なランダムに選択したデータのセットでマイニング モデルをテストできるように、トレーニング セットとテスト データ セットには、データを分割する機能も提供します。 データは、実際には別々に格納されません。構造キャッシュ内のケース データには、その特定のケースがトレーニングに使用されるかテストに使用されるかを示すプロパティが設定されます。 キャッシュを削除すると、その情報を取得できなくなります。  
  
 詳細については、「[マイニング構造 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」を参照してください。  
  
 データ マイニング構造には、入れ子になったテーブルを含めることができます。 入れ子になったテーブルは、プライマリ データ テーブルでモデル化されているケースに関する追加の詳細情報を提供します。 詳細については、「[入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)」をご覧ください。  
  
  
##  <a name="bkmk_Models"></a> Mining Models  
 処理前のデータ マイニング モデルは、メタデータのプロパティの組み合わせにすぎません。 これらのプロパティでは、マイニング構造とデータ マイニング アルゴリズムを指定し、データの処理方法に影響するパラメーターとフィルター設定のコレクションを定義します。 詳細については、「[入れ子になったテーブル (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-models-analysis-services-data-mining.md)」を参照してください。  
  
 モデルを処理すると、マイニング構造のキャッシュに格納されたトレーニング データを使用して、データの統計プロパティと、アルゴリズムおよびそのパラメーターによって定義されたヒューリスティックの両方に基づいたパターンが生成されます。 これは、モデルの *トレーニング* と呼ばれます。  
  
 トレーニングの結果は、見つかったパターンを表し、予測を生成するルールを提供する一連の概要データで、*モデル コンテンツ*に格納されます。 詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
 限られた状況では、標準形式である Predictive Model Markup Language (PMML) に従ってモデルの数式とデータ バインドを表すファイルにモデルの論理構造をエクスポートすることもできます。 PMML を使用する他のシステムにこの論理構造をインポートし、そのモデルを予測に使用することができます。 詳細については、「 [DMX 選択ステートメントについて](../../dmx/understanding-the-dmx-select-statement.md)」を参照してください。  
  
  
##  <a name="bkmk_CustomObjects"></a> カスタム データ マイニング オブジェクト  
 精度チャート、予測クエリなど、データ マイニング プロジェクトのコンテキストで使用するその他のオブジェクトは、ソリューション内に保存されませんが、ASSL を使用してスクリプト化することや、AMO を使用して作成することができます。  
  
 また、これらのカスタム オブジェクトを追加することで、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスで利用可能なサービスと機能を拡張することもできます。  
  
 **カスタム アセンブリ**  
 .NET アセンブリは、CLR または COM に準拠した任意の言語を使用して定義した後、SQL Server のインスタンスに登録できます。 アセンブリ ファイルは、アプリケーションで定義された場所から読み込まれ、コピーは、データと共にサーバーに保存されます。 アセンブリ ファイルのコピーは、サービスが開始されるたびにアセンブリを読み込むために使用されます。  
  
 詳細については、「 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)」を参照してください。  
  
 **カスタム ストアド プロシージャ**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータ マイニングでは、ストアド プロシージャを使用して、データ マイニング オブジェクトを操作できます。 独自のストアド プロシージャを作成して、機能を拡張し、予測クエリおよびコンテンツ クエリから返されるデータをより簡単に操作できます。  
  
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
 次のストアド プロシージャを使用して、クロス検証を実行できます。  
  
 [データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)  
  
 また、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、内部でデータ マイニングに使用されるシステム ストアド プロシージャが多数用意されています。 システム ストアド プロシージャは内部で使用するためのものですが、それらを応用することもできます。 これらのストアド プロシージャは、マイクロソフトによって随時変更される場合があります。そのため、実際の運用では、DMX、AMO、または XMLA を使用してクエリを作成することをお勧めします。  
  
 **カスタム プラグイン アルゴリズム**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、独自のアルゴリズムを作成し、そのアルゴリズムを新しいデータ マイニング サービスとしてサーバー インスタンスに追加するためのメカニズムが用意されています。  
  
 Analysis Services では、COM インターフェイスを使用して、プラグイン アルゴリズムと通信します。 新しいアルゴリズムの実装方法の詳細については、「 [プラグイン アルゴリズム](../../analysis-services/data-mining/plugin-algorithms.md)」を参照してください。  
  
 新しいアルゴリズムはそれぞれ使用する前に登録する必要があります。 アルゴリズムを登録するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスの .ini ファイルにアルゴリズムに必要なメタデータを追加します。 新しいアルゴリズムを使用する各インスタンスに情報を追加する必要があります。 アルゴリズムを追加したら、インスタンスを再起動し、MINING_SERVICES スキーマ行セットを使用して、新しいアルゴリズムを表示し、そのアルゴリズムでサポートされているオプション、プロバイダーなどを確認できます。  
  
  
## <a name="see-also"></a>関連項目  
 [多次元モデルの処理 (Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  
