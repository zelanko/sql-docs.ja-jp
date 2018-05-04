---
title: FilterAxis プロパティ (ADO MD) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7ba6b397879039064943fcb6264ef3dd76aa8fc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis プロパティ (ADO MD)
現在のフィルター情報を示す[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)です。  
  
## <a name="return-values"></a>戻り値  
 返します、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)オブジェクト、および読み取り専用です。  
  
## <a name="remarks"></a>解説  
 使用して、 **FilterAxis**プロパティ データをスライスするために使用されたディメンションに関する情報を返します。 [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)のプロパティ、**軸**スライサー ディメンションの数を返します。 この軸には、通常、1 行だけがあります。  
  
 **軸**によって返される**FilterAxis**に含まれていない、[軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)のコレクション、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [軸オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [ディメンション オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount プロパティ (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
