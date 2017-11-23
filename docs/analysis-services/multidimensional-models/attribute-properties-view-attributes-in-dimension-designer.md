---
title: "ディメンション デザイナーの属性を表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec4596584aafb35d54506d244855447b0ce67c7f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="attribute-properties---view-attributes-in-dimension-designer"></a>属性のプロパティ - ディメンション デザイナーでの属性の表示
  属性はディメンション オブジェクトで作成されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のディメンション デザイナーを使用して、属性を表示したり構成したりできます。 ディメンション デザイナーの **[ディメンション構造]** タブの **[属性]** ペインには、ディメンションの属性が一覧表示されます。 このペインを使用して、属性の追加、削除、または構成を行います。 また、新しい階層でレベルとして使用する属性や、既存の階層にレベルとして追加する属性を選択できます。  
  
 ディメンションの属性を表示するには、そのディメンションのディメンション デザイナーを開きます。 ディメンション デザイナーの **[ディメンション構造]** タブの **[属性]**  ペインに、ディメンションの属性が表示されます。 **の** [ディメンション] **メニューで** [属性を表示] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をポイントし、次のいずれかのコマンドをクリックして、リスト ビュー、ツリー ビュー、グリッド ビューを切り替えることができます。  
  
1.  **[リスト]**。 属性を一覧形式で表示します。 一覧から属性を削除したり、属性の名前を変更したり、属性の使用法を変更したりするには、その属性を右クリックします。 このビューは階層の構築に使用します。 属性の情報とメンバーのプロパティは表示されません。  
  
2.  **[ツリー]**。 ディメンションをツリーのトップレベル ノードとして、属性をツリー形式で表示します。 属性の属性リレーションシップを表示したり、新しい属性リレーションシップを作成したりするには、次の操作を実行して、その属性を展開します。  
  
    -   ディメンション、属性、またはメンバー プロパティをクリックして、 **[プロパティ]** ウィンドウにそのプロパティを表示します。  
  
    -   属性またはメンバー プロパティを右クリックして、一覧から削除したり、名前を変更したり、その使用法を変更したりします。  
  
     このビューは、メンバー プロパティの表示と作成に使用します。 また、階層の構築にも使用できます。  
  
3.  **[グリッド]**。 属性をグリッド形式で表示します。 グリッドには次の列が表示されます。  
  
    -   **[名前]** には **Name** プロパティの値が表示されます。 設定を変更するには、別の名前を入力します。  
  
    -   **[使用法]** では、これが Regular、Key、Parent、AccountType のいずれの属性であるかを指定します。 別の設定を選択するには、この列の値をクリックします。  
  
    -   **[種類]** では、属性のビジネス インテリジェンス カテゴリを指定します。 別の設定を選択するには、このセルをクリックします。  
  
    -   **[キー列]** には、属性の **KeyColumn** プロパティの OLE DB データ型が表示されます。 この列は変更できません。  
  
    -   **[名前列]** は、属性の **NameColumn** プロパティの設定が **KeyColumn** プロパティの設定と同じ列であるかどうかを示します。 この列は変更できません。  
  
     その属性のプロパティを表示するには、グリッドのいずれかの行をクリックします。  
  
     このビューは、属性の作成と構成に使用します。  
  
 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]では、属性の使用法に応じて、次の表のアイコンが属性に付いています。  
  
|アイコン|属性の使用法|  
|----------|---------------------|  
|![属性アイコン](../../analysis-services/multidimensional-models/media/as-icon-attribute.gif "属性アイコン")|Regular または AccountType|  
|![キー属性アイコン](../../analysis-services/multidimensional-models/media/as-icon-key-attribute.gif "キー属性アイコン")|Key|  
|![親属性アイコン](../../analysis-services/multidimensional-models/media/as-icon-parent-attribute.gif "親属性アイコン")|Parent|  
  
## <a name="see-also"></a>参照  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
