---
title: "キューブ階層のプロパティの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies [Analysis Services], multilevel
- hierarchies [Analysis Services], cubes
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dad968995a91d8a163a8ba067925e4dcb07848cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="define-cube-hierarchy-properties"></a>キューブ階層のプロパティの定義
  キューブ階層のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のユーザー定義階層に一意の設定を指定できます。 次の表では、キューブ階層のプロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**有効**|キューブ ディメンションの階層が有効かどうかを決定します。|  
|**HierarchyID**|階層の一意の識別子 (ID) を格納します。|  
|**OptimizedState**|階層に適用される最適化のレベルを決定します。 このプロパティは、以下の値をとります。<br /><br /> **FullyOptimized**:<br />                    インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> **NotOptimized**:<br />                    インスタンスは追加のインデックスを構築しません。|  
|**[表示]**|キューブ階層の表示を決定します。 既定値は **True**です。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
