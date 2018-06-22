---
title: キューブ階層のプロパティの定義 |Microsoft ドキュメント
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
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 199e00331e26cea5c84242582f9c6382215ad411
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071574"
---
# <a name="define-cube-hierarchy-properties"></a>キューブ階層のプロパティの定義
  キューブ階層のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のユーザー定義階層に一意の設定を指定できます。 次の表では、キューブ階層のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`Enabled`|キューブ ディメンションの階層が有効かどうかを決定します。|  
|`HierarchyID`|階層の一意の識別子 (ID) を格納します。|  
|`OptimizedState`|階層に適用される最適化のレベルを決定します。 このプロパティは、以下の値をとります。<br /><br /> `FullyOptimized`インスタンスは、クエリのパフォーマンスを向上させるために、階層のインデックスを構築します。 これが既定値です。<br /><br /> `NotOptimized`: インスタンスでは、追加のインデックスは構築されません。|  
|`Visible`|キューブ階層の表示を決定します。 既定値は `True` です。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  