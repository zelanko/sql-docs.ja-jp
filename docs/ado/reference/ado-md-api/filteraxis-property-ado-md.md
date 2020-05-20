---
title: FilterAxis プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: rothja
ms.author: jroth
ms.openlocfilehash: b7f9b34757970ce98dedaa9601340cad533ad002
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764233"
---
# <a name="filteraxis-property-ado-md"></a>FilterAxis プロパティ (ADO MD)
現在の[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)に関するフィルター情報を示します。  
  
## <a name="return-values"></a>戻り値  
 は[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)オブジェクトを返し、は読み取り専用です。  
  
## <a name="remarks"></a>Remarks  
 データのスライスに使用されたディメンションに関する情報を返すには、 **Filteraxis**プロパティを使用します。 **軸**の[dimensioncount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)プロパティは、スライサーディメンションの数を返します。 通常、この軸には1行しかありません。  
  
 **Filteraxis**によって返された**軸**は、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトの[Axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)コレクションに含まれていません。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Axis オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Dimension オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [DimensionCount プロパティ (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
