---
title: "マイニング構造 (DMX) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_MINING_STRUCTURE
- CREATE MINING STRUCTURE
dev_langs:
- DMX
helpviewer_keywords:
- CREATE MINING STRUCTURE statement
- mining structures [DMX], creating
- RELATED TO column
ms.assetid: c0dec39c-e90f-4afd-aeaf-a9c3e1d1a5e0
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cb0b52cf7ac2b866119ff75bbd0d7e8da8cbac84
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-mining-structure-dmx"></a>CREATE MINING STRUCTURE (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースに新しいマイニング構造を作成し、必要に応じてトレーニング パーティションとテスト パーティションを定義します。 使用することができます、マイニング構造を作成した後、 [ALTER MINING STRUCTURE & #40";"DMX"&"#41;](../dmx/alter-mining-structure-dmx.md)ステートメントに、マイニング構造にモデルを追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE [SESSION] MINING STRUCTURE <structure>  
(  
    [(<column definition list>)]  
)  
[WITH HOLDOUT (<holdout-specifier> [OR <holdout-specifier>])]  
[REPEATABLE(<holdout seed>)]  
<holdout-specifier>::=  <holdout-maxpercent> PERCENT | <holdout-maxcases> CASES  
```  
  
## <a name="arguments"></a>引数  
 *構造体*  
 構造の一意の名前です。  
  
 *列定義リスト*  
 列定義のコンマ区切りのリストです。  
  
 *提示された maxpercent*  
 テスト用に確保するデータの割合を示す 1 ～ 100 の整数です。  
  
 *提示された maxcases*  
 テストに使用するケースの最大数を示す整数です。  
  
 ケースの最大数に指定された値が入力ケース数を超える場合、すべての入力ケースがテストに使用され、警告が発生します。  
  
> [!NOTE]  
>  ケースの最大数と割合の両方を指定すると、2 つの制限のいずれか小さい方が使用されます。  
  
 *提示されたシード*  
 データのパーティション分割を開始するシードとして使用される整数です。  
  
 0 に設定すると、マイニング構造 ID のハッシュがシードとして使用されます。  
  
> [!NOTE]  
>  パーティションを再現できるようにする必要がある場合は、シードを指定する必要があります。  
  
 既定値 : REPEATABLE(0)  
  
## <a name="remarks"></a>解説  
 マイニング構造を定義するには、列リストを指定し、必要に応じて列間の階層リレーションシップを指定して、さらに必要に応じてマイニング構造をトレーニング データセットとテスト データセットにパーティション分割します。  
  
 オプションの SESSION キーワードは、その構造が、現在のセッションの間しか使用できない一時的な構造であることを示します。 セッションが終了すると、構造およびその構造に基づくモデルはすべて削除されます。 一時的なマイニング構造およびモデルを作成するには、まず AllowSessionMiningModels、データベースのプロパティを設定する必要があります。 詳細については、「 [データ マイニング プロパティ](../analysis-services/server-properties/data-mining-properties.md)」を参照してください。  
  
## <a name="column-definition-list"></a>列定義リスト  
 列定義リストに各列の次の情報を含めることによって、マイニング構造を定義します。  
  
-   名前 (必須)  
  
-   データ型 (必須)  
  
-   Distribution  
  
-   モデリング フラグの一覧  
  
-   コンテンツの種類 (必須)  
  
-   RELATED TO 句によって示される、属性列とのリレーションシップです (適用される場合にのみ必須)。  
  
 列定義リストの次の構文を使用して、単一列を定義します。  
  
```  
<column name>    <data type>    [<Distribution>]    [<Modeling Flags>]    <Content Type>    [<column relationship>]  
```  
  
 列定義リストの次の構文を使用して、入れ子になったテーブル列を定義します。  
  
```  
<column name>    TABLE    ( <column definition list> )  
```  
  
 データ型、コンテンツの種類、列の分布、および構造列の定義に使用できるモデリング フラグの一覧は、次のトピックを参照してください。  
  
-   [データ型 (&) #40";"データ マイニング"&"#41;](../analysis-services/data-mining/data-types-data-mining.md)  
  
-   [コンテンツの種類 (&) #40 です。 データ マイニング (&) #41;](../analysis-services/data-mining/content-types-data-mining.md)  
  
-   [列の分布 (&) #40";"データ マイニング"&"#41;](../analysis-services/data-mining/column-distributions-data-mining.md)  
  
-   [モデリング フラグ (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
 列には複数のモデリング フラグ値を定義できます。 ただし、1 つの列に定義できるコンテンツの種類とデータ型はそれぞれ 1 つだけです。  
  
### <a name="column-relationships"></a>列のリレーションシップ  
 列定義ステートメントに句を追加して、2 つの列間のリレーションシップを記述できます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]次の使用をサポートしている\<列リレーションシップ > 句。  
  
 **を関連します。**  
 値の階層を示します。 RELATED TO 列の対象にすることが可能なのは、入れ子になったテーブル内のキー列、ケース行内の不連続値の列、RELATED TO 句のある別の列です。これにより、より深い階層が示されます。  
  
## <a name="holdout-parameters"></a>提示されたパラメーター  
 提示されたパラメーターを指定する場合は、構造データのパーティションを作成します。 提示されたパラメーターに指定したデータ量がテスト用に予約され、残りのデータはトレーニングに使用されます。 既定では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用してマイニング構造を作成する場合、30% のテスト データと 70% のトレーニング データを含む、提示されたパーティションが作成されます。 詳しくは、「 [Training and Testing Data Sets](../analysis-services/data-mining/training-and-testing-data-sets.md)」をご覧ください。  
  
 データ マイニング拡張機能 (DMX) を使用してマイニング構造を作成する場合、提示されたパーティションが作成されるように手動で指定する必要があります。  
  
> [!NOTE]  
>  **ALTER MINING STRUCTURE**ステートメントが提示されたパラメーターをサポートしていません。  
  
 提示されたパラメーターは 3 つまで指定できます。 提示されたケースの最大数と提示されたケースの割合の両方を指定すると、ケースの最大数に達するまでケースの割合が予約されます。 続けて、整数として提示データの割合を指定する、 **%**キーワード、続けて、整数としてのケースの最大数を指定し、**ケース**キーワード。 次の例に示すように、条件は任意の順序で組み合わせることができます。  
  
```  
WITH HOLDOUT (20 PERCENT)   
WITH HOLDOUT (2000 CASES)   
WITH HOLDOUT (20 PERCENT OR 2000 CASES)   
WITH HOLDOUT (2000 CASES OR 20 PERCENT)  
```  
  
 提示されたシードによって、トレーニング データセットまたはテスト データセットにケースをランダムに割り当てる処理の開始位置が制御されます。 提示されたシードを設定すると、パーティションを反復可能にすることができます。 提示されたシードを指定しない場合、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、マイニング構造の名前を使用してシードが作成されます。 構造の名前を変更すると、シード値が変更されます。 提示されたシード パラメーターは、他の提示されたパラメーターのいずれかまたは両方と共に使用できます。  
  
> [!NOTE]  
>  パーティションの情報がトレーニング データと共にキャッシュされているため、予約データを使用することを確認、 **CacheMode**マイニング構造のプロパティに設定されて**KeepTrainingData**です。 これは、既定の設定[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]における新しいマイニング構造です。 変更、 **CacheMode**プロパティを**ClearTrainingCases**パーティションが処理されたすべてのマイニング モデルを与えませんを含む、提示された既存のマイニング構造にします。 ただし場合、<xref:Microsoft.AnalysisServices.MiningStructureCacheMode>に設定されていない**KeepTrainingData**、提示されたパラメーターには影響はありません。 つまり、すべてのソース データがトレーニングに使用され、テスト セットは使用できません。 パーティションの定義は構造と共にキャッシュされます。トレーニング ケースのキャッシュを消去すると、テスト データのキャッシュおよび提示されたセットの定義も消去されます。  
  
## <a name="examples"></a>使用例  
 次の例では、DMX を使用して、提示されたパラメーターによってマイニング構造を作成する方法について説明します。  
  
### <a name="example-1-adding-a-structure-with-no-training-set"></a>例 1 : トレーニング セットを含まない構造を追加する  
 次の例と呼ばれる新しいマイニング構造を作成する`New Mailing`関連するマイニング モデルを作成するしたりせず、提示されたパラメーターを使用します。 構造にマイニング モデルを追加する方法については、次を参照してください。 [ALTER MINING STRUCTURE & #40";"DMX"&"#41;](../dmx/alter-mining-structure-dmx.md)です。  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)  
```  
  
### <a name="example-2-specifying-holdout-percentage-and-seed"></a>例 2 : 提示された割合とシードを指定する  
 次の句を列定義リストの後に追加すると、マイニング構造に関連付けられているすべてのマイニング モデルをテストするためのデータセットを定義できます。 このステートメントでは、ケースの最大数を制限せずに、入力ケースの合計の 25% のテスト セットを作成します。 パーティションを作成するためのシードとして 5000 を使用します。 シードを指定した場合は、基になるデータに変更が生じない限り、マイニング構造を処理するたびに、テスト セットに対して同じケースが選択されます。  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT) REPEATABLE(5000)  
```  
  
### <a name="example-3-specifying-holdout-percentage-and-max-cases"></a>例 3 : 提示された割合とケースの最大数を指定する  
 次の句では、入力ケースの合計の 25% または 2000 ケースのいずれか少ない方を含むテスト セットを作成します。 シードとして 0 が指定されているので、入力ケースのサンプリングの開始に使用されるシードを作成するためにマイニング構造の名前が使用されます。  
  
```  
CREATE MINING STRUCTURE [New Mailing]  
(  
    CustomerKey LONG KEY,   
    Gender TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Bike Buyer] LONG DISCRETE   
)   
WITH HOLDOUT(25 PERCENT OR 2000 CASES) REPEATABLE(0)  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

