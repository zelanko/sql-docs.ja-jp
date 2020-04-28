---
title: Ordinal プロパティ (ADO MD Cell) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cell::Ordinal
- Ordinal
helpviewer_keywords:
- Ordinal property [ADO MD]
ms.assetid: a6001168-b954-47f0-ba0d-c05c4cc40c58
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 194b72ce66eb2efdc3a246f24948b01c790f7b8e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949376"
---
# <a name="ordinal-property-ado-md-cell"></a>Ordinal プロパティ (ADO MD セル)
セルセット内の位置によって[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)を一意に識別します。  
  
## <a name="return-values"></a>戻り値  
 **長**整数を返し、読み取り専用です。  
  
## <a name="remarks"></a>Remarks  
 セルの序数値は、セルセット内のセルを一意に識別します。 概念的には、セルセット内のセルには、セルセットが*p*次元配列であるかのように番号が付けられます。ここで、 *p*は[軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)の数です。 セルは、行優先順で0から始まる番号が付けられます。 セルの序数を計算するための式を次に示します。  
  
 セルの序数値を[Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトの[Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティと共に使用して、[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)をすばやく取得できます。  
  
## <a name="applies-to"></a>適用対象  
 [Cell オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Axis の例 (VBScript)](../../../ado/reference/ado-md-api/axis-example-vbscript.md)   
 [Cellset オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)   
 [Item プロパティ (ADO MD セルセット)](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)   
 [Ordinal プロパティ (ADO MD 位置)](../../../ado/reference/ado-md-api/ordinal-property-ado-md-position.md)
