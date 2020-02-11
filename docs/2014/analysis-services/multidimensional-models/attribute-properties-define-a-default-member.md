---
title: 既定のメンバーを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959645223eacec6c000ddbfa23615b7949d10d5a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077418"
---
# <a name="define-a-default-member"></a>既定のメンバーの定義
  属性階層がクエリに含まれていない場合は、属性階層の既定のメンバーが式の評価に使用されます。 属性階層を示す属性を含む属性階層またはユーザー階層がクエリに含まれる場合は必ず、既定のメンバーは無視されます。 これは、クエリで指定されたメンバーが使用されるためです。  
  
 属性階層の既定のメンバーを設定するには、属性階層の `DefaultMember` プロパティの値として属性メンバーを指定します。 このプロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [ディメンション構造] タブか、キューブ デザイナーの [計算] タブのキューブの計算スクリプトで設定できます。 ディメンションのセキュリティを定義するときに、[ディメンション データ] タブでセキュリティ ロール (ディメンションの既定のメンバー セットをオーバーライドしている) に `DefaultMember` プロパティを指定することもできます。 また、キューブが 2 回以上データベース ディメンションを参照する場合、キューブのディメンションにデータベースのディメンションと異なる名前がある場合、または異なるキューブにそれぞれ異なる既定のメンバーを割り当てる場合は、名前解決の問題を回避するために、キューブの MDX スクリプトで既定のメンバーを定義します。  
  
 属性がクエリに含まれていない場合は、属性上の既定のメンバーが式の評価に使用されます。 属性の既定のメンバーは、属性の `DefaultMember` プロパティによって指定されます。 ディメンションからの階層がクエリに含まれている場合は、階層内のレベルに対応する属性からのすべての既定のメンバーは無視されます。 ディメンションの階層がクエリに含まれていない場合は、既定のメンバーがディメンションのすべての属性に対して使用されます。  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>既定のメンバーが指定されていない場合の既定のメンバーの解決  
 属性階層に既定のメンバーが指定されておらず、属性階層が集計可能な場合 (属性の `IsAggregatable` プロパティが `True` に設定されている場合)、(All) メンバーが既定のメンバーです。 既定のメンバーが指定されおらず、属性階層が集計可能でない場合 (属性の `IsAggregatable` プロパティが `False` に設定されている場合)、既定のメンバーは属性階層の最上位から選択されます。  
  
## <a name="specifying-the-default-member"></a>既定のメンバーの指定  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ディメンションのすべての属性には、既定のメンバーがあります。このメンバー `DefaultMember`は、属性のプロパティを使用して指定できます。 この設定は、属性がクエリに含まれていない場合、式の評価に使用されます。 クエリがディメンションの階層を指定する場合は、階層にある属性の既定のメンバーは無視されます。 ディメンションに階層が指定されていないクエリの場合`DefaultMember` 、ディメンション属性の設定が有効になります。  
  
 属性の`DefaultMember`設定が空白で、その`IsAggregatable`プロパティがに`True`設定されている場合、既定のメンバーは All メンバーです。 `IsAggregatable`プロパティがに`False`設定されている場合、既定のメンバーは最初に表示されるレベルの最初のメンバーになります。  
  
 属性`DefaultMember`の設定は、属性が参加するすべての階層に適用されます。 ディメンションの別の階層に異なる設定を使用することはできません。 たとえば、[1998] メンバーが [Year] 属性の既定のメンバーである場合、この設定はディメンションのすべての階層に適用されます。 この`DefaultMember`場合の設定は、1つの階層では [1998]、別の階層では [1997] にすることはできません。  
  
 自動的には集計されない階層にある、特定のレベルの既定のメンバーを定義する場合は、階層の上のレベルにあるすべてのレベルの既定のメンバーを定義する必要があります。 たとえば、[すべての国-環境] という階層では、国の既定のメンバーを定義しない限り、気候の既定のメンバーを定義することはできません。 これを行わないと、クエリタイム エラーが発生します。  
  
 階層のレベルが自動的に集計される場合は、階層の他の属性に関係なく、階層のどの属性にも既定のメンバーを定義できます。 たとえば、"hierarchy Country-City" の場合、[City] など、City の既定のメンバーを定義できます。[モントリオール] State または Country の既定のメンバーを定義する必要はありません。  
  
## <a name="see-also"></a>参照  
 [属性階層のすべての&#41; レベル &#40;を構成する](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
