---
title: State プロパティ (ADO MD) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1960818e3ebf5b58610e18bfb23ee7c8c3101b8e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="state-property-ado-md"></a>State プロパティ (ADO MD)
セルセットの現在の状態を示します。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**の現在の状態を示す整数値、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)オブジェクトし、は読み取り専用です。 次の値が無効です:**取得のみ**(0) と**可能**(1)。  
  
## <a name="remarks"></a>解説  
 使用する、 [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)定数名は、プロジェクトで参照されている ADO タイプ ライブラリがある必要があります。 参照してください[ADO md を使用する ADO](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)詳細についてはします。  
  
## <a name="applies-to"></a>適用対象  
 [CellSet オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Close メソッド (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Open メソッド (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
