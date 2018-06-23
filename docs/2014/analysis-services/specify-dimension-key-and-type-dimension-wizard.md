---
title: ディメンションのキーおよび種類 (ディメンション ウィザード) を指定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1ce08115251beee6dc71509bc4d3a53420ecd678
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163944"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>[ディメンションのキーおよび種類を指定] (ディメンション ウィザード)
  **[ディメンションのキーおよび種類を指定]** ページを使用すると、ディメンションのキー属性を定義でき、ディメンションが SCD (緩やかに変化するディメンション) であるかどうかを示すことができます。  
  
> [!NOTE]  
>  このページは、 **[構築方法の選択]** ページの **[データ ソースを使用せずにディメンションを構築する]** が選択され、 **[ディメンションの種類の選択]** ページの **[標準ディメンション]** が選択されている場合のみ表示されます。  
  
## <a name="options"></a>および  
 **キー属性**  
 ディメンションのキー属性となる属性を選択します。  
  
> [!NOTE]  
>  ディメンションの属性が定義されていない場合、このオプションに使用できる値は **[キー属性を自動的に作成します]** のみとなります。 この値は、ディメンションの属性が定義されている場合は使用できません。  
  
 **これは、変化するディメンション**  
 ディメンションが緩やかに変化するディメンションであることを示します。 このオプションを選択すると、時間経過と共にディメンションの階層内でメンバーが移動するのを追跡するために使用できる追加の列および属性が作成されます。  
  
## <a name="see-also"></a>参照  
 [ディメンション ウィザードの F1 ヘルプ](dimension-wizard-f1-help.md)   
 [ディメンション&#40;Analysis Services - 多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  