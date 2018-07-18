---
title: キューブ属性のプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], defining
ms.assetid: 579ca818-f33d-4060-906d-c8bfee93bf99
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af8e4c54aac81e4f6decdd6533a052fce751b627
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299222"
---
# <a name="define-cube-attribute-properties"></a>キューブ属性のプロパティの定義
  キューブ属性のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のディメンション属性に一意の設定を指定できます。 次の表では、キューブ属性のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`AggregationUsage`|集計デザイン ウィザードによる属性の集計の設計方法を指定します。 このプロパティは、以下の値をとります。<br /><br /> `Default`: 既定値です。 集計デザイン ウィザードは、属性の種類に基づいて既定のルール (キーの場合は Full、その他の場合は Unrestricted) を適用します。<br /><br /> `None`: この属性を含める必要があります、キューブの集計にはありません。<br /><br /> `Unrestricted`: 集計のデザイン ウィザードに対して制限が適用されません。<br /><br /> `Full`: すべてのキューブの集計には、この属性を含める必要があります。|  
|`AttributeHierarchyEnabled`|属性階層をこのキューブ ディメンションで有効にするかどうかを識別します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して無効にすることができます。 この設定は、基になる属性階層が無効になっている場合には影響を受けません。 既定値は`True`します。|  
|`OptimizedState`|属性階層をこのキューブ ディメンションに対して最適化するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して最適化できます。 この設定は、基になる属性階層が最適化されていない場合には影響を受けません。 このプロパティは、以下の値をとります。<br /><br /> `FullyOptimized`: 既定値です。 インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> `NotOptimized`インスタンスでは、追加のインデックスは構築されません。|  
|`AttributeHierarchyVisible`|属性階層をこのキューブ ディメンションで表示するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールで表示できます。 この設定は、基になる属性階層が表示されていない場合には影響を受けません。 既定値は `True` です。|  
|`AttributeID`|属性の一意識別子 (ID) を示します。|  
  
## <a name="see-also"></a>参照  
 [キューブ ディメンションのプロパティを定義します。](define-cube-dimension-properties.md)   
 [キューブ階層のプロパティの定義](define-cube-hierarchy-properties.md)  
  
  
