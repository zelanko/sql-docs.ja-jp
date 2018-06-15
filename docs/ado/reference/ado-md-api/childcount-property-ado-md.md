---
title: ChildCount プロパティ (ADO MD) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fdc3697ac683b63df1f40fbec543e113f11037e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283581"
---
# <a name="childcount-property-ado-md"></a>ChildCount プロパティ (ADO MD)
対象のメンバーの数を示す現在[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクト階層の親であります。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**整数であり、読み取り専用です。  
  
## <a name="remarks"></a>コメント  
 使用して、 **ChildCount**子供の数の推定値を取得するプロパティ、**メンバー**がします。 子の実際の**メンバー**によって返されることができます、[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティです。  
  
 **メンバー**オブジェクトから、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクト、返される最大数は 65536 です。 子の実際の数は 65536 を超えている場合、返される値は 65536 をできます。 そのため、アプリケーションが解釈する必要があります、 **ChildCount** 65536 以上 65536 です。  
  
 **メンバー**オブジェクトから、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクト、ADO のコレクションを使用して[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティを**子**を確認する、子の正確な数。 子の正確な数を決定するには、コレクション内の子の数が多い場合は低速可能性があります。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [子プロパティ (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count プロパティ (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
