---
title: ChildCount プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ChildCount
- Member::ChildCount
helpviewer_keywords:
- ChildCount property [ADO MD]
ms.assetid: 5463be22-ca50-43ea-9c92-468fc8eda280
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01be10781c0925683ed2da9fdff24190d175fca6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611410"
---
# <a name="childcount-property-ado-md"></a>ChildCount プロパティ (ADO MD)
対象のメンバーの数を示す現在[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクト階層の親であります。  
  
## <a name="return-values"></a>戻り値  
 返します、**長い**整数は読み取り専用とします。  
  
## <a name="remarks"></a>コメント  
 使用して、 **ChildCount**子供の数の推定値を返すプロパティを**メンバー**が。 実際の子、**メンバー**によって返される、[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティ。  
  
 **メンバー**オブジェクトから、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクト、返される最大数は 65536 です。 子の実際の数は 65536 を超えている場合、返される値は 65536 をできます。 そのため、アプリケーションが解釈する必要があります、 **ChildCount** 65536 以上 65536 です。  
  
 **メンバー**オブジェクトから、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクト、ADO のコレクションを使用して[カウント](../../../ado/reference/ado-api/count-property-ado.md)プロパティを**子**を確認する、子の正確な数。 子の正確な数を決定するには、コレクション内の子の数が多い場合は低速可能性があります。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Children プロパティ (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count プロパティ (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
