---
title: "序数に基づくプロパティ (ADO MD のセル) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b6928eeeb7450b2edbd244d70d3c6a8aa999343a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="ordinal-property-ado-md-cell"></a>序数に基づくプロパティ (ADO MD のセル)
一意に識別、[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)セル セット内の位置によってです。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**整数であり、読み取り専用です。  
  
## <a name="remarks"></a>解説  
 セルの序数値は、セルセット内のセルを一意に識別します。 概念的には、セルの番号付けは、セル セットで、セルセットが、 *p*-次元の配列、 *p*の数は、[軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)です。 セルは、行優先順で 0 から始まる番号が付けられます。 セルの序数を計算する式を次に示します。  
  
 セルの序数値で使用できます、[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)のプロパティ、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)を迅速に取得するオブジェクト、[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [セルのオブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [軸の例 (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Item プロパティ (ADO MD セルセット)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [序数に基づくプロパティ (ADO MD 位置)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)

