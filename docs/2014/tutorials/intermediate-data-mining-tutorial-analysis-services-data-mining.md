---
title: 中級レベルのデータ マイニング チュートリアル (Analysis Services - データ マイニング) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 545c219623331ef167731c3142f36642e530307a
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312300"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>中級者向けデータ マイニング チュートリアル (Analysis Services - データ マイニング)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ マイニング モデルの作成と操作の統合環境を提供します。 データ ソースへのバインド、同じデータでの複数のモデルの作成とテスト、および予測分析で使用するモデルの配置を簡単に行うことができます。  
  
 「基本的なデータ マイニング チュートリアル」では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用してデータ マイニング ソリューションを作成する方法を学習し、顧客の購買行動を分析して見込み客を限定するための絞り込みメール配信キャンペーンをサポートする 3 つのモデルを作成しました。  
  
 この中級者向けチュートリアルでは、この使用経験があることを前提に、予測分析やマーケット バスケット分析などの一般的なビジネス要件を含むいくつかの新しいシナリオを紹介します。 そして、時系列モデル、アソシエーション モデル、およびシーケンス クラスター モデルの作成方法を学習します。 最後に、ニューラル ネットワークを使用してデータの相関関係を調べ、ロジスティック回帰を使用して予測を行う方法を学習します。  
  
 レッスンは互いに独立しており、個別に実行できます。  
  
 次のチュートリアルを完了するには、データ マイニング ツールおよび基本的なデータ マイニング チュートリアル」で紹介したマイニング モデル ビューアーについて理解する必要があります。  
  
 すべてのシナリオで [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データ ソースが使用されますが、シナリオごとに異なるデータ ソース ビューを作成します。 データ ソースを最初に作成すれば、後はどの順序でレッスンを進めてもかまいません。  
  
## <a name="lesson-scenarios"></a>レッスンのシナリオ  
 絞り込みメール配信キャンペーンの成功を受けて、データ マイニングの知識を活かしてビジネス プランニングに使用する新しいモデルを開発するように依頼されました。 次のタスクが含まれます。  
  
-   **予測:** を作成、*時系列*世界各地のさまざまな地域内の製品の売上を予測するモデル。 地域ごとの個別モデルを開発して使用する方法について*クロス予測*です。  
  
-   **マーケット バスケット分析:** を作成、*アソシエーション モデル*へのアクセス中に購入される製品のグループを分析する、[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]電子商取引サイトです。 このマーケット バスケット モデルに基づいて、顧客に製品を勧めることができます。  
  
-   **シーケンス分析:** をビルドする、*シーケンス クラスター モデル*顧客が製品を購入順序を分析します。 このモデルに基づいて、Web サイト デザインの変更や新たな製品を計画することができます。  
  
-   **因子分析:** を使用する、*ニューラル ネットワーク*をサービス品質低下コール センター データの考えられる原因を調査するモデル。 予備モデルから洞察をに基づいてができあがります、*ロジスティック回帰モデル*カスタマー エクスペリエンスを向上させるための戦略を予測します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、複数種類のデータ マイニング アルゴリズムの作成方法と使用方法を説明します。 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: 中級者向けデータ マイニング ソリューションの作成&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 このレッスンでは、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースに基づいて、いくつかの新しいデータ ソース ビューと多数のマイニング モデルをサポートする新しいプロジェクトを作成します。  
  
 [レッスン 2: 予測シナリオの作成&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 このレッスンでは、予測シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムを使用して作成されたマイニング モデルの調査も行います。  
  
 個々の地域向けのモデルを作成した後に、クロス予測に使用できる汎用モデルを作成します。  
  
 [レッスン 3: マーケット バスケット シナリオの作成&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 このレッスンでは、新しいデータ ソース ビューを追加し、入れ子になったテーブルとキーを操作する方法について学習します。 このデータを基に、マーケット バスケット シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して作成されたマイニング モデルの調査も行います。  
  
 [レッスン 4: シーケンス クラスター シナリオのビルド&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 このレッスンでは、シーケンス クラスター シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたマイニング モデルを調査する方法についても学習します。  
  
 [レッスン 5: ニューラル ネットワーク モデルとロジスティック回帰モデルの構築&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 このレッスンでは、Microsoft ニューラル ネットワーク アルゴリズムおよび Microsoft ロジスティック回帰アルゴリズムを使用して、関連するいくつかのマイニング モデルを作成します。 また、データ ソース ビューを操作して、モデルの基になるデータを調査する方法についても学習します。  
  
## <a name="requirements"></a>要件  
 次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。  
  
 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 公式データベースをインストールする[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を参照してください、 [Microsoft SQL Sample Databases](http://go.microsoft.com/fwlink/?LinkId=88417)ページし、サンプル データベースの適切なバージョンを選択します。  
  
## <a name="see-also"></a>参照  
 [基本的なデータ マイニングのチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Bike Buyer DMX のチュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [マーケット バスケット DMX のチュートリアル](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  