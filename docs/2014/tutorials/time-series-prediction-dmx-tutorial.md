---
title: 時系列予測 DMX のチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 1623f824c062c270268323fd45ebf0e9533c8788
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63044189"
---
# <a name="time-series-prediction-dmx-tutorial"></a>時系列予測の DMX のチュートリアル
  このチュートリアルでは、時系列マイニング構造を作成し、3 つのカスタム時系列マイニング モデルを作成し、それらのモデルを使用して予測を行う方法を学習します。  
  
 マイニング モデルの作成は、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータに基づいて行います。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、多国籍の大規模な製造企業です。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、データ マイニングを使用して売上予測を生成することにしました。 既にいくつかのリージョン予測モデルが構築されています。詳細については、「[レッスン 2: 予測シナリオの作成」 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)を参照してください。 営業部門で、そのデータ マイニング モデルを新しい売上データで定期的に更新できるようにする必要があります。 また、さまざまな予測が得られるようにモデルをカスタマイズしたいとも考えています。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、このタスクを実行するために使用できるいくつかのツールが用意されてい[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]ます。  
  
-   データ マイニング拡張機能 (DMX) クエリ言語  
  
-   Microsoft タイムシリーズアルゴリズム  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムでは、時間に関するデータの予測に使用できるモデルが作成されます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルと予測クエリの作成に使用できるクエリ言語です。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でマイニング モデルを作成するために使用するオブジェクトについて理解していることを前提にしています。 DMX を使用してマイニング構造またはマイニングモデルをまだ作成していない場合は、「[自転車購入者向け Dmx チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)」を参照してください。  
  
 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: 時系列マイニング モデルおよびマイニング構造の作成](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 このレッスンでは、`CREATE MINING MODEL` ステートメントを使用して、新しい予測モデルと関連マイニング モデルを追加する方法を学習します。  
  
 [レッスン 2: 時系列マイニング構造へのマイニング モデルの追加](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 このレッスンでは、ALTER MINING STRUCTURE ステートメントを使用して、新しいマイニング モデルを時系列構造に追加する方法を学習します。 また、時系列の分析に使用されるアルゴリズムをカスタマイズする方法も学習します。  
  
 [レッスン 3: 時系列構造と時系列モデルの処理](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 このレッスンでは、`INSERT INTO` ステートメントを使用して [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースのデータを構造に取り込むことによってモデルをトレーニングする方法を学習します。  
  
 [レッスン 4: DMX を使用した時系列予測の作成](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 このレッスンでは、時系列予測を作成する方法を学習します。  
  
 [レッスン 5 : 時系列モデルの拡張](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 このレッスンでは、`EXTEND_MODEL_CASES` パラメーターを使用して、予測を行うときに新しいデータでモデルを更新する方法を学習します。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを行う前に、次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース  
  
 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 の[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]公式サンプルデータベースをインストールするには、 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 「」の「Microsoft SQL Server のサンプルとコミュニティプロジェクト」のホームページにアクセスして Microsoft SQL Server 製品サンプルを参照してください。 [**データベース**] をクリックし、[**リリース**] タブをクリックして、目的のデータベースを選択します。  
  
> [!NOTE]  
>  チュートリアルを確認するときは、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [中級者向けデータマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
