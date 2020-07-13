---
title: マーケットバスケット DMX のチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe12f1c4ca1c0946572c61e89f4f4edb8ba9a762
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63185644"
---
# <a name="market-basket-dmx-tutorial"></a>マーケット バスケット DMX のチュートリアル
  このチュートリアルでは、データマイニング拡張機能 (DMX) クエリ言語を使用して、マイニングモデルを作成、トレーニング、および調査する方法について説明します。 その後、このマイニング モデルを使用して、同時に購入される傾向が高い製品を示す予測を作成します。  
  
 マイニング モデルは、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータから作成します。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、多国籍の大規模な製造企業です。 北米、ヨーロッパ、およびアジアの市場向けに、金属製自転車や複合材製自転車の製造および販売を行っています。 企業の拠点は従業員 290 人を擁する米国ワシントン州ボセルで、また各国の市場の拠点として、複数の地域販売チームが配置されています。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、データ マイニング機能を用いたカスタム アプリケーションを作成して、同時に購入する傾向が高い製品の種類を予測することにしました。 このカスタム アプリケーションの目標は、一連の製品を指定できるようにし、指定した製品と共に購入される追加製品を予測できるようにすることです。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] はこれらの情報を使用して、企業の Web サイトで "お勧め" の製品を表示すると共に、顧客によりわかりやすく情報を表示したいと考えています。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、このタスクを実行するために使用できるいくつかのツールが用意されてい[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ます。  
  
-   DMX クエリ言語  
  
-   [Microsoft アソシエーションアルゴリズム](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルの作成と作業に使用できるクエリ言語です。 アソシエーション[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズムによって、一緒に購入される可能性のある製品を予測できるモデルが作成されます。  
  
 このチュートリアルの目標は、カスタム アプリケーションで使用する DMX クエリを設定することです。  
  
 **詳細については、「** [データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md)」を参照してください。  
  
## <a name="mining-structure-and-mining-models"></a>マイニング構造とマイニングモデル  
 DMX ステートメントを作成するにあたっては、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] がマイニング モデルの作成に使用する主なオブジェクトを理解しておくことが重要です。 *マイニング構造*は、マイニングモデルの作成元のデータドメインを定義するデータ構造です。 1つのマイニング構造には、同じドメインを共有する複数の*マイニングモデル*を含めることができます。 マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。  
  
 マイニング構造の構成要素は、データ ソースに格納されているデータについて記述したマイニング構造列です。 マイニング構造列には、データ型、コンテンツの種類、データの配布方法などの情報が格納されます。  
  
 マイニング モデルには、マイニング構造で記述されたキー列と、残りの列のサブセットが含まれる必要があります。 マイニング モデルでは、各列の使用法と、マイニング モデルの作成に使用するアルゴリズムを定義します。 たとえば、DMX では列がキー列または PREDICT 列であることを指定できます。 指定されない列は入力列として扱われます。  
  
 DMX でマイニング モデルを作成するには、2 つの方法があります。 1 つは、`CREATE MINING MODEL` ステートメントを使用して、マイニング構造とそれに関連するマイニング モデルを一度に作成する方法です。もう 1 つは、最初に `CREATE MINING STRUCTURE` ステートメントを使用してマイニング構造を作成し、`ALTER STRUCTURE` ステートメントを使用してマイニング モデルを追加する方法です。 これらの方法について次に説明します。  
  
 `CREATE MINING MODEL`  
 このステートメントを使用すると、マイニング構造とそれに関連するマイニング モデルを一度に、同じ名前を使って作成できます。 マイニング構造と区別するため、マイニング モデルの名前には "Structure" という文字列が付加されます。  
  
 このステートメントは、1 つのマイニング モデルを含むマイニング構造を作成する場合に便利です。  
  
 詳細については、「[CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)」を参照してください。  
  
 CREATE MINING STRUCTURE  
 新しいマイニング構造をモデルなしで作成するには、このステートメントを使用します。  
  
 CREATE MINING STRUCTURE を使用すると、予約データ セットも作成できます。予約データ セットは、同一のマイニング構造に基づくすべてのモデルをテストするために使用できます。  
  
 詳細については、「[CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)」を参照してください。  
  
 `ALTER MINING STRUCTURE`  
 このステートメントを使用すると、サーバー上に既に存在するマイニング構造にマイニング モデルを追加できます。  
  
 1 つのマイニング構造に複数のマイニング モデルを追加すると、いくつかの作業に役立ちます。 たとえば、異なるアルゴリズムを使用して複数のマイニング モデルを作成し、最適なアルゴリズムを見つけ出すことができます。 または、同じアルゴリズムを使用して複数のマイニングモデルを作成することもできますが、パラメーターの設定はマイニングモデルごとに異なるため、パラメーターに最適な設定を見つけることができます。  
  
 詳細については、「 [ALTER マイニング STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)」を参照してください。  
  
 このチュートリアルでは複数のマイニング モデルを含むマイニング構造を作成します。したがって、2 つ目の方法を使用します。  
  
 **詳細情報**  
  
 Dmx [&#41; リファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-reference)、Dmx の[Select ステートメント](/sql/dmx/understanding-the-dmx-select-statement)、[構造、および Dmx 予測クエリの使用方法](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)について説明します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: Market Basket マイニング構造の作成](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 このレッスンでは、`CREATE` ステートメントを使用して、マイニング構造を作成する方法を学習します。  
  
 [レッスン 2: Market Basket マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 このレッスンでは、`ALTER` ステートメントを使用して、マイニング モデルをマイニング構造に追加する方法を学習します。  
  
 [レッスン 3: Market Basket マイニング構造の処理](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 このレッスンでは、 `INSERT INTO`ステートメントを使用して、マイニング構造とそれに関連付けられているマイニングモデルを処理する方法について学習します。  
  
 [レッスン 4: マーケット バスケット予測の実行](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 このレッスンでは、`PREDICTION JOIN` ステートメントを使用して、マイニング モデルに対する予測を作成する方法を学習します。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを行う前に、次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース  
  
 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 の[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]公式サンプルデータベースをインストールするには、 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 「」の「Microsoft SQL Server のサンプルとコミュニティプロジェクト」のホームページにアクセスして Microsoft SQL Server 製品サンプルを参照してください。 [**データベース**] をクリックし、[**リリース**] タブをクリックして、目的のデータベースを選択します。  
  
> [!NOTE]  
>  チュートリアルを確認するときは、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [自転車購入者 DMX チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
