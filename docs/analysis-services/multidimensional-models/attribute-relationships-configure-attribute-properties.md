---
title: 属性リレーションシップのプロパティの構成 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a7270dd698dfb8d3d3002c302186e97b912044f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179287"
---
# <a name="attribute-relationships---configure-attribute-properties"></a>属性リレーションシップ - 属性のプロパティの構成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  次の表で、属性リレーションシップのプロパティの一覧およびその説明を示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|属性|属性の名前を示します。|  
|Cardinality|リレーションシップのカーディナリティを示します。 値は、多対一リレーションシップの場合は Many、一対一リレーションシップの場合は One です。 既定値は Many です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、カーディナリティ プロパティに効果はなく、その使用方法は将来の実装のために予約されています。|  
|名前|属性のよく似た名前を示します。|  
|RelationshipType|メンバーのリレーションシップが時間を経て変化するかどうかを示します。 値が Rigid の場合、メンバー間のリレーションシップが時間を経て変化しないことを意味し、値が Flexible の場合は、メンバー間のリレーションシップが時間を経て変化することを意味します。 既定では Flexible です。 リレーションシップを Flexible に定義すると、集計は削除され、増分更新の一部として再計算されます (新しいメンバーだけが追加された場合、集計は削除されません)。 リレーションシップを Rigid に定義すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではディメンションが増分更新されたときの集計が維持されます。 Rigid に定義されているリレーションシップが実際に変化した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では増分処理時にエラーが生成されます。 適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。|  
|Visible|属性リレーションシップの表示を決めます。 値は True または False です。 既定値は True です。|  
  
  
