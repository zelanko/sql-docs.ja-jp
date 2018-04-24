---
title: InheritTypeEnum |Microsoft ドキュメント
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
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4be349722f849c0a5f059236b4a1d689cf18494
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="inherittypeenum"></a>InheritTypeEnum
オブジェクトがアクセス許可の設定を継承する方法を示す[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトとは、プライマリ オブジェクトに含まれるその他のコンテナーの両方のエントリを継承します。|  
|**adInheritContainers**|2|プライマリ オブジェクトに含まれるその他のコンテナーでは、エントリを継承します。|  
|**adInheritNone**|0|既定値です。 継承は行われません。|  
|**adInheritNoPropagate**|4|**AdInheritObjects**と**adInheritContainers**フラグは、継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内の非コンテナー オブジェクトでは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
