---
description: InheritTypeEnum
title: InheritTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: rothja
ms.author: jroth
ms.openlocfilehash: dfa4d6c15cc7d26dbfe964947bd09a04e2f75128
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439854"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)で設定された権限をオブジェクトが継承する方法を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトと、プライマリオブジェクトに含まれるその他のコンテナーは両方ともエントリを継承します。|  
|**adInheritContainers**|2|プライマリオブジェクトに含まれる他のコンテナーは、エントリを継承します。|  
|**adInheritNone**|0|既定値。 継承は行われません。|  
|**adInheritNoPropagate**|4|**Adinheritobjects**と**adinheritobjects**フラグは、継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内のコンテナー以外のオブジェクトは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
