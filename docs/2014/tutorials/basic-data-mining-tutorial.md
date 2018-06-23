---
title: 基本的なデータ マイニング チュートリアル |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
caps.latest.revision: 48
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 92e55dccdd72e07b4303d6c996a002fc4fcca8af
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312390"
---
# <a name="basic-data-mining-tutorial"></a>基本的なデータ マイニング チュートリアル
  ようこそ、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]基本的なデータ マイニングのチュートリアルです。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ マイニング モデルを作成して、予測を作成するための統合環境を提供します。 このチュートリアルでは、機械学習を分析および顧客の購買行動を予測を使用するターゲット メーリング キャンペーンのシナリオを完了します。 このチュートリアルでは、クラスタリング、デシジョン ツリー、Naive Bayes (ナイーブ ベイズ) という非常に重要な 3 つのデータ マイニング アルゴリズムを使用する方法を示します。 マイニング モデル ビューアーを使用して結果の分析および予測と精度チャートに含まれているデータ マイニング ツールを使用して作成する方法も学習[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。 すべての例で、架空の企業である [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] を使用します。  
  
 完了することもお勧め慣れてデータ マイニング ツールを使用して、ときに、[中級者向けデータ マイニング チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)です。 これらのレッスンでは、予測、マーケット バスケット分析、タイム シリーズ (時系列)、アソシエーション モデル、入れ子になったテーブル、およびシーケンス クラスターの使用方法を示します。  
  
## <a name="tutorial-scenario"></a>チュートリアルのシナリオ  
 このチュートリアルでは、従業員は[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]命じられた購買履歴に基づいて会社の顧客に関する詳細と、予測を行うために使用できるマーケティングにした履歴データを使用します。 会社はこれまでデータ マイニングを行ったことがなかったので、データ マイニング専用の新しいデータベースを作成し、データ マイニング モデルを設定する必要があります。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、さまざまな種類の機械学習メソッドの作成方法と使用方法を説明します。 また、マイニング モデルのコピーを作成し、入力データにフィルターを適用してさまざまな結果を取得する方法も学習します。 その後、リフト チャートを使用して、両方のモデルの結果を比較できます。 最後に、ドリルスルーを使用して、基になるマイニング構造から詳細なデータを取得します。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ マイニングには、次が含まれています。 簡単にできるようにする機能の開発と比較を複数の予測モデルの結果に操作を実行します。  
  
-   *提示されたテストの設定 -* トレーニング セットとテスト セットにマイニング構造内のデータを分割するマイニング構造を作成するときにようになりましたことができます。 これにより、類似のデータ セットに対してモデルをテストし、関連するモデルの精度を比較できます。  
  
-   *マイニング モデルのフィルター -* フィルターをマイニング モデルにアタッチし、トレーニングとテストの両方にフィルターを適用できます。 これにより、データの異なるサブセットに対して関連モデルを簡単に構築できます。  
  
-   *構造ケースおよび構造列へのドリルスルー*簡単に移動できます、マイニング モデルでの一般的なパターンから実用的な詳細データ ソースにします。  
  
 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: 準備、Analysis Services データベース&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 このレッスンでは、新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを作成する方法、データ ソースとデータ ソース ビューを追加する方法、およびデータ マイニングで使用する新しいデータベースを準備する方法を学習します。  
  
 [レッスン 2: 絞り込み構造の作成&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 このレッスンでは、絞り込みメール配信シナリオの一部として使用できるマイニング モデル構造の作成方法を学習します。  
  
 [レッスン 3: モデルの追加と処理](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 このレッスンでは、構造にモデルを追加する方法を学習します。 モデルの作成には、次のアルゴリズムを使用します。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] デシジョン ツリー  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] クラスター  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes  
  
 [レッスン 4: 絞り込みモデルの検証&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 このレッスンでは、ビューアーを使用して各モデルの結果を調査および解釈する方法を学習します。  
  
 [レッスン 5: モデルのテスト&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 このレッスンでは、いずれかの絞り込みメール配信モデルのコピーを作成し、トレーニング データを制限するためのマイニング モデル フィルターを特定の顧客のセットに追加し、モデルの実行可能性を評価します。  
  
 [レッスン 6: の作成と操作の予測&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 「基本的なデータ マイニング チュートリアル」の最後のレッスンでは、モデルを使用して、自転車を購入する可能性が最も高い顧客を予測します。 次に、基になるケースをドリルスルーして連絡先情報を取得します。  
  
## <a name="requirements"></a>要件  
 次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元モードで  
  
-   [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。  
  
 セキュリティ強化のため、サンプル データベースは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と一緒にインストールされません。 公式データベースをインストールする[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を参照してください、 [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417)ページし、選択[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]です。  
  
> [!NOTE]  
>  チュートリアルを行う作業しているときにした方を簡単に追加する場合、手順の間で前後に移動、**次のトピック「** と**前のトピック**ドキュメント ビューアーのツールバーのボタンです。  
  
## <a name="see-also"></a>参照  
 [データ マイニング ソリューション](../../2014/analysis-services/data-mining/data-mining-solutions.md)   
 [マイニング モデル タスクと操作方法](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [作成して、dmx データ マイニング モデルのクエリ: チュートリアル&#40;Analysis Services - データ マイニング&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  