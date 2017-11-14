---
title: "DrilledDown プロパティ (ADO MD) |Microsoft ドキュメント"
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
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8dfa880e78bdeccf722723a7d05f2f0ca1938ed6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="drilleddown-property-ado-md"></a>DrilledDown プロパティ (ADO MD)
子の直後に続くかどうかを示す、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)軸にします。  
  
## <a name="return-values"></a>戻り値  
 返します、**ブール**値し、は読み取り専用です。 **DrilledDown**返します**True**軸に現在のメンバーの子メンバーがない場合。 **DrilledDown**返します**False**現在のメンバーに 1 つまたは複数の子メンバーがある場合は、軸にします。  
  
## <a name="remarks"></a>解説  
 使用して、 **DrilledDown**このメンバーの直後の軸でこのメンバーの少なくとも 1 つの子があるかどうかを判断するプロパティです。 この情報は、メンバーを表示するときに役立ちます。  
  
 このプロパティでのみサポート[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)に属しているオブジェクト、[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクト。 このプロパティが参照されたときにエラーが発生した**メンバー**に属しているオブジェクト、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [メンバー オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [ParentSameAsPrev プロパティ (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)

