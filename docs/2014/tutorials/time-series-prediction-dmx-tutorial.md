---
title: 時系列予測の DMX のチュートリアルの時間 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2a9e3e5db1e0f21bfe3822d73fd0e3c0b456e250
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312200"
---
# <a name="time-series-prediction-dmx-tutorial"></a>時系列予測の DMX のチュートリアル
  このチュートリアルでは、時系列マイニング構造を作成し、3 つのカスタム時系列マイニング モデルを作成し、それらのモデルを使用して予測を行う方法を学習します。  
  
 マイニング モデルの作成は、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] サンプル データベース内のデータに基づいて行います。このサンプル データベースには、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のデータが格納されています。 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、多国籍の大規模な製造企業です。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] は、データ マイニングを使用して売上予測を生成することにしました。 一部地域の予測モデルが既に作成されています。詳細については、次を参照してください。[レッスン 2: Building a Forecasting Scenario&#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)です。 営業部門で、そのデータ マイニング モデルを新しい売上データで定期的に更新できるようにする必要があります。 また、さまざまな予測が得られるようにモデルをカスタマイズしたいとも考えています。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] このタスクの実行に使用できるいくつかのツールを提供します。  
  
-   データ マイニング拡張機能 (DMX) クエリ言語  
  
-   Microsoft タイム シリーズ アルゴリズム  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のクエリ エディター  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムでは、時間に関するデータの予測に使用できるモデルが作成されます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で提供されるデータ マイニング拡張機能 (DMX) は、マイニング モデルと予測クエリの作成に使用できるクエリ言語です。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でマイニング モデルを作成するために使用するオブジェクトについて理解していることを前提にしています。 既に作成されていない場合、マイニング構造またはマイニング モデル DMX を使用してを参照してください。 [Bike Buyer DMX のチュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)です。  
  
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
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベース  
  
 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 公式サンプル データベースをインストールする[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に進み、 [ http://www.CodePlex.com/MSFTDBProdSamples ](http://go.microsoft.com/fwlink/?LinkId=88417)または Microsoft SQL Server の製品サンプル セクションに Microsoft SQL Server のサンプルとコミュニティのプロジェクトのホーム ページです。 をクリックして**データベース**、をクリックして、**リリース**タブし、データベースを選択します。  
  
> [!NOTE]  
>  追加することをお勧めのチュートリアルを確認するときに**次のトピック「** と**前のトピック**ドキュメント ビューアーのツールバーのボタンです。  
  
## <a name="see-also"></a>参照  
 [基本的なデータ マイニングのチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [データ マイニング チュートリアルを中間&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  