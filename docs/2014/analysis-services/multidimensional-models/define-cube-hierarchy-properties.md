---
title: キューブ階層のプロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0ace708cc4ee09295380b814bbf21f5a1c350974
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075707"
---
# <a name="define-cube-hierarchy-properties"></a>キューブ階層のプロパティの定義
  キューブ階層のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のユーザー定義階層に一意の設定を指定できます。 次の表では、キューブ階層のプロパティについて説明します。  
  
|プロパティ|[説明]|  
|--------------|-----------------|  
|`Enabled`|キューブ ディメンションの階層が有効かどうかを決定します。|  
|`HierarchyID`|階層の一意の識別子 (ID) を格納します。|  
|`OptimizedState`|階層に適用される最適化のレベルを決定します。 このプロパティは、以下の値をとります。<br /><br /> 
  `FullyOptimized`: インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> 
  `NotOptimized`: インスタンスは追加のインデックスを構築しません。|  
|`Visible`|キューブ階層の表示を決定します。 既定値は `True` です。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
