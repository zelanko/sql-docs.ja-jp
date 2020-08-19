---
description: ChildCount プロパティ (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 713958259b274e779802828d1940cabf25c5c222
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441204"
---
# <a name="childcount-property-ado-md"></a>ChildCount プロパティ (ADO MD)
現在の [メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md) オブジェクトが階層内の親であるメンバーの数を示します。  
  
## <a name="return-values"></a>戻り値  
 **長**整数を返し、読み取り専用です。  
  
## <a name="remarks"></a>解説  
 **Childcount**プロパティを使用して、**メンバー**が持つ子の数の推定値を返します。 **メンバー**の実際の子は、 [children](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティで返すことができます。  
  
 [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクトの**メンバー**オブジェクトの場合、返される最大値は65536です。 実際の子の数が65536を超えた場合、返される値は依然として65536になります。 このため、アプリケーションで65536は、 **Childcount** が65536の子以上であることを解釈する必要があります。  
  
 [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトの**メンバー**オブジェクトの場合は、 **Children**コレクションの ADO collection [Count](../../../ado/reference/ado-api/count-property-ado.md)プロパティを使用して、子の正確な数を決定します。 コレクション内の子の数が多い場合、子の正確な数を判断するには時間がかかることがあります。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Children プロパティ (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)   
 [Count プロパティ (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)
