---
title: "ドリルスルー クエリ (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AllowDrillThrough property
- drillthrough [Analysis Services]
- drillthrough [DMX]
ms.assetid: 246c784b-1b0c-4f0b-96f7-3af265e67051
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1cb15acfcc31572a34c6bf2fe6c3ec75101a9fd0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drillthrough-queries-data-mining"></a>ドリルスルー クエリ (データ マイニング)
  *ドリルスルー クエリ* を使用すると、マイニング モデルにクエリを送信して、基になるケースまたは構造データから詳細を取得できます。 ドリルスルーは、モデルのトレーニングに使用されたケースとテストに使用されたケースを比較する際や、ケース データの詳細を確認する際に役立ちます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ マイニングは、ドリルスルーの次の 2 つのオプションを提供します。  
  
-   **モデル ケース**へのドリルスルー  
  
     モデル ケースへのドリルスルーは、デシジョン ツリーのクラスターや分岐などのモデル内の特定のパターンからドリルし、個々のケースの詳細を表示するときに使用します。  
  
-   **構造ケース**へのドリルスルー  
  
     構造ケースのドリルスルーは、モデル内で使用できない情報が構造に含まれている際に使用します。 たとえば、構造のデータとして顧客の連絡先情報が含まれていても、クラスター モデルでは使用しません。 しかし、モデルを作成した後に、特定のクラスターにグループ化された顧客に関する連絡先情報を取得する必要が生じる場合もあります。  
  
 ここでは、こようなクエリの作成例を紹介します。  
  
 [データ マイニング デザイナーでのドリルスルーの使用](#bkmk_Designer)  
  
 [DMX を使用したドリルスルー クエリの作成](#bkmk_DMX)  
  
 [ドリルスルーの使用に関する注意点](#bkmk_Considerations)  
  
-   [セキュリティの問題](#bkmk_Security)  
  
-   [制限事項](#bkmk_Limits)  
  
##  <a name="bkmk_Designer"></a> データ マイニング デザイナーでのドリルスルーの使用  
 ドリルスルーを許可するようにマイニング モデルが構成されており、ユーザーが適切な権限を持っている場合、モデルの参照時に適切なビューアーでノードをクリックすると、そのノード内のケースに関する詳細情報を取得できます。  
  
 [マイニング モデルからケース データにドリルスルーする](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)  
  
 マイニング構造を処理したときにトレーニング ケースがキャッシュされており、かつユーザーが必要な権限を持っている場合は、モデル ケースとマイニング構造から情報を返すことができます。マイニング モデルに含まれていなかった列も同様に返すことができます。  
  
##  <a name="bkmk_DMX"></a> DMX を使用したドリルスルー クエリの作成  
 モデルまたは構造に対する権限がある場合は、DMX クエリを作成することでケース データをドリルスルーできます。 DMX でドリルスルー クエリを作成する構文の例については、次のトピックを参照してください。  
  
 [DMX を使用したドリルスルー クエリの作成](../../analysis-services/data-mining/create-drillthrough-queries-using-dmx.md)  
  
##  <a name="bkmk_Considerations"></a> ドリルスルーの使用に関する注意点  
  
-   データ マイニング ウィザードを使用する場合は、最終ページにモデル ケースへのドリルスルーを有効にするオプションがあります。 既定では、ドリルスルーは無効になっています。 詳細については、「[ウィザードの完了 (データ マイニング ウィザード)](http://msdn.microsoft.com/library/6aef1548-35eb-42fd-ae87-63650a79eda1)」を参照してください。  
  
-   既存のマイニング モデルにドリルスルー機能を追加することは可能ですが、その場合、データをドリルスルーする前にモデルを再処理する必要があります。  
  
-   マイニング構造を処理したときにキャッシュされたトレーニング ケースに関する情報が取得されることで、ドリルスルーが機能します。 そのため、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **ClearAfterProcessing**に変更して、構造の処理後、キャッシュされたデータを消去した場合、ドリルスルーは機能しません。 構造列へのドリルスルーを有効にするには、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **KeepTrainingCases** に変更してから構造を再処理する必要があります。  
  
-   ドリルスルーがマイニング構造で許可されておらず、マイニング モデルでは許可されている場合、マイニング構造の情報は表示できず、モデル ケースの情報のみを表示できます。  
  
###  <a name="bkmk_Security"></a> ドリルスルーのセキュリティに関する問題  
 モデルから構造ケースにドリルスルーする場合は、マイニング構造とマイニング モデルの両方で [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) プロパティが **True**に設定されていることを確認する必要があります。 さらに、構造とモデルの両方に対するドリルスルー権限を持つロールのメンバーである必要があります。 ロールを作成する方法については、「[ロール デザイナー (Analysis Services - 多次元データ)](http://msdn.microsoft.com/library/e8ba42db-0565-4d68-b3ab-0c63d8d07192)」を参照してください。 参照してください。  
  
 ドリルスルー権限は、構造およびモデルで個別に設定されます。 構造で権限が与えられていない場合でも、モデル権限があればモデルからドリルスルーを行うことができます。 構造のドリルスルー権限がある場合は、[StructureColumn (DMX)](../../dmx/structurecolumn-dmx.md) 関数を使用して、構造列をモデルからドリルスルー クエリに含めることもできます。  
  
> [!NOTE]  
>  マイニング構造とマイニング モデルの両方についてドリルスルーを有効にした場合、そのマイニング モデルに対するドリルスルー権限を持つロールのすべてのメンバー ユーザーが、マイニング構造内の列を表示できるようになります。これらの列がマイニング モデルに含まれていなかったとしても同様です。 したがって、機密データを保護するため、個人情報をマスクするデータ ソース ビューを設定し、マイニング構造に対するドリルスルー アクセスは必要な場合にのみ許可する必要があります。  
  
###  <a name="bkmk_Limits"></a> ドリルスルーに関する制限事項  
  
-   モデルのドリルスルー操作には、モデルの作成に使用したアルゴリズムに応じて、次の制限事項が適用されます。  
  
|アルゴリズム名|問題点|  
|--------------------|-----------|  
|Microsoft Naïve Bayes アルゴリズム|サポートされていません。 これらのアルゴリズムでは、コンテンツ内の特定のノードにケースが割り当てられません。|  
|Microsoft ニューラル ネットワーク アルゴリズム|サポートされていません。 これらのアルゴリズムでは、コンテンツ内の特定のノードにケースが割り当てられません。|  
|Microsoft ロジスティック回帰アルゴリズム|サポートされていません。 これらのアルゴリズムでは、コンテンツ内の特定のノードにケースが割り当てられません。|  
|Microsoft 線形回帰アルゴリズム|サポートされています。 ただし、モデルによって作成されるノードが **All**だけであるため、ドリルスルーすると、モデルのすべてのトレーニング ケースが返されます。 トレーニング セットが大きいと、結果の読み込みに非常に時間がかかることがあります。|  
|Microsoft タイム シリーズ アルゴリズム (Microsoft Time Series algorithm)|サポートされています。 ただし、構造やケース データのドリルスルーに、データ マイニング デザイナーの **[マイニング モデル ビューアー]** を使用することはできません。 代わりに、DMX クエリを作成する必要があります。<br /><br /> また、タイム シリーズ モデルでは、特定のノードをドリルスルーしたり、特定のノード内のケースを取得する DMX クエリを記述したりすることができません。 日付や属性値などの他の条件を使用して、モデルや構造からケース データを取得することは可能です。<br /><br /> [Lag (DMX)](../../dmx/lag-dmx.md) 関数を使用すると、モデルのケースから日付を返すこともできます。<br /><br /> Microsoft タイム シリーズ アルゴリズムで作成された ARTXP ノードおよび ARIMA ノードの詳細を表示する場合は、[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c) を使用できます。|  
  
##  <a name="bkmk_Tasks"></a> 関連タスク  
 次のリンクを使用して特定のシナリオでのドリルスルーを行います。  
  
|タスク|リンク|  
|----------|----------|  
|データ マイニング デザイナーでのドリルスルーの使用を記述するプロシージャ|[マイニング モデルからケース データにドリルスルーする](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)|  
|既存のマイニング モデルを変更してドリルスルーを許可するには|[マイニング モデルのドリルスルーの有効化](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)|  
|DMX WITH DRILLTHROUGH 句を使用してマイニング構造のドリルスルーを有効にする|[CREATE MINING STRUCTURE (DMX)](../../dmx/create-mining-structure-dmx.md)|  
|マイニング構造とマイニング モデルにドリルスルーを適用する権限の割り当ての詳細について|[データ マイニング構造およびデータ マイニング モデルに対する権限の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)|  
  
## <a name="see-also"></a>参照  
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)  
  
  

