---
title: 中級者向けデータマイニングチュートリアル (Analysis Services-データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4c244701d8a58765061ef3bde1f918c8be5a941d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63017177"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a>中級者向けデータ マイニング チュートリアル (Analysis Services - データ マイニング)
  [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]には、データマイニングモデルを作成および操作するための統合環境が用意されています。 データ ソースへのバインド、同じデータでの複数のモデルの作成とテスト、および予測分析で使用するモデルの配置を簡単に行うことができます。  
  
 「基本的なデータ マイニング チュートリアル」では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] を使用してデータ マイニング ソリューションを作成する方法を学習し、顧客の購買行動を分析して見込み客を限定するための絞り込みメール配信キャンペーンをサポートする 3 つのモデルを作成しました。  
  
 この中級者向けチュートリアルでは、この使用経験があることを前提に、予測分析やマーケット バスケット分析などの一般的なビジネス要件を含むいくつかの新しいシナリオを紹介します。 そして、時系列モデル、アソシエーション モデル、およびシーケンス クラスター モデルの作成方法を学習します。 最後に、ニューラル ネットワークを使用してデータの相関関係を調べ、ロジスティック回帰を使用して予測を行う方法を学習します。  
  
 レッスンは互いに独立しており、個別に実行できます。  
  
 次のチュートリアルを完了するには、「基本的なデータマイニングチュートリアル」で紹介したデータマイニングツールとマイニングモデルビューアーについて理解しておく必要があります。  
  
 すべてのシナリオで [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データ ソースが使用されますが、シナリオごとに異なるデータ ソース ビューを作成します。 データ ソースを最初に作成すれば、後はどの順序でレッスンを進めてもかまいません。  
  
## <a name="lesson-scenarios"></a>レッスンのシナリオ  
 絞り込みメール配信キャンペーンの成功を受けて、データ マイニングの知識を活かしてビジネス プランニングに使用する新しいモデルを開発するように依頼されました。 これには、次のタスクが含まれます。  
  
-   **予測:***タイムシリーズ*モデルを作成して、世界中のさまざまな地域における製品の売上を予測します。 地域ごとに個別のモデルを開発し、*クロス予測*の使用方法について学習します。  
  
-   **マーケットバスケット分析:** ここでは、 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] e コマースサイトへのアクセス時に購入した製品のグループを分析するための*アソシエーションモデル*を作成します。 このマーケットバスケットモデルに基づいて、顧客に製品を提案することができます。  
  
-   **シーケンス分析:** 顧客が製品を購入する順序を分析するために、*シーケンスクラスターモデル*を構築します。 このモデルに基づいて、Web サイト デザインの変更や新たな製品のオファーを計画することができます。  
  
-   **要因分析:** コールセンターデータのサービス品質の低下の原因を調べるには、*ニューラルネットワーク*モデルを使用します。 暫定モデルからの洞察に基づいて、顧客エクスペリエンスを向上させる戦略を予測する*ロジスティック回帰モデル*を作成します。  
  
## <a name="what-you-will-learn"></a>学習する内容  
 このチュートリアルでは、複数種類のデータ マイニング アルゴリズムの作成方法と使用方法を説明します。 このチュートリアルは次のレッスンで構成されています。  
  
 [レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 このレッスンでは、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベースに基づいて、いくつかの新しいデータ ソース ビューと多数のマイニング モデルをサポートする新しいプロジェクトを作成します。  
  
 [レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 このレッスンでは、予測シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムを使用して作成されたマイニング モデルの調査も行います。  
  
 個々の地域向けのモデルを作成した後に、クロス予測に使用できる汎用モデルを作成します。  
  
 [レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 このレッスンでは、新しいデータ ソース ビューを追加し、入れ子になったテーブルとキーを操作する方法について学習します。 このデータを基に、マーケット バスケット シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して作成されたマイニング モデルの調査も行います。  
  
 [レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 このレッスンでは、シーケンス クラスター シナリオの一部として使用できるマイニング モデルを作成します。 また、[!INCLUDE[msCoName](../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたマイニング モデルを調査する方法についても学習します。  
  
 [レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 このレッスンでは、Microsoft ニューラル ネットワーク アルゴリズムおよび Microsoft ロジスティック回帰アルゴリズムを使用して、関連するいくつかのマイニング モデルを作成します。 また、データ ソース ビューを操作して、モデルの基になるデータを調査する方法についても学習します。  
  
## <a name="requirements"></a>要件  
 次のソフトウェアがインストールされていることを確認してください。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] と [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データベース。  
  
 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。 の[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]公式データベースをインストールするには、 [Microsoft SQL サンプル](https://go.microsoft.com/fwlink/?LinkId=88417)データベースのページにアクセスし、適切なバージョンのサンプルデータベースを選択します。  
  
## <a name="see-also"></a>参照  
 [基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [自転車購入者 DMX チュートリアル](../../2014/tutorials/bike-buyer-dmx-tutorial.md)   
 [マーケット バスケット DMX のチュートリアル](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
