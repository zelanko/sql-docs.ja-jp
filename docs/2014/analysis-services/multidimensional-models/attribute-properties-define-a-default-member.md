---
title: 既定のメンバー定義 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
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
manager: mblythe
ms.openlocfilehash: 3b89100b174df0d70306e42d3ae850cb3257ce52
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175627"
---
# <a name="define-a-default-member"></a>既定のメンバーの定義
  属性階層がクエリに含まれていない場合は、属性階層の既定のメンバーが式の評価に使用されます。 属性階層を示す属性を含む属性階層またはユーザー階層がクエリに含まれる場合は必ず、既定のメンバーは無視されます。 これは、クエリで指定されたメンバーが使用されるためです。  
  
 として属性メンバーを指定することによって、属性階層の既定のメンバーが設定されて、`DefaultMember`属性階層のプロパティの値。 このプロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のディメンション デザイナーの [ディメンション構造] タブか、キューブ デザイナーの [計算] タブのキューブの計算スクリプトで設定できます。 ディメンションのセキュリティを定義するときに、[ディメンション データ] タブでセキュリティ ロール (ディメンションの既定のメンバー セットをオーバーライドしている) に `DefaultMember` プロパティを指定することもできます。 また、キューブが 2 回以上データベース ディメンションを参照する場合、キューブのディメンションにデータベースのディメンションと異なる名前がある場合、または異なるキューブにそれぞれ異なる既定のメンバーを割り当てる場合は、名前解決の問題を回避するために、キューブの MDX スクリプトで既定のメンバーを定義します。  
  
 属性がクエリに含まれていない場合は、属性上の既定のメンバーが式の評価に使用されます。 属性の既定のメンバーがで指定された、`DefaultMember`属性のプロパティです。 ディメンションからの階層がクエリに含まれている場合は、階層内のレベルに対応する属性からのすべての既定のメンバーは無視されます。 ディメンションの階層がクエリに含まれていない場合は、既定のメンバーがディメンションのすべての属性に対して使用されます。  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>既定のメンバーが指定されていない場合の既定のメンバーの解決  
 場合は、属性階層の既定のメンバーが指定されていないと、属性階層が集計可能では (、`IsAggregatable`属性にプロパティに設定`True`)、(All) メンバーは、既定のメンバーです。 既定のメンバーが指定されていないと、属性階層が集計可能でない場合 (、`IsAggregatable`属性にプロパティに設定`False`)、既定のメンバーは、属性階層の最上位レベルから選択します。  
  
## <a name="specifying-the-default-member"></a>既定のメンバーの指定  
 内のディメンションのすべての属性[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は既定のメンバーを使用して指定することができますが、`DefaultMember`属性のプロパティです。 この設定は、属性がクエリに含まれていない場合、式の評価に使用されます。 クエリがディメンションの階層を指定する場合は、階層にある属性の既定のメンバーは無視されます。 クエリがディメンションでは、階層を指定しない場合、`DefaultMember`ディメンション属性の設定は有効にします。  
  
 場合、`DefaultMember`属性が空白の設定とその`IsAggregatable`プロパティに設定されている`True`既定のメンバーがすべてのメンバーです。 場合、`IsAggregatable`プロパティに設定されている`False`既定のメンバーが可視の最上位レベルの最初のメンバーです。  
  
 `DefaultMember`属性が参加するすべての階層に属性が適用されるを設定します。 ディメンションの別の階層に異なる設定を使用することはできません。 たとえば、[1998] メンバーが [Year] 属性の既定のメンバーである場合、この設定はディメンションのすべての階層に適用されます。 `DefaultMember`設定ここではできません。 [1998] [1997] と 1 つの階層で別の階層にします。  
  
 自動的には集計されない階層にある、特定のレベルの既定のメンバーを定義する場合は、階層の上のレベルにあるすべてのレベルの既定のメンバーを定義する必要があります。 たとえば、All-Countries&#x2013;Climate 階層では、Countries の既定のメンバーを定義しないと、Climate の既定のメンバーは定義できません。 これを行わないと、クエリタイム エラーが発生します。  
  
 階層のレベルが自動的に集計される場合は、階層の他の属性に関係なく、階層のどの属性にも既定のメンバーを定義できます。 たとえば、Country&#x2013;Province&#x2013;City の階層では、State または Country の既定のメンバーを定義しなくても、[City].[Montreal] など、City の既定のメンバーを定義できます。  
  
## <a name="see-also"></a>参照  
 [構成、&#40;すべて&#41;属性階層のレベル](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  