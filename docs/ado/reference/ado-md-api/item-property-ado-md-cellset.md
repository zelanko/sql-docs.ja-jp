---
title: "Item プロパティ (ADO MD セルセット) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Item
- Cellset::Item
helpviewer_keywords:
- Item property [ADO MD]
ms.assetid: 0e93d79b-b12e-4e98-889e-c2dfcca20fd0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3fa95d6c1441fe81db90d868e08717ff39d37fe
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="item-property-ado-md-cellset"></a>Item プロパティ (ADO MD セルセット)
セルを取得、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)の座標を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set  
Cell = Cellset.Item ( Positions)  
```  
  
## <a name="parameters"></a>パラメーター  
 *位置*  
 A **VariantArray**のセルを一意に指定する値。 *位置*次のいずれかになります。  
  
-   位置の番号の配列  
  
-   メンバー名の配列  
  
-   序数の位置  
  
## <a name="remarks"></a>解説  
 使用して、**項目**返されるプロパティを[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)オブジェクト内の[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクト。 場合、**項目**に対応するセル プロパティを見つけられない、*位置*引数、エラーが発生します。  
  
 **項目**プロパティは既定のプロパティを**セルセット**オブジェクト。 次の構文は同義です。  
  
```  
  
Cellset.Item ( Positions )Cellset ( Positions )  
```  
  
## <a name="remarks"></a>解説  
 *位置*引数が返されるセルを指定します。 セルの序数位置または各軸に沿った位置によって指定できます。 各軸に沿った位置を指定してセルを指定する場合は、位置の数値の値または各位置のメンバーの名前を指定できます。  
  
 内の 1 つのセルを一意に識別する数値は、序数位置は、**セルセット**です。 内のセルが概念的には、番号付けは、**セルセット**かのよう、**セルセット**された、 *p*-次元の配列場所*p*軸の数です。 セルは、行優先順で指定されます。 以下には、セルの序数を計算する式を示します。  
  
 として文字列をメンバー名が渡された場合**項目**軸の数値識別子の増加順に、メンバーを一覧表示する必要があります。 軸には、ディメンションの入れ子の増加順にメンバーを表示: つまり、最も外側のディメンションのメンバーにするには、内部のディメンションのメンバーが従います。 別の文字列によって表される各ディメンションおよびメンバーの文字列のリストをコンマで区切る必要があります。  
  
> [!NOTE]
>  データ プロバイダーによってメンバー名のセルの取得をサポートされていない可能性があります。 詳細については、プロバイダーのマニュアルを参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [セルのオブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)
