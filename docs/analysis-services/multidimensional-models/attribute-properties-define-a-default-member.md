---
title: "既定のメンバー定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 642c8ceb45d5a756f8fad396d0fb1bf48138afb0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="attribute-properties---define-a-default-member"></a>属性のプロパティ - 既定のメンバーの定義
  属性階層がクエリに含まれていない場合は、属性階層の既定のメンバーが式の評価に使用されます。 属性階層を示す属性を含む属性階層またはユーザー階層がクエリに含まれる場合は必ず、既定のメンバーは無視されます。 これは、クエリで指定されたメンバーが使用されるためです。  
  
 属性階層の既定のメンバーを設定するには、属性階層の **DefaultMember** プロパティの値として属性メンバーを指定します。 このプロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [ディメンション構造] タブか、キューブ デザイナーの [計算] タブのキューブの計算スクリプトで設定できます。 ディメンションのセキュリティを定義するときに、[ディメンション データ] タブでセキュリティ ロールに **DefaultMember** プロパティを指定する (ディメンションの既定のメンバー セットよりも優先させる) こともできます。 また、キューブが 2 回以上データベース ディメンションを参照する場合、キューブのディメンションにデータベースのディメンションと異なる名前がある場合、または異なるキューブにそれぞれ異なる既定のメンバーを割り当てる場合は、名前解決の問題を回避するために、キューブの MDX スクリプトで既定のメンバーを定義します。  
  
 属性がクエリに含まれていない場合は、属性上の既定のメンバーが式の評価に使用されます。 属性の既定のメンバーは、属性の **DefaultMember** プロパティによって指定されます。 ディメンションからの階層がクエリに含まれている場合は、階層内のレベルに対応する属性からのすべての既定のメンバーは無視されます。 ディメンションの階層がクエリに含まれていない場合は、既定のメンバーがディメンションのすべての属性に対して使用されます。  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>既定のメンバーが指定されていない場合の既定のメンバーの解決  
 属性階層に既定のメンバーが指定されておらず、属性階層が集計可能な場合 (属性の **IsAggregatable** プロパティが **True**に設定されている場合)、(All) メンバーが既定のメンバーです。 既定のメンバーが指定されておらず、属性階層が集計可能でない場合 (属性の **IsAggregatable** プロパティが **False**に設定されている場合)、既定のメンバーは属性階層の最上位から選択されます。  
  
## <a name="specifying-the-default-member"></a>既定のメンバーの指定  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のディメンションの各属性には既定のメンバーが含まれており、属性の **DefaultMember** プロパティを使用して指定できます。 この設定は、属性がクエリに含まれていない場合、式の評価に使用されます。 クエリがディメンションの階層を指定する場合は、階層にある属性の既定のメンバーは無視されます。 クエリがディメンションの階層を指定しない場合は、ディメンション属性の **DefaultMember** 設定が有効になります。  
  
 属性の **DefaultMember** 設定が空白で、その **IsAggregatable** プロパティが **True**に設定されている場合、既定のメンバーは All メンバーです。 **IsAggregatable** プロパティが **False**に設定されている場合、既定のメンバーは最初の表示可能レベルの最初のメンバーです。  
  
 属性の **DefaultMember** 設定は、属性が参加するすべての階層に適用されます。 ディメンションの別の階層に異なる設定を使用することはできません。 たとえば、[1998] メンバーが [Year] 属性の既定のメンバーである場合、この設定はディメンションのすべての階層に適用されます。 この場合、 **DefaultMember** 設定が、ある階層では [1998] で、別の階層では [1997] となることはありません。  
  
 自動的には集計されない階層にある、特定のレベルの既定のメンバーを定義する場合は、階層の上のレベルにあるすべてのレベルの既定のメンバーを定義する必要があります。 たとえば、All-Countries&#x2013;Climate 階層では、Countries の既定のメンバーを定義しないと、Climate の既定のメンバーは定義できません。 これを行わないと、クエリタイム エラーが発生します。  
  
 階層のレベルが自動的に集計される場合は、階層の他の属性に関係なく、階層のどの属性にも既定のメンバーを定義できます。 たとえば、Country&#x2013;Province&#x2013;City の階層では、State または Country の既定のメンバーを定義しなくても、[City].[Montreal] など、City の既定のメンバーを定義できます。  
  
## <a name="see-also"></a>参照  
 [属性階層の &#40;All&#41; レベルの構成](../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  

