---
title: 属性リレーションシップのプロパティの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- flexible relationships (Analysis Services)
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
- properties [Analysis Services], attribute relationships
- rigid relationships (Analysis Services)
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 241fa2af16377fd2cacf657ec6f99c5ca4bd0c53
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544704"
---
# <a name="configure-attribute-relationship-properties"></a>属性リレーションシップのプロパティの構成
  次の表で、属性リレーションシップのプロパティの一覧およびその説明を示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|属性|属性の名前を示します。|  
|カーディナリティ|リレーションシップのカーディナリティを示します。 値は、多対一リレーションシップの場合は Many、一対一リレーションシップの場合は One です。 既定値は Many です。 では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、カーディナリティプロパティは効果がありません。その使用は将来の実装のために予約されています。|  
|名前|属性のよく似た名前を示します。|  
|RelationshipType|メンバーのリレーションシップが時間を経て変化するかどうかを示します。 値が Rigid の場合、メンバー間のリレーションシップが時間を経て変化しないことを意味し、値が Flexible の場合は、メンバー間のリレーションシップが時間を経て変化することを意味します。 既定では Flexible です。 リレーションシップを Flexible に定義すると、集計は削除され、増分更新の一部として再計算されます (新しいメンバーだけが追加された場合、集計は削除されません)。 リレーションシップを Rigid に定義すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではディメンションが増分更新されたときの集計が維持されます。 Rigid に定義されているリレーションシップが実際に変化した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では増分処理時にエラーが生成されます。 適切なリレーションシップとリレーションシップのプロパティを指定すると、クエリ パフォーマンスと処理パフォーマンスが向上します。|  
|Visible|属性リレーションシップの表示を決めます。 値は True または False です。 既定値は True です。|  
  
  
