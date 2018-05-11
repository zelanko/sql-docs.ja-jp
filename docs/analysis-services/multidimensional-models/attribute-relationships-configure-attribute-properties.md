---
title: 属性リレーションシップのプロパティを構成する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0fd5bc7535cb4bfe45fcaae3a904d5574d540b9c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-relationships---configure-attribute-properties"></a>属性リレーションシップ-属性のプロパティを構成します。
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  次の表で、属性リレーションシップのプロパティの一覧およびその説明を示します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|属性|属性の名前を示します。|  
|Cardinality|リレーションシップの基数を示します。 値は、多対一リレーションシップの場合は Many、一対一リレーションシップの場合は One です。 既定値は Many です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、Cardinality プロパティには効力がありません。このプロパティの使用は、将来の実装に向けて予約されています。|  
|名前|属性のよく似た名前を示します。|  
|RelationshipType|メンバーのリレーションシップが時間を経て変化するかどうかを示します。 値が Rigid の場合、メンバー間のリレーションシップが時間を経て変化しないことを意味し、値が Flexible の場合は、メンバー間のリレーションシップが時間を経て変化することを意味します。 既定では Flexible です。 リレーションシップを Flexible に定義すると、集計は削除され、増分更新の一部として再計算されます (新しいメンバーだけが追加された場合、集計は削除されません)。 リレーションシップを Rigid に定義すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではディメンションが増分更新されたときの集計が維持されます。 Rigid に定義されているリレーションシップが実際に変化した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では増分処理時にエラーが生成されます。 適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。|  
|[表示]|属性リレーションシップの表示を決めます。 値は True または False です。 既定値は True です。|  
  
  
