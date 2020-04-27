---
title: '[ソースキューブディメンションの選択] (データマイニングウィザード)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb61763a49bad7eae1a49a01633ec8f45e27642
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069233"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a>[ソース キューブ ディメンションの選択] (データ マイニング ウィザード)
  **[ソース キューブ ディメンションの選択]** ページを使用すると、分析する対象のケースを含んでいるキューブからディメンションを選択できます。 たとえば、人口統計に基づいて顧客の購入行動を分析するモデルを構築する場合は、Customer ディメンションを選択します。一般に、このディメンションには、顧客ごとに固有のレコードが含まれているほか、性別、居住地、所得など、人口統計の内訳を表す各種の属性が含まれます。 ウィザードの後半では、このケース テーブルに関連したテーブルを追加できます。たとえば、顧客が購入した製品を表す、入れ子になったテーブルを追加することも可能です。  
  
> [!NOTE]  
>   このページは、ウィザードの **[定義方法の選択]** ページで **[既存のキューブを使用する]** を選択した場合にのみ表示されます。  
  
## <a name="options"></a>オプション  
 **[ソース キューブ ディメンションの選択]**  
 マイニング構造のソース データを提供するキューブのディメンションを選択します。  
  
## <a name="choosing-a-dimension"></a>ディメンションの選択  
 モデルに使用するディメンションは 1 つしか選択できません。したがって、キューブの構造を十分に理解し、目的のモデルに合った情報を提供するうえで最も適したディメンションを選ぶことが重要です。 どのディメンションを使用すればよいか迷った場合は、ディメンション デザイナーを使用してキューブを参照し、そこに含まれているフィールドとデータを調べます。 詳細については、「[ディメンション デザイナーでのディメンション データの参照](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md)」をご覧ください。  
  
 ディメンション全般について詳しく理解するには、「[ディメンションの概要 (Analysis Services - 多次元データ)](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)」をご覧ください。  
  
 データ マイニングに役立つ属性やメジャーなど、1 つのディメンションに含まれる代表的な情報の種類については、「[ディメンション リレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」をご覧ください。  
  
 データ マイニング モデルを構築するために必要な属性が、選択したディメンションにない場合は、ディメンションに対する変更が必要になることもあります。 詳細については、「 [データベース ディメンションの定義](multidimensional-models/define-database-dimensions.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [データマイニング構造 &#40;データマイニングウィザードの作成&#41;](create-the-data-mining-structure-data-mining-wizard.md)   
 [[ケースキー &#40;データマイニングウィザード] を選択し&#41;](select-the-case-key-data-mining-wizard.md)  
  
  
