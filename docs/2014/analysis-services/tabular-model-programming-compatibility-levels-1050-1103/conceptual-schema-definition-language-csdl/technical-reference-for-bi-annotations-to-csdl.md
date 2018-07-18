---
title: Csdl の BI 注釈のテクニカル リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 63b3e069-6ba5-474e-b769-47b7cc87b7dd
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78300a412d7db986edd76172c7cf49e6c86aaec9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192392"
---
# <a name="technical-reference-for-bi-annotations-to-csdl"></a>CSDL への BI 注釈のテクニカル リファレンス
  このセクションでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] テーブル モデルを表すために使用される CSDL の要素、属性、およびプロパティの一覧を示します。 一部の新規要素以外は、ビジネス インテリジェンス モデリングをサポートするために注釈が付加されたか、拡張されたものです。  
  
 表形式モデルと CSDL のエンティティ、リレーションシップ、および数式を表現する方法の概要については、次を参照してください。[ビジネス インテリジェンス向け CSDL 注釈&#40;CSDLBI&#41;](../csdl-annotations-for-business-intelligence-csdlbi.md)します。  
  
## <a name="extended-csdl-elements-complex-types"></a>拡張 CSDL 要素: 複合型  
 CSDL の次の要素が、テーブルと多次元の両方のビジネス インテリジェンス データ モデルをサポートするために追加または拡張されました。  
  
-   [AssociationSet 要素&#40;CSDLBI&#41;](associationset-element-csdlbi.md)  
  
-   [BaseProperty 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [DefaultDetails 要素&#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md)  
  
-   [DisplayKey 要素&#40;CSDLBI&#41;](displaykey-element-csdlbi.md)  
  
-   [EntityContainer 要素&#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)  
  
-   [EntitySet 要素&#40;CSDLBI&#41;](entityset-element-csdlbi.md)  
  
-   [EntityType 要素&#40;CSDLBI&#41;](entitytype-element-csdlbi.md)  
  
-   [Hierarchy 要素&#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)  
  
-   [KPI 要素&#40;CSDLBI&#41;](kpi-element-csdlbi.md)  
  
-   [KpiGoal 要素&#40;CSDLBI&#41;](kpigoal-element-csdlbi.md)  
  
-   [KpiStatus 要素&#40;CSDLBI&#41;](kpistatus-element-csdlbi.md)  
  
-   [上位の要素&#40;CSDLBI&#41;](level-element-csdlbi.md)  
  
-   [要素の測定&#40;CSDLBI&#41;](measure-element-csdlbi.md)  
  
-   [Member 要素&#40;CSDLBI&#41;](member-element-csdlbi.md)  
  
-   [MemberRef 要素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)  
  
-   [NavigationProperty 要素&#40;CSDLBI&#41;](navigationproperty-element-csdlbi.md)  
  
-   [Property 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)  
  
-   [PropertyRef 要素&#40;CSDLBI&#41;](propertyref-element-csdlbi.md)  
  
## <a name="simple-type-and-subtypes"></a>単純型とサブタイプ  
 次の表に、前の一覧の複合型の定義に含まれる単純型と副次的な複合型の一部を示します。 左列の単純型とサブタイプについてのドキュメントは、右列の親要素で用意されています。  
  
|単純型|トピックを参照します。|  
|-----------------|--------------------|  
|Alignment|[BaseProperty 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|CompareOptions|[EntityContainer 要素&#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|目次|[EntityType 要素&#40;CSDLBI&#41;](entitytype-element-csdlbi.md)|  
|ContextualNameRule|[Member 要素&#40;CSDLBI&#41;](member-element-csdlbi.md)|  
|DefaultAggregationFunction|[Property 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|DirectQueryMode|[EntityContainer 要素&#40;CSDLBI&#41;](entitycontainer-element-csdlbi.md)|  
|GroupingBehavior|[Property 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|MemberRefs|[MemberRef 要素&#40;CSDLBI&#41;](memberref-element-csdlbi.md)|  
|PropertyRefs|[PropertyRef 要素&#40;CSDLBI&#41;](propertyref-element-csdlbi.md)|  
|SortDirection|[BaseProperty 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|状態|[AssociationSet 要素&#40;CSDLBI&#41;](associationset-element-csdlbi.md)|  
|Stability|[Property 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
|SortDirection|[BaseProperty 要素&#40;CSDLBI&#41;](property-element-csdlbi.md)|  
  
## <a name="see-also"></a>参照  
 [CSDLBI の概念](../csdlbi-concepts.md)  
  
  
