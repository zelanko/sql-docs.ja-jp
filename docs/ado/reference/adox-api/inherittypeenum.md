---
title: "InheritTypeEnum |Microsoft ドキュメント"
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
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de2281f5badafc7c2140347ab96dfb7251f98ed2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="inherittypeenum"></a>InheritTypeEnum
オブジェクトがアクセス許可の設定を継承する方法を示す[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)です。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトとは、プライマリ オブジェクトに含まれるその他のコンテナーの両方のエントリを継承します。|  
|**adInheritContainers**|2|プライマリ オブジェクトに含まれるその他のコンテナーでは、エントリを継承します。|  
|**adInheritNone**|0|既定値です。 継承は行われません。|  
|**adInheritNoPropagate**|4|**AdInheritObjects**と**adInheritContainers**フラグは、継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内の非コンテナー オブジェクトでは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
