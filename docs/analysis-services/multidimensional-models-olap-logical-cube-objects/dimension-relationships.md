---
title: ディメンションのリレーションシップ |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a61931404c298824bbfd29187470bef6875ccfa
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52524462"
---
# <a name="dimension-relationships"></a>ディメンション リレーションシップ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ディメンションを使用する場合は、キューブ内にある、キューブ ディメンションとメジャー グループ間のリレーションシップが定義されます。 キューブ ディメンションとは、特定のキューブで使用されるデータベース ディメンションのインスタンスです。 キューブにはキューブ ディメンションを含めることができ、実際、多くの場合は含んでいます。キューブ ディメンションはメジャー グループと直接には関連付けられていませんが、別のディメンションまたは別のメジャー グループを介して間接的にメジャー グループと関連付けられることがあります。 データベース ディメンションまたはメジャー グループがキューブに追加すると[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を調べて、ディメンション テーブルと、キューブのデータ ソース ビューでは、ファクト テーブル間のリレーションシップを調べて、ディメンションの使用法を判別しようとしています。ディメンションの属性間のリレーションシップ。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、検出できるリレーションシップのディメンションの使用法を自動設定します。  
  
 ディメンションとメジャー グループ間のリレーション シップは、そのリレーション シップに参加しているディメンション テーブルとファクト テーブル、および特定のメジャー グループに含まれているディメンションの粒度を指定する粒度属性で構成されます。  
  
## <a name="regular-dimension-relationships"></a>標準ディメンションのリレーションシップ  
 ディメンションのキー列が直接ファクト テーブルと結合されている場合、キューブ ディメンションとメジャー グループ間には標準ディメンションのリレーションシップが存在します。 この直接的なリレーションシップは、基になるリレーショナル データベース、プライマリ キーと外部キー リレーションシップに基づきますが、データ ソース ビューで定義されている論理リレーションシップに基づくこともあります。 標準ディメンションのリレーションシップは、従来のスター スキーマ デザインにおけるディメンション テーブルとファクト テーブル間のリレーションシップを表します。 通常のリレーションシップの詳細については、次を参照してください。[標準のリレーションシップとファクト リレーションシップのプロパティを定義](../../analysis-services/multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)します。  
  
## <a name="reference-dimension-relationships"></a>参照ディメンション リレーションシップ  
 次の図に示すように、キューブ ディメンションのキー列が別のディメンション テーブルのキーを使用して間接的にファクト テーブルに結合される場合は、このキューブ ディメンションとメジャー グループ間には参照ディメンションのリレーションシップが存在します。  
  
 ![論理図、参照されるディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension1.gif "論理図、参照されるディメンション リレーションシップ")  
  
 参照ディメンションのリレーションシップは、ディメンション テーブルとファクト テーブル間のリレーションシップをスノーフレーク スキーマ デザインで表します。 ディメンション テーブルがスノーフレーク スキーマ形式で関連付けられている場合、複数のテーブルの列を使用して 1 つのディメンションを定義することや、個別のテーブルに基づいて個別のディメンションを定義し、次に、参照ディメンションのリレーションシップの設定を使用してそれらの間にリンクを定義することができます。 という名前の 1 つのファクト テーブルを次に示します**InternetSales**、2 つのディメンション テーブルと**顧客**と**Geography**、スノーフレーク スキーマ。  
  
 ![論理スキーマ、参照されるディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdim-schema1.gif "の論理スキーマ、参照されるディメンション リレーションシップ")  
  
 ディメンションを作成することができます、**顧客**ディメンション メイン テーブルとしてテーブルと**Geography**関連テーブルとして含まれているテーブル。 作成すると、標準のリレーションシップがディメンションと InternetSales メジャー グループ間に定義されます。  
  
 また、InternetSales メジャー グループに関連する 2 つのディメンションを作成することができます: に基づくディメンション、**顧客**テーブル、および基にディメンションを**Geography**テーブル。 次に、Customer ディメンションを使用する参照ディメンションのリレーションシップを使用して Geography ディメンションを InternetSales メジャー グループに関連付けることができます。 この場合、InternetSales メジャー グループ内のファクトを Geography ディメンションを使用して多次元化すると、それらのファクトは顧客別および地域別に多次元化されます。 キューブに Reseller Sales という 2 つ目のメジャー グループが含まれる場合は、Reseller Sales と Geography の間にリレーションシップが存在しないので、Geography を使用して Reseller Sales メジャー グループ内のファクトを多次元化することはできません。  
  
 次の図に示すように、連結できる参照ディメンションの数に上限はありません。  
  
 ![論理図、参照されるディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-refdimension2.gif "論理図、参照されるディメンション リレーションシップ")  
  
 参照リレーションシップの詳細については、次を参照してください。[参照リレーションシップと参照リレーションシップのプロパティを定義](../../analysis-services/multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)します。  
  
## <a name="fact-dimension-relationships"></a>ファクト ディメンションのリレーションシップ  
 ファクト ディメンションは逆ディメンションとも呼ばれますが、ディメンション テーブルの属性列ではなくファクト テーブルの属性列で構築される標準ディメンションです。 重複部分を減らすために、有用な多次元データがファクト テーブルに格納されることがあります。 たとえば、次の図、 **FactResellerSales** 、ファクト テーブルから、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]サンプル データベース。  
  
 ![列のテーブルがディメンションをサポートする実際](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-factdim.gif "列ディメンションをサポートするには、ファクト テーブル")  
  
 このテーブルには、販売店からの注文を格納する各行の属性情報だけではなく、注文自体についても属性情報が格納されています。 前の図で円で囲まれた属性の識別の情報は、 **FactResellerSales**ディメンションの属性として使用できるテーブルです。 この場合、運送業者の問い合わせ番号および販売店からの受注番号という 2 つの付加情報が CarrierTrackingNumber 属性列と CustomerPONumber 属性列によって表されます。 この情報は、興味深い-たとえば、ユーザー間違いなくことに関心を 1 つの追跡番号で発送されたすべての注文のコスト、商品の合計などの集計情報を確認します。 ただし、この 2 つの属性の編成および集計には、ディメンション データが必要です。  
  
 理論上は、FactResellerSales テーブルと同じキー情報を使用するディメンション テーブルを 1 つ作成し、残りの 2 つの属性列である CarrierTrackingNumber と CustomerPONumber をそのディメンション テーブルに移動できます。 ただし、わずか 2 つの属性を別のディメンションとして表すために、非常に多くの重複データを設定し、データ ウェアハウスを不必要に複雑にすることになります。  
  
> [!NOTE]  
>  多くの場合、ファクト ディメンションはドリルスルー アクションをサポートするために使用されます。 アクションの詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。  
  
> [!NOTE]  
>  ファクト ディメンションは、ファクト リレーションシップが参照するメジャー グループが更新されるたびに増分更新する必要があります。 ファクト ディメンションが ROLAP ディメンションの場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 処理エンジンがすべてのキャッシュを削除し、メジャー グループの増分処理を行います。  
  
 ファクト リレーションシップの詳細については、次を参照してください。[ファクト リレーションシップとファクト リレーションシップのプロパティを定義](../../analysis-services/multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)します。  
  
## <a name="many-to-many-dimension-relationships"></a>多対多ディメンションのリレーションシップ  
 ほとんどのディメンションでは、各ファクトは一意のディメンション メンバーと結合していますが、1 つのディメンション メンバーは複数のファクトと関連付けることができます。 リレーショナル データベース用語では、これを一対多のリレーションシップと呼びます。 ただし、多くの場合、1 つのファクトを複数のディメンション メンバーと結合すると便利です。 たとえば、銀行の顧客は複数の口座 (当座預金口座、普通預金口座、クレジット カードの口座、および投資口座) を持つ場合がありますが、1 つの口座に対し、共同所有者がいたり、複数の所有者がいたりするケースもあります。 このようなリレーションシップから作成された顧客ディメンションには、1 回の口座取引に関連付けられるメンバーが複数存在します。  
  
 ![論理スキーマ/多対多のディメンション リレーションシップ](../../analysis-services/multidimensional-models-olap-logical-cube-objects/media/as-many-dimension1.gif "論理スキーマ/多対多のディメンション リレーションシップ")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ディメンションとファクト テーブル間の多対多リレーションシップを定義できます。  
  
> [!NOTE]  
>  上の図に示したように、多対多ディメンションのリレーションシップをサポートするには、データ ソース ビューで、関係するすべてのテーブル間に外部キー リレーションシップを確立する必要があります。 それができないことで、リレーションシップを確立するときに正しい中間メジャー グループを選択する、**ディメンションの使用法**ディメンション デザイナーのタブ。  
  
 多対多リレーションシップの詳細については、次を参照してください。[定義多対多リレーションシップと多対多リレーションシップのプロパティ](../../analysis-services/multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)します。  
  
## <a name="see-also"></a>参照  
 [ディメンション &#40;Analysis Services - 多次元データ&#41;](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
