---
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
ms.openlocfilehash: f420d7d49ad24188f5210001af1209427478f3f6
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82746680"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)で設定された権限をオブジェクトが継承する方法を指定します。  
  
|定数|[値]|説明|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトと、プライマリオブジェクトに含まれるその他のコンテナーは両方ともエントリを継承します。|  
|**adInheritContainers**|2|プライマリオブジェクトに含まれる他のコンテナーは、エントリを継承します。|  
|**adInheritNone**|0|既定値。 継承は行われません。|  
|**adInheritNoPropagate**|4|**Adinheritobjects**と**adinheritobjects**フラグは、継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内のコンテナー以外のオブジェクトは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
