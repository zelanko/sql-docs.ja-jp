---
title: "レッスン 4: 定義する高度な属性およびディメンション プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 0e86b9be-e47d-4bb4-87eb-136ff3a61aef
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0b7051c7279cebb104cbf78ef4a224235c197b0e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-4-defining-advanced-attribute-and-dimension-properties"></a>レッスン 4 : 高度な属性およびディメンションのプロパティの定義
このレッスンでは、属性、属性階層、およびディメンションの高度なプロパティをいくつか取り上げ、その使用方法を学習します。  
  
> [!NOTE]  
> このレッスンでは、このチュートリアルの最初の 3 つのレッスンで作成した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの改良版を使用します。 このレッスンの最初の実習では、このレッスンで使用する適切なサンプル プロジェクトの場所を示し、このプロジェクトが最初の 3 つのレッスンで作成したプロジェクトと異なる点を説明します。  
  
このレッスンの内容は次のとおりです。  
  
[Analysis Services チュートリアル プロジェクトの修正バージョンの使用](../analysis-services/lesson-4-1-using-a-modified-version-of-the-analysis-services-tutorial-project.md)  
ここでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの修正バージョンを開き、内容を確認して、配置します。このプロジェクトには、複数のメジャー グループと追加ディメンションが含まれています。  
  
[親子階層の親属性プロパティの定義](../analysis-services/lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
ここでは、親子ディメンションのレベル名を定義し、親メンバーに関連付けられているデータの表示、または非表示を指定します。 詳細については、「 [親子ディメンション](../analysis-services/multidimensional-models/parent-child-dimension.md) 」と「 [親子階層の属性](../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
[属性メンバーの自動的なグループ化](../analysis-services/lesson-4-3-automatically-grouping-attribute-members.md)  
ここでは、属性階層内のメンバーの配置に基づいて、属性メンバーのグループを自動的に作成します。 詳細については、[「属性メンバーのグループ化 (分離)](../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md)」を参照してください。  
  
[属性階層の非表示化と無効化](../analysis-services/lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)  
ここでは、属性階層を無効にし、非表示にする方法と、そのタイミングについて学習します。  
  
[2 次属性に基づく属性メンバーの並べ替え](../analysis-services/lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)  
ここでは、2 次属性に基づいて、ディメンションを目的の順序で並べ替える方法を学習します。  
  
[ユーザー定義階層の属性間での属性リレーションシップの指定](../analysis-services/4-6-specifying-attribute-relationships-in-user-defined-hierarchy.md)  
ここでは、属性のメンバーのプロパティを定義する方法と、プロパティ間の集計リレーションシップを指定する方法を学習します。 詳細については、「 [属性リレーションシップの定義](../analysis-services/multidimensional-models/attribute-relationships-define.md) 」および「 [ユーザー階層プロパティ](../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)」を参照してください。  
  
[不明なメンバーと NULL 処理のプロパティの定義](../analysis-services/lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
この実習では、UnknownMember プロパティと UnknownMemberName プロパティを構成し、null ディメンション メンバーによって発生するエラー状況を処理します。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 5 : ディメンションおよびメジャー グループ間のリレーションシップの定義](../analysis-services/lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services のチュートリアル シナリオ](../analysis-services/analysis-services-tutorial-scenario.md)  
[多次元モデリング (Adventure Works チュートリアル)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
[多次元モデル内のディメンション](../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
  

