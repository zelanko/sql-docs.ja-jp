---
title: 基本的なデータマイニングチュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d434df95a26485d4d7795d3ab960b8d2457b8ff6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63185576"
---
# <a name="basic-data-mining-tutorial"></a>基本的なデータ マイニング チュートリアル
  「 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]基本的なデータマイニングチュートリアル」へようこそ。 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]には、データマイニングモデルを作成し、予測を行うための統合環境が用意されています。 このチュートリアルでは、機械学習を使用して顧客の購買行動を分析および予測することで、絞り込みメール配信キャンペーンのためのシナリオを完成させます。 このチュートリアルでは、クラスタリング、デシジョン ツリー、Naive Bayes (ナイーブ ベイズ) という非常に重要な 3 つのデータ マイニング アルゴリズムを使用する方法を示します。 また、マイニングモデルビューアーを使用して結果を分析する方法や、に[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]含まれるデータマイニングツールを使用して予測と精度チャートを作成する方法についても説明します。 すべての例で、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] を使用します。  
  
 データマイニングツールを使い慣れている場合は、「[中間データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」も完了することをお勧めします。 これらのレッスンでは、予測、マーケット バスケット分析、タイム シリーズ (時系列)、アソシエーション モデル、入れ子になったテーブル、およびシーケンス クラスターの使用方法を示します。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 このチュートリアルでは、購入履歴に基づい[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]て会社の顧客の詳細を学習し、その履歴データを使用してマーケティングで使用できる予測を作成した従業員の従業員です。 会社はこれまでデータ マイニングを行ったことがなかったので、データ マイニング専用の新しいデータベースを作成し、データ マイニング モデルを設定する必要があります。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、さまざまな種類の機械学習メソッドの作成方法と使用方法を説明します。 また、マイニング モデルのコピーを作成し、入力データにフィルターを適用してさまざまな結果を取得する方法も学習します。 その後、リフト チャートを使用して、両方のモデルの結果を比較できます。 最後に、ドリルスルーを使用して、基になるマイニング構造から詳細なデータを取得します。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データマイニングには、複数の予測モデルを簡単に開発して比較し、結果に対してアクションを実行するために役立つ次の機能があります。  
  
-   *予約テストセット-* マイニング構造を作成するときに、マイニング構造のデータをトレーニングセットとテストセットに分割できるようになりました。 これにより、類似のデータ セットに対してモデルをテストし、関連するモデルの精度を比較できます。  
  
-   *マイニングモデルフィルター-* これで、フィルターをマイニングモデルにアタッチし、トレーニングとテストの両方でフィルターを適用できるようになりました。 これにより、データの異なるサブセットに対して関連モデルを簡単に構築できます。  
  
-   *構造ケースおよび構造列へのドリルスルー-* マイニングモデルの一般的なパターンから、データソース内の実用的な詳細に簡単に移動できるようになりました。  
  
 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: Analysis Services データベースの準備 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 このレッスンでは、新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを作成する方法、データ ソースとデータ ソース ビューを追加する方法、およびデータ マイニングで使用する新しいデータベースを準備する方法を学習します。  
  
 [レッスン 2: &#40;の基本的なデータマイニングチュートリアルでは、絞り込みメール配信構造の作成&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 このレッスンでは、絞り込みメール配信シナリオの一部として使用できるマイニング モデル構造の作成方法を学習します。  
  
 [レッスン 3: モデルの追加と処理](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 このレッスンでは、構造にモデルを追加する方法を学習します。 モデルの作成には、次のアルゴリズムを使用します。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]デシジョンツリー  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]クラスター  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]Naive Bayes  
  
 [レッスン 4: 「基本的なデータマイニングチュートリアル」 &#40;対象を絞ったメーリングモデルの調査&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 このレッスンでは、ビューアーを使用して各モデルの結果を調査および解釈する方法を学習します。  
  
 [レッスン 5: モデルのテスト &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 このレッスンでは、いずれかの絞り込みメール配信モデルのコピーを作成し、トレーニング データを制限するためのマイニング モデル フィルターを特定の顧客のセットに追加し、モデルの実行可能性を評価します。  
  
 [レッスン 6: 予測の作成と操作 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 「基本的なデータ マイニング チュートリアル」の最後のレッスンでは、モデルを使用して、自転車を購入する可能性が最も高い顧客を予測します。 次に、基になるケースをドリルスルーして連絡先情報を取得します。  
  
## <a name="requirements"></a>必要条件  
 次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   
  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。  
  
 セキュリティ強化のため、サンプル データベースは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と一緒にインストールされません。 の[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]公式データベースをインストールするには、 [Microsoft SQL サンプルデータベース](https://go.microsoft.com/fwlink/?LinkId=88417)のページに[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]アクセスし、を選択してください。  
  
> [!NOTE]  
>  チュートリアルを通じて作業する場合、ドキュメントビューアーのツールバーに**次のトピック**と**前のトピック**のボタンを追加すると、手順を前後に移動しやすくなることがあります。  
  
## <a name="see-also"></a>参照  
 [データマイニングソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md)   
 [マイニングモデルタスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [DMX を使用したデータマイニングモデルの作成とクエリ: チュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
