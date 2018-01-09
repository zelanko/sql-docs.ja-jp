---
title: "属性リレーションシップのプロパティを構成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bcc42c8bcd73c52851f3ed7fae5f4f7a4915b450
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="attribute-relationships---configure-attribute-properties"></a>属性リレーションシップ-属性のプロパティを構成します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]次の表と、属性リレーションシップのプロパティを示しています。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|属性|属性の名前を示します。|  
|Cardinality|リレーションシップの基数を示します。 値は、多対一リレーションシップの場合は Many、一対一リレーションシップの場合は One です。 既定値は Many です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、Cardinality プロパティには効力がありません。このプロパティの使用は、将来の実装に向けて予約されています。|  
|[オブジェクト名]|属性のよく似た名前を示します。|  
|RelationshipType|メンバーのリレーションシップが時間を経て変化するかどうかを示します。 値が Rigid の場合、メンバー間のリレーションシップが時間を経て変化しないことを意味し、値が Flexible の場合は、メンバー間のリレーションシップが時間を経て変化することを意味します。 既定では Flexible です。 リレーションシップを Flexible に定義すると、集計は削除され、増分更新の一部として再計算されます (新しいメンバーだけが追加された場合、集計は削除されません)。 リレーションシップを Rigid に定義すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではディメンションが増分更新されたときの集計が維持されます。 Rigid に定義されているリレーションシップが実際に変化した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では増分処理時にエラーが生成されます。 適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。|  
|[表示]|属性リレーションシップの表示を決めます。 値は True または False です。 既定値は True です。|  
  
  
