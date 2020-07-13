---
title: ソリューションとデータソースの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0488b231-1045-4169-aabb-c1005d86ca30
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 21bedc825f5890e3eb6551818dc5dc10724d2bf8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68891438"
---
# <a name="creating-a-solution-and-data-source-intermediate-data-mining-tutorial"></a>ソリューションとデータ ソースの作成 (中級者向けデータ マイニング チュートリアル)
  データ マイニングを使用するには、最初に [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] で **[Analysis Services 多次元およびデータ マイニング プロジェクト]** テンプレートを使用して、プロジェクトを作成する必要があります。 テンプレートを開くと、データ ソース、マイニング構造、マイニング モデル、さらにマイニング構造で多次元データが使用される場合はキューブまで、データ マイニングに必要なすべてのスキーマがデザイナーに読み込まれます。  
  
 プロジェクトを作成すると、ソリューションは配置されるまでローカル ファイルとして保存されます。 ソリューションを配置すると、プロジェクトのプロパティに指定された [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーが [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] によって検索され、プロジェクトと同じ名前の新しい [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースが作成されます。 既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は新しいプロジェクトに対して **localhost** インスタンスを使用します。 名前付きインスタンスを使用している場合、または既定のインスタンスに別の名前を指定した場合は、プロジェクトの配置データベース プロパティを、データ マイニング オブジェクトを作成する場所に変更する必要があります。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトの詳細については、「 [Create a ANALYSIS SERVICES Project &#40;SSDT&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt)」を参照してください。  
  
### <a name="to-create-a-new-analysis-services-project-for-this-tutorial"></a>このチュートリアル用の新しい Analysis Services プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]を開きます。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  **[インストールされているテンプレート]** ペインの **[Analysis Services 多次元およびデータ マイニング プロジェクト]** をクリックします。  
  
4.  **[名前]** ボックスに、新しいプロジェクトの名前「 **DM Intermediate**」を入力します。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-instance-where-data-mining-objects-are-stored-optional"></a>データ マイニング オブジェクトを格納するインスタンスを変更するには (オプション)  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。  
  
3.  サーバー名 **** が **localhost**であることを確認します。 別のインスタンスを使用する場合は、インスタンスの名前を入力します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の名前付きインスタンスを使用する場合は、コンピューター名とインスタンス名を入力します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-change-the-deployment-properties-for-a-project-optional"></a>プロジェクトの配置プロパティを変更するには (オプション)  
  
1.  ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[プロパティ]** をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[プロパティ ページ]** ペインの左側で、 **[配置]** をクリックします。  
  
     **[オプション]** ペインで **[配置モード]** をクリックし、上書きする場合はオプションを **[すべて配置]** に設定し、オブジェクトを更新するかオブジェクトを追加する場合は **[変更のみを配置]** に設定します。  
  
## <a name="creating-a-data-source"></a>データ ソースの作成  
 「基本的なデータ マイニング チュートリアル」では、 *データベースの接続情報を格納する* データ ソース [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] を作成しました。 このソリューションでは、同じ手順で [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] データ ソースを作成します。  
  
#### <a name="to-create-a-data-source"></a>データ ソースを作成するには  
  
-   [データソースの作成 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
 1 つのデータ ソースで複数のデータ ソース ビューをサポートできます。また、各データ ソース ビューには複数のテーブルを含めることができます。 ただし、データソースとデータソースビューは、作成するデータマイニング[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]モデルと共にデータベースに配置されるため、ベストプラクティスとして、各データソースビューにはデータマイニングモデルまたはモデルのグループごとに必要なテーブルのみを含めることをお勧めします。  
  
 以降のレッスンでは、それぞれの新しいシナリオをサポートするデータ ソース ビューを追加します。 マーケット バスケットのレッスンとシーケンス クラスターのレッスンのみ、同じデータ ソース ビューを使用します。それ以外は、各シナリオは異なるデータ ソース ビューを使用するため、各レッスンは互いに無関係であり、別々に実行できます。  
  
|シナリオ|データ ソース ビューに含まれているデータ|  
|--------------|-------------------------------------------|  
|[レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)|単一のビューとして収集された、各地域での各自転車モデルの月間の売上レポート。|  
|[レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)|顧客注文の一覧を含むテーブルと、各顧客の購入記録を示す入れ子になったテーブル。|  
|[レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)|マーケット バスケット分析に使用したものと同じデータに、品目の購入順序を示す識別子が追加されています。|  
|[レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)|コール センターのいくつかの事前パフォーマンス追跡データを含む単一のテーブル。|  
  
## <a name="next-lesson"></a>次のレッスン  
 [レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [データマイニングプロジェクト](../../2014/analysis-services/data-mining/data-mining-projects.md)   
 [多次元モデル内のデータ ソース ビュー](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
