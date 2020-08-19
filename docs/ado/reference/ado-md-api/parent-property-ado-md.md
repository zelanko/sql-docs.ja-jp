---
description: Parent プロパティ (ADO MD)
title: Parent プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parent
- Member::Parent
helpviewer_keywords:
- Parent property [ADO MD]
ms.assetid: 32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c599bd75388dc0b2ea7e4a5c16f495817f917ba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440794"
---
# <a name="parent-property-ado-md"></a>Parent プロパティ (ADO MD)
階層内の現在の [メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md) の親であるメンバーを示します。  
  
## <a name="return-values"></a>戻り値  
 [メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトを返し、読み取り専用です。  
  
## <a name="remarks"></a>解説  
 階層の最上位レベル (ルート) にあるメンバーには親がありません。 このプロパティは、 [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトに属する**メンバー**オブジェクトでのみサポートされます。 このプロパティが、 [Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクトに属する**メンバー**オブジェクトから参照されている場合に、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [Children プロパティ (ADO MD)](../../../ado/reference/ado-md-api/children-property-ado-md.md)
