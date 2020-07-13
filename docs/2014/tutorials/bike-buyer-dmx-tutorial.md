---
title: 自転車購入者 DMX チュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 4b634cc1-86dc-42ec-9804-a19292fe8448
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3cf9a0c9e6059330c0b8edbd8228f617ba093564
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63140551"
---
# <a name="bike-buyer-dmx-tutorial"></a>Bike Buyer DMX のチュートリアル
  このチュートリアルでは、データ マイニング拡張機能 (DMX) クエリ言語を使用して、マイニング モデルを作成、トレーニング、および調査する方法を学習します。 その後、これらのマイニング モデルを使用して、顧客が自転車を購入するかどうかを判断する予測を作成します。  
  
 マイニング モデルは、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータから作成します。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、多国籍の大規模な製造企業です。 北米、ヨーロッパ、およびアジアの市場向けに、金属製自転車や複合材製自転車の製造および販売を行っています。 その基本操作は、ワシントン州と290人の従業員の両方に存在し、国際的な市場ベースを通じて複数の地域販売チームがいます。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、データ マイニング機能を用いたカスタム アプリケーションを作成して、データ分析を拡張することにしました。 このカスタム アプリケーションでは、次の機能を実現することを目標にします。  
  
-   潜在顧客の特性を入力し、潜在顧客が自転車を購入するかどうかを予測する。  
  
-   特性の他に潜在顧客の一覧も入力し、どの顧客が自転車を購入するかを予測する。  
  
 1 つ目のケースでは、顧客登録ページから顧客データを取得し、2 つ目のケースでは、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門が潜在顧客の一覧を提供するようにします。  
  
 マーケティング部門には、さらに住所、子どもの数、通勤距離などの特性に基づいて既存の顧客を分類するという要求が出されています。 この分類を使用して、特定の種類の顧客に的を絞ることができるかどうか確認することが求められています。 これには、追加のマイニング モデルが必要です。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、これらのタスクを実行するために使用できるいくつかのツールが用意されてい[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ます。  
  
-   DMX クエリ言語  
  
-   [Microsoft デシジョンツリーアルゴリズム](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)と[microsoft クラスタリングアルゴリズム](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルの作成と作業に使用できるクエリ言語です。 [!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー アルゴリズムを使用すると、顧客が自転車を購入するかどうかの予測に使用できるモデルを作成できます。 作成したモデルには、個別の顧客または複数の顧客のテーブルを入力できます。 [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスタリング アルゴリズムを使用すると、共通の特性に基づいて顧客のグループを作成できます。 このチュートリアルの目標は、カスタム アプリケーションで使用する DMX スクリプトを設定することです。  
  
 **詳細については、「** [データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md)」を参照してください。  
  
## <a name="mining-structure-and-mining-models"></a>マイニング構造とマイニングモデル  
 DMX ステートメントを作成するにあたっては、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がマイニング モデルの作成に使用する主なオブジェクトを理解しておくことが重要です。 マイニング構造は、マイニング モデルの作成元のデータ ドメインを定義するデータ構造です。 1 つのマイニング構造には、同じドメインを共有する複数のマイニング モデルを含めることができます。 マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。  
  
 マイニング構造の構成要素は、データ ソースに格納されているデータについて記述したマイニング構造列です。 マイニング構造列には、データ型、コンテンツの種類、データの配布方法などの情報が格納されます。  
  
 マイニング モデルには、マイニング構造で記述されたキー列と、残りの列のサブセットが含まれる必要があります。 マイニング モデルでは、各列の使用法と、マイニング モデルの作成に使用するアルゴリズムを定義します。 たとえば、DMX では列がキー列または PREDICT 列であることを指定できます。 指定されない列は入力列として扱われます。  
  
 DMX でマイニング モデルを作成するには、2 つの方法があります。 1 つは、CREATE MINING MODEL ステートメントを使用して、マイニング構造とそれに関連するマイニング モデルを一度に作成する方法です。もう 1 つは、最初に CREATE MINING STRUCTURE ステートメントを使用してマイニング構造を作成し、ALTER STRUCTURE ステートメントを使用してマイニング モデルを追加する方法です。 次の表でこれらの方法について説明します。  
  
 CREATE MINING MODEL  
 このステートメントを使用すると、マイニング構造とそれに関連するマイニング モデルを一度に、同じ名前を使って作成できます。 マイニング構造と区別するため、マイニング モデルの名前には "Structure" という文字列が付加されます。 このステートメントは、1 つのマイニング モデルを含むマイニング構造を作成する場合に便利です。  
  
 詳細については、「[CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)」を参照してください。  
  
 ALTER MINING STRUCTURE  
 このステートメントを使用すると、サーバー上に既に存在するマイニング構造にマイニング モデルを追加できます。 このステートメントは、複数の異なるマイニング モデルを含むマイニング構造を作成する場合に便利です。 1 つのマイニング構造に複数のマイニング モデルを追加すると、いくつかの作業に役立ちます。 たとえば、異なるアルゴリズムを使用する複数のマイニング モデルを作成し、最適なアルゴリズムを見つけ出すことができます。 また、同じアルゴリズムでそれぞれ異なるパラメーターを設定して複数のマイニング モデルを作成し、パラメーターの最適な設定を見つけ出すことができます。  
  
 詳細については、「 [ALTER マイニング STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)」を参照してください。  
  
 このチュートリアルでは複数のマイニング モデルを含むマイニング構造を作成します。したがって、2 つ目の方法を使用します。  
  
 **詳細情報**  
  
 Dmx [&#41; リファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-reference)、Dmx の[Select ステートメント](/sql/dmx/understanding-the-dmx-select-statement)、[構造、および Dmx 予測クエリの使用方法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)について説明します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: Bike Buyer マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)  
 このレッスンでは、`CREATE` ステートメントを使用して、マイニング構造を作成する方法を学習します。  
  
 [レッスン 2: Bike Buyer マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
 このレッスンでは、`ALTER` ステートメントを使用して、マイニング モデルをマイニング構造に追加する方法を学習します。  
  
 [レッスン 3: Bike Buyer マイニング構造の処理](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
 このレッスンでは、`INSERT INTO` ステートメントを使用して、マイニング構造とそれに関連するマイニング モデルを処理する方法を学習します。  
  
 [レッスン 4: Bike Buyer マイニング モデルの参照](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
 このレッスンでは、`SELECT` ステートメントを使用してマイニング モデルの内容を調査する方法を学習します。  
  
 [レッスン 5: 予測クエリの実行](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
 このレッスンでは、`PREDICTION JOIN` ステートメントを使用して、マイニング モデルに対する予測を作成する方法を学習します。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを行う前に、次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]、 [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)]、 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]、また[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]は[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 の[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]公式サンプルデータベースをインストールするには、 [Microsoft SQL サンプルデータベース](https://go.microsoft.com/fwlink/?LinkId=88417)のページにアクセスし、インストールするデータベースを選択してください。  
  
> [!NOTE]  
>  チュートリアルを確認するときは、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [マーケットバスケット DMX のチュートリアル](../../2014/tutorials/market-basket-dmx-tutorial.md)   
 [基本的なデータ マイニング チュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
  
